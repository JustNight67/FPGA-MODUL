---
weight: 39
title: "Praktek ALU"
description: "Program Adder, Subtractor, Multiplier Comparator"
icon: "Code"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

## Project

1. Membuka aplikasi Vivado 2020.2

2. Membuat Project baru

3. Buat project dengan nama BAB7_nama

    <center>
    <img src="/images/babSeven/Ba7-7.png" class="img-fluid mb-3 responsive-img">
    </center>

4. Kemudian pada bagian source pilih tanda + untuk membuat source baru.

    <center>
    <img src="/images/babSeven/Ba7-8.png" class="img-fluid mb-3 responsive-img">
    </center>

5. Lalu, akan muncul tampilan window baru, pilih add or create design source

    <center>
    <img src="/images/babSeven/Ba7-9.png" class="img-fluid mb-3 responsive-img">
    </center>

6. Buatlah 8 source baru dan beri nama masing-masing source halfadder, fulladder, adder_3bit, fullsubtractor, subtractor_3bit, multiplier_3bit, comparator_3bit dan ALU.

<center>
<img src="/images/babSeven/Ba7-10.png" class="img-fluid mb-3 responsive-img">
</center>

Setelah semua source telah dibuat klik next, lalu akan muncul tampilan define modules pilih OK.

<center>
<img src="/images/babSeven/Ba7-11.png" class="img-fluid mb-3 responsive-img">
</center>

Pada bagian source, klik 2 kali pada source **halfadder.vhd** kemudian masukkan kode berikut.

## Program Adder

Berikut adalah program VHDL untuk aritmatika HalfAdder, FullAdder, dan 3-Bit Adder

### Half Adder

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-12.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Half Adder" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity halfadder is
    Port ( a : in STD_LOGIC;
        b : in STD_LOGIC;
        s : out STD_LOGIC;
        cout : out STD_LOGIC);
end halfadder;

architecture Behavioral of halfadder is

begin
s <= a xor b;
cout <= a and b;

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

### Full Adder

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-13.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Full Adder" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity fulladder is
    Port ( a : in STD_LOGIC;
        b : in STD_LOGIC;
        cin : in std_logic;
        s : out STD_LOGIC;
        cout : out STD_LOGIC);
end fulladder;

architecture Behavioral of fulladder is
component halfadder
port (a,b : in std_logic;
    s : out std_logic;
    cout : out std_logic);
end component;
signal s1,c1,c2:std_logic;
begin
ha1 : halfadder port map(a,b,s1,c1);
ha2 : halfadder port map(s1,cin,s,c2);
cout <= c1 or c2;

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

### Adder 3 Bit

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-14.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code 3-Bit Adder" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity adder_3bit is
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        cin : in STD_LOGIC;
        sum : out std_logic_vector (2 downto 0);
        cout : out STD_LOGIC);
end adder_3bit;

architecture Behavioral of adder_3bit is
component fulladder
port ( a : in std_logic;
    b : in std_logic;
    cin : in std_logic;
    s : out std_logic;
    cout : out std_logic);
end component;
signal c1,c2:std_logic;
begin
fa1:fulladder port map(a(0),b(0),cin,sum(0),c1);
fa2:fulladder port map(a(1),b(1),c1,sum(1),c2);
fa3:fulladder port map(a(2),b(2),c2,sum(2),cout);

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<span></span>

## Program Subtractor

Berikut adalah program VHDL untuk aritmatika Full Subtractor dan 3-Bit Subtractor

### Full Subtractor

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-16.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Full Subtractor" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity fullsubtractor is
    Port ( a : in STD_LOGIC;
        b : in STD_LOGIC;
        bin : in STD_LOGIC;
        diff : out STD_LOGIC;
        bout : out STD_LOGIC);
end fullsubtractor;

architecture Behavioral of fullsubtractor is

begin
diff <= a xor b xor bin;
bout <= ((not a) and b) or ((not a) and bin) or (b and bin);

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

### Subtractor 3 Bit

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-17.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Subtractor 3 Bit" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity subtractor_3bit is
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        bin : in STD_LOGIC;
        diff : out std_logic_vector (2 downto 0);
        bout : out STD_LOGIC);
end subtractor_3bit;

architecture Behavioral of subtractor_3bit is
component fullsubtractor is
port ( a : in std_logic;
    b : in std_logic;
    bin : in std_logic;
    diff : out std_logic;
    bout : out std_logic);
end component;
signal br0,br1: std_logic;
begin
fs1 : fullsubtractor port map (a(0),b(0),bin,diff(0),br0);
fs2 : fullsubtractor port map (a(1),b(1),br0,diff(1),br1);
fs3 : fullsubtractor port map (a(2),b(2),br1,diff(2),bout);
end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

## Program Multiplier 3 Bit

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-18.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-19.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Multiplier 3 Bit" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity multiplier_3bit is
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        p : out std_logic_vector (5 downto 0));
end multiplier_3bit;

architecture Behavioral of multiplier_3bit is
component fulladder is
    Port ( a : in STD_LOGIC;
        b : in STD_LOGIC;
        cin : in std_logic;
        s : out STD_LOGIC;
        cout : out STD_LOGIC);
end component;
component halfadder is
    Port ( a : in STD_LOGIC;
        b : in STD_LOGIC;
        s : out STD_LOGIC;
        cout : out STD_LOGIC);
end component;

signal f0,f1,f2,f3,f4,f5,f6,f7,f8,f9,f10,f11,f12,s1,s2: std_logic;
begin
ha1: halfadder port map (f0,f1,p(1),f2);
fa1: fulladder port map (f2,f3,f4,s1,f5);
ha2: halfadder port map (f5,f6,s2,f7);
ha3: halfadder port map (s1,f8,p(2),f9);
fa2: fulladder port map (f9,s2,f10,p(3),f11);
fa3: fulladder port map (f11,f7,f12,p(4),p(5));
f0 <= a(0) and b(1);
f1 <= a(1) and b(0);
f3 <= a(0) and b(2);
f4 <= a(1) and b(1);
f6 <= a(1) and b(2);
f8 <= a(2) and b(0);
f10<= a(2) and b(1);
f12<= a(2) and b(2);
p(0)<= a(0) and b(0);

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<span></span>

## Program Comparator 3 Bit

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-20.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Multiplier 3 Bit" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity comparator_3bit is
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        less : out STD_LOGIC;
        equal : out STD_LOGIC;
        greater : out STD_LOGIC);
end comparator_3bit;

architecture Behavioral of comparator_3bit is
begin
    process (a,b)
    begin
        if (a > b) then
            less <= '0';
            equal <= '0';
            greater <= '1';
        elsif (a < b) then
            less <= '1';
            equal <= '0';
            greater <= '0';
        else 
            less <= '0';
            equal <= '1';
            greater <= '0';
        end if;
    end process;
end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<span></span>

## Program ALU

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-21.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-22.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-23.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Multiplier 3 Bit" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity alu is
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        c : in STD_LOGIC;
        sel : in std_logic_vector (1 downto 0);
        result : out std_logic_vector (5 downto 0));
end alu;

architecture Behavioral of alu is
component comparator_3bit
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        less : out STD_LOGIC;
        equal : out STD_LOGIC;
        greater : out STD_LOGIC);
end component;
component multiplier_3bit
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        p : out std_logic_vector (5 downto 0));
end component;
component subtractor_3bit
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        bin : in STD_LOGIC;
        diff : out std_logic_vector (2 downto 0);
        bout : out STD_LOGIC);
end component;
component adder_3bit
    Port ( a : in std_logic_vector (2 downto 0);
        b : in std_logic_vector (2 downto 0);
        cin : in STD_LOGIC;
        sum : out std_logic_vector (2 downto 0);
        cout : out STD_LOGIC);
end component;
signal t_comp, t_multi, t_sub, t_adder : std_logic_vector (5 downto 0) := (others => '0');
begin
alu1 : adder_3bit port map (a=>a,b=>b,cin=>c,sum=>t_adder(2 downto 0),cout=>t_adder(3));
alu2 : subtractor_3bit port map (a=>a,b=>b,bin=>c,diff=>t_sub(2 downto 0),bout=>t_sub(3));
alu3 : multiplier_3bit port map(a=>a,b=>b,p=>t_multi);
alu4 : comparator_3bit port map(a=>a,b=>b,less=>t_comp(0),equal=>t_comp(1),greater=>t_comp(2));

process (sel,t_comp,t_multi,t_sub, t_adder)
begin
case sel is
when "00"=>
    result<=t_adder; when "01"=>
    result<=t_sub; when "10"=>
    result<=t_multi; when "11"=>
    result<=t_comp; when others=>
    result<="000000";
end case;
end process;
end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<span></span>

Setelah semua kode untuk masing-masing source berhasil ditulis dan tidak terdapat error, pastikan semua source telah di save.

1. Kemudian pastikan source ALU adalah top module. jika bukan source ALU yang menjadi top module, klik kanan **ALU.vhd** pada bagian source kemudian pilih **set as top**.

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-24.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

2. Selanjutnya pada bagian RTL analysis, pilih schematic untuk menampilkan rangkaian ALU yang telah dibuat.

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-25.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

    <span></span>

    Gambar diatas adalah tampilan ALU yang telah berhasil dibuat menggunakan kode vhdl dan dijadikan schematic pada aplikasi Vivado.

3. Kemudian pada pojok kanan atas pilih **I/O Planning** dan pilih **I/O ports** untuk memasukkan port yang akan digunakan untuk mengimplementasikan ALU pada board FPGA.

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-26.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

    <span></span>

    Berikut adalah port yang digunakan pada I/O ports

4. Tekan *Ctrl + S* untuk menyimpan konfigurasi yang telah dibuat, kemudian akan muncul tampilan save constraints. Beri nama ALU lalu pilih OK.

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-27.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

    <span></span>

    Lalu pada bagian baru akan muncul file constraint yang telah dibuat, klik 2 kali untuk menampilkan isi dari file ALU.xdc yang berisi konfigurasi port yang telah dibuat.

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-28.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-29.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-30.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

5. Selanjutnya, hubungkan board nexys dengan komputer menggunakan micro usb dan pada bagian Program and Debug pilih generate bitstream untuk membuat file .bit yang akan diupload pada board.

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-31.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

6. Setelah proses generate bitstream selesai, klik open target dan pilih auto connect

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-32.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

7. Setelah board berhasil terhubung dengan komputer, **klik program dan pilih xc7a100t_0**

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-33.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

8.	Ketika program berhasil diupload pada board maka pada bagian hardware akan terllihat status Programmed.

    <center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSeven/Ba7-34.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>
