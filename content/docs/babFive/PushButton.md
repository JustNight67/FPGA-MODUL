---
weight: 29
title: "Push Button"
description: "Memahami Komponen apa saja yang digunakan pada Seven Segment"
icon: "Radio_Button_Checked"
date: "2025-10-13T12:31:10+07:00"
lastmod: "2025-10-20T18:05:10+07:00"
toc: true
---

Push Button adalah saklar yang beroperasi dengan cara ditekan dan bisa melakukan dua fungsi berbeda, yaitu menutup sirkuit bila ditekan atau justru membuka sirkuit bila ditekan. Jika tekanan dilepaskan atau terjadi tekanan berikutnya maka akan menormalkan kembali tombol ke posisi semula. Secara umum, komponen ini memiliki cara kerja yang sama dengan switch, namun hanya berbeda pada cara pengoperasiannya saja.

Komponen ini juga berfungsi sebagai pemberi sinyal pada rangkaian listrik ketika bagian knopnya ditekan, dan alat ini akan bekerja sehingga kontak- kontaknya akan terhubung untuk jenis Normally Open (NO) dan akan terlepas untuk jenis Normally Close (NC). Pada board FPGA Nexys 4 dan A7 terdapat total 7 push button, namun yang dapat digunakan hanya 5. Karena dua push button yang berwarna merah sudah memiliki fungsi sendiri yaitu untuk CPU reset.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-18.png" alt="Gambar 5.10 - Push Button pada Nexys A7" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.10</b> Push Button pada Nexys A7</p>

## TUGAS

### Program UpDown Counter menggunakan Push Button

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-19.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-20.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-21.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Push Button" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;

entity sevseg3 is
    Port ( clk : in STD_LOGIC;
           count_up : in STD_LOGIC;
           count_down : in STD_LOGIC;
           seg : out std_logic_vector(6 downto 0));
end sevseg3;

architecture Behavioral of sevseg3 is
signal temp_count : std_logic_vector(3 downto 0) :="0000";
signal up_edge : std_logic_vector(1 downto 0);
signal down_edge : std_logic_vector(1 downto 0);

begin

process(clk, temp_count)
begin
if rising_edge(clk) then
    up_edge <= up_edge(0) & count_up;
    down_edge <= down_edge(0) & count_down;
    if (up_edge = "01") then
        if temp_count <9 then
            temp_count <= temp_count + 1;
        else
            temp_count <= "0000";
        end if;
else
    if (down_edge = "10") then
        if temp_count >0 then
           temp_count <= temp_count - 1;
        else
           temp_count <= "1001";
        end if;
    end if;
  end if;
end if;
end process;

process (temp_count)
begin
    case temp_count is
        when "0000" => seg <= "1000000";
        when "0001" => seg <= "1111001";
        when "0010" => seg <= "0100100";
        when "0011" => seg <= "0110000";
        when "0100" => seg <= "0011001";
        when "0101" => seg <= "0010010";
        when "0110" => seg <= "0000010";
        when "0111" => seg <= "1111000";
        when "1000" => seg <= "0000000";
        when "1001" => seg <= "0010000";
        when others => seg <= "1111111";
   end case;
end process;

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<h5>Port yang digunakan pada I/O Planning</h5>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-22.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>
