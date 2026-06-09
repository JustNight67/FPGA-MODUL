---
weight: 25
title: "Sensor dan Pin Pmod"
description: "Memahami definisi dan jenis Sensor serta Struktur dasar pin pada konektor Pmod Nexys Board"
icon: "Pin"
date: "2025-10-13T12:24:40+07:00"
lastmod: "2025-10-13T12:24:40+07:00"
toc: true
---

## Sensor

Nexys A7 menyediakan Pmod (Peripheral Module) sebagai antarmuka standar untuk menghubungkan modul eksternal, termasuk sensor. PMOD adalah konektor dengan format 2×6 pin (12 pin) yang memudahkan ekspansi board FPGA dengan berbagai perangkat tambahan Struktur dasar pin pada konektor Pmod adalah:

<ul><li><b>4 pin I/O</b> (GPIO) yang dapat diprogram melalui FPGA.</li></ul>
<ul><li><b>2 pin GND</b> sebagai ground referensi.</ul></li>
<ul><li><b>2 pin VCC</b> (biasanya 3,3 V) sebagai catu daya untuk modul eksternal.</li></ul>
<ul><li>Sisanya digunakan sebagai pin tambahan untuk I/O atau sinyal kontrol.</li></ul>

<div class="d-flex justify-content-center w-60">
<img src="/images/babFour/Ba4-7.png" alt="Gambar 4.7 - Pin Pmod Nexys A7" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 4.7</b> Pin Pmod Nexys A7</p>

Nexys A7 memiliki beberapa port Pmod (JA, JB, JC, JD, JE, JXADC). Masing-masing port bisa digunakan untuk menghubungkan sensor dengan protokol yang sesuai. Misalnya:

<ul><li><b>JXADC</b> → khusus untuk input analog menggunakan pin XADC </li></ul>
<ul><li><b>JA - JD</b> → digunakan untuk komunikasi digital (SPI, I²C, UART, atau GPIO biasa). </li></ul>

<div class="d-flex justify-content-center w-60">
<img src="/images/babFour/Ba4-8.png" alt="Gambar 4.8 - Pinout Pmod JA, JB, JC, JD dan XADC" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 4.8</b> Pinout Pmod JA, JB, JC, JD dan XADC</p>

## Praktek

### Menampilkan Hello, World! pada PuTTY menggunakan Nexys A7

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFour/Bafo-9.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFour/Bafo-10.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFour/Bafo-11.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Hello World!" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.NUMERIC_STD.ALL;

entity UART_HelloWorld is
    Port (
        clk   : in  std_logic;  -- System clock (100 MHz)
        tx    : out std_logic;  -- UART Transmit
        start : in  std_logic   -- Start signal
    );
end UART_HelloWorld;

architecture Behavioral of UART_HelloWorld is

    constant clk_freq  : integer := 100_000_000; -- 100 MHz
    constant baud_rate : integer := 9600;
    constant baud_div  : integer := clk_freq / baud_rate;

    type state_type is (IDLE, SEND);
    signal state        : state_type := IDLE;

    signal tx_data      : std_logic_vector(7 downto 0);
    signal tx_busy      : std_logic := '0';
    signal bit_cnt      : integer range 0 to 9 := 0;
    signal shift_reg    : std_logic_vector(9 downto 0);
    signal baud_counter : integer range 0 to baud_div := 0;

    -- "dandi fpga\r\n"
type string_array is array (0 to 12) of std_logic_vector(7 downto 0);
signal message : string_array := (
    X"48", -- H
    X"45", -- E
    X"4C", -- L
    X"4C", -- L
    X"4F", -- O
    X"20", -- (spasi)
    X"57", -- W
    X"4F", -- O
    X"52", -- R
    X"4C", -- L
    X"44", -- D
    X"0D", -- \r (Carriage return)
    X"0A"  -- \n (Line feed)
);

    signal char_index : integer range 0 to 12 := 0;

begin

    process (clk)
    begin
        if rising_edge(clk) then
            case state is
                when IDLE =>
                    tx <= '1';  -- idle line
                    if start = '1' then
                        char_index <= 0;
                        state <= SEND;
                    end if;

                when SEND =>
                    if tx_busy = '0' then
                        tx_data   <= message(char_index);
                        -- UART frame: start(0) + data(8bit LSB first) + stop(1)
                        shift_reg <= '1' & tx_data & '0';
                        bit_cnt   <= 0;
                        tx_busy   <= '1';
                    end if;

                    if tx_busy = '1' then
                        if baud_counter = baud_div then
                            baud_counter <= 0;
                            tx <= shift_reg(0); -- kirim LSB
                            shift_reg <= '1' & shift_reg(9 downto 1);
                            bit_cnt <= bit_cnt + 1;
                            if bit_cnt = 9 then
                                tx_busy <= '0';
                                if char_index = 12 then
                                    state <= IDLE;  -- selesai
                                else
                                    char_index <= char_index + 1;
                                end if;
                            end if;
                        else
                            baud_counter <= baud_counter + 1;
                        end if;
                    end if;
            end case;
        end if;
    end process;

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<span class=""> </span>

<h3>Pinout Nexys A7</h3>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFour/Ba4-12.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

## Menggunakan Sensor Untuk Menampilkan Hasilnya pada PuTTY

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFour/Bafo-13.jpg" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFour/Bafo-14.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFour/Bafo-15.jpg" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Sensor" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.STD_LOGIC_ARITH.ALL;
use IEEE.STD_LOGIC_UNSIGNED.ALL;

entity LDR_UART is
  Port (
        clk       : in std_logic;
        reset     : in std_logic;
        ldr_input : in std_logic;
        tx        : out std_logic 
        );
end LDR_UART;

architecture Behavioral of LDR_UART is
    constant clk_freq     : integer := 100_000_000; -- frekuensi 100 Mhz
    constant baud_rate    : integer := 9600; -- UART baud rate
    constant baud_div     : integer := clk_freq / baud_rate;
    constant delay_cycles : integer := clk_freq * 5; -- 5 detik
    
    type state_type is (IDLE, DELAY, SEND);
    signal state : state_type := IDLE;
    
    signal tx_data : std_logic_vector(7 downto 0);
    signal tx_busy : std_logic := '0';
    signal bit_cnt : integer range 0 to 9 := 0;
    signal shift_reg : std_logic_vector(9 downto 0);
    signal baud_counter : integer range 0 to delay_cycles := 0;
    signal delay_counter : integer range 0 to delay_cycles := 0;
    
    type string_array is array (0 to 7) of std_logic_vector(7 downto 0);
    
    signal message_terang : string_array := (
        X"54", X"65", X"72", X"61", X"6E", X"67", X"0D", X"0A" -- Terang\r\n
    );
    
    signal message_gelap : string_array := (
        X"47", X"65", X"6C", X"61", X"70", X"0D", X"0A", X"0A" -- Gelap\r\n
    );
    
        signal char_index : integer range 0 to 7 := 0;
        signal current_message : string_array;

begin
    process(clk, reset)
    begin
        if reset = '1' then
            state <= IDLE;
            tx_busy <= '0';
            char_index <= 0;
            tx <= '1';
            delay_counter <= 0;
        elsif rising_edge(clk) then
            case state is
                when IDLE =>
                    tx <= '1'; -- idle state of uart tx line
                    if ldr_input = '1' then
                        current_message <= message_gelap;
                    else
                        current_message <= message_terang;
                    end if;
                    char_index <= 0;
                    state <= SEND;
                when SEND =>
                    if tx_busy = '0' then
                        tx_data <= current_message(char_index);
                        shift_reg <= '1' & tx_data & '0'; -- start bit, data, stop bit
                        bit_cnt <= 0;
                        tx_busy <= '1';
                    end if;
                    
                    if tx_busy = '1' then
                        if baud_counter = baud_div then
                        baud_counter <= 0;
                        tx <= shift_reg(0);
                        shift_reg <= '1' & shift_reg(9 downto 1);
                        bit_cnt <= bit_cnt + 1;
                        if bit_cnt = 9 then
                            tx_busy <= '0';
                            if char_index = 7 then
                                state <= DELAY; --Delay before next reading
                                delay_counter <= 0;
                            else
                                char_index <= char_index + 1;
                            end if;
                        end if;
                     else
                        baud_counter <= baud_counter + 1;
                     end if;
                 end if;
                 
             when DELAY =>
                if delay_counter < delay_cycles then
                    delay_counter <= delay_counter + 1;
                else
                    state <= IDLE; -- Restart cycle after delay
                end if;
           end case;
      end if;
   end process;
end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<span class=""> </span>

<h3>Pinout Nexys A7</h3>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFour/Ba4-16.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>
