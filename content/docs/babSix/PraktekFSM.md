---
weight: 35
title: "Praktek Finite State Machine"
description: "Melakukan praktik FSM Seven Segment dan Traffic Light"
icon: "Assignment"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

## Finite State Machine pada Seven Segment untuk menampilkan urutan angka secara bergantian

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSix/Ba6-6.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSix/Ba6-7.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSix/Ba6-8.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code FSM Seven Segment" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.numeric_std.ALL;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx leaf cells in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity sevseg_fsm is
    Port ( clk : in STD_LOGIC;
           reset : in STD_LOGIC;
           an : out std_logic_vector(7 downto 0);
           seg : out std_logic_vector(6 downto 0));
end sevseg_fsm;

architecture Behavioral of sevseg_fsm is
    signal state    : integer range 0 to 7 := 0;
    signal clkdiv   : unsigned(23 downto 0) := (others => '0');
    signal tick     : std_logic := '0';
    signal digitval : integer range 0 to 9 := 0;

begin

    process (clk, reset)
    begin
        if reset = '1' then
            clkdiv <= (others => '0');
            tick   <= '0';
        elsif rising_edge(clk) then
            clkdiv <= clkdiv + 1;
            if clkdiv = 0 then
                tick <= '1';
            else
                tick <= '0';
            end if;
        end if;
     end process;
     
        -- FSM : pindah ke digit berikutnya
     process(clk, reset)
     begin
        if reset = '1' then
            state <= 0;
        elsif rising_edge(clk) then
            if tick = '1' then
                if state = 7 then
                    state <= 0;
                else
                    state <= state + 1;
                end if;
            end if;
        end if;
     end process;
     
     process(state)
     begin
        an <= (others => '1');
        an(state) <= '0';
     end process;
     
     process(state)
     begin
        case state is
            when 0 => digitval <= 1;
            when 1 => digitval <= 2;
            when 2 => digitval <= 3;
            when 3 => digitval <= 4;
            when 4 => digitval <= 5;
            when 5 => digitval <= 6;
            when 6 => digitval <= 7;
            when 7 => digitval <= 8;
            when others => digitval <= 0;
        end case;
     end process;
     
     process(digitval)
     begin
        case digitval is         --gfedcba
            when      0 => seg <= "1000000"; --0
            when      1 => seg <= "1111001"; --1
            when      2 => seg <= "0100100"; --2
            when      3 => seg <= "0110000"; --3
            when      4 => seg <= "0011001"; --4
            when      5 => seg <= "0010010"; --5
            when      6 => seg <= "0000010"; --6
            when      7 => seg <= "1111000"; --7
            when      8 => seg <= "0000000"; --8
            when      9 => seg <= "0010000"; --9
            when others => seg <= "1111111"; -- blank
        end case;
     end process;

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<h5>Pinout Nexys A7</h5>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSix/Ba6-9.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

## Finite State Machine menggunakan Modul Traffic Light

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSix/Ba6-10.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSix/Ba6-11.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code FSM Traffic Light" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.all;
use IEEE.std_logic_unsigned.all;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx leaf cells in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity TrafficLightFSM is
    Port ( clk : in STD_LOGIC;
           reset : in STD_LOGIC;
           green : out STD_LOGIC;
           yellow : out STD_LOGIC;
           red : out STD_LOGIC);
end TrafficLightFSM;

architecture Behavioral of TrafficLightFSM is
    type state_type is (S_YELLOW, S_RED, S_GREEN);
    signal state, next_state : state_type;
    signal counter : integer range 0 to 100000000 := 0;

begin
    process (clk, reset)
    begin 
        if reset = '1' then
            state <= S_YELLOW;
            counter <= 0;
        elsif rising_edge(clk) then
            if counter = 50000000 then
                state <= next_state;
                counter <= 0;
            else
                counter <= counter + 1;
            end if;
        end if;
     end process;
     
     
     process (state, counter)
     begin
        case state is
            when S_YELLOW => 
            red <= '0';
            green <= '0';
            yellow <= '1';
            if counter = 50000000 then -- 5 detik
                next_state <= S_RED;
            else
                next_state <= S_YELLOW;
            end if;
            
            when S_RED => 
            red <= '1';
            green <= '0';
            yellow <= '0';
            if counter = 50000000 then -- 5 detik
                next_state <= S_GREEN;
            else
                next_state <= S_RED;
            end if;
            
            when S_GREEN => 
            red <= '0';
            green <= '1';
            yellow <= '0';
            if counter = 50000000 then -- 5 detik
                next_state <= S_YELLOW;
            else
                next_state <= S_GREEN;
            end if;
       end case;
    end process;          
end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<h5>Pinout Nexys A7</h5>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSix/Ba6-12.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>
