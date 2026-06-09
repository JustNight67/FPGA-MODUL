---
weight: 28
title: "Komponen Seven Segment"
description: "Memahami Komponen apa saja yang digunakan pada Seven Segment serta memprogram untuk menampilkan angka dan binary to BCD Seven Segment"
icon: "Lightbulb"
date: "2025-10-13T12:31:10+07:00"
lastmod: "2025-10-20T18:05:10+07:00"
toc: true
---

Dalam konteks Seven Segment yang dikendalikan oleh FPGA, terdapat komponen-komponen Seven Segment yang memainkan peran penting dalam mengatur tampilan angka dan waktu.

## Clock

Clock merupakan sinyal listrik yang berupa suatu denyutan dan berfungsi untuk mengkoordinasikan atau mensikronkan setiap aksi-aksi atau proses- proses yang dilakukan oleh setiap komponen di dalam perangkat elektronika. Bagaimana proses A, bagaimana proses B, bagaimana proses C, dan seterusnya. Oleh karena itu, nilai clock sangat penting agar perangkat elektronika dapat berfungsi sebagaimana mestinya. Ada beberapa istilah penting yang berkaitan dengan clock, yaitu :

<ul><li><b>Cycle</b>, yaitu satuan yang digunakan untuk menandakan selesainya satu siklus clock mulai dari denyutan dikeluarkan kemudian naik hingga nilainya mencapai 1 lalu mulai turun hingga nilainya 0.</li></ul>
<ul><li><b>Cycle Time</b>(T), adalah jumlah waktu yang diperlukan oleh sinyal clock untuk menyelesaikan satu siklus clock.
</li></ul>
<ul><li><b>Raise Time</b>, adalah waktu yang dibutuhkan untuk perubahan nilai clock dari 0 ke 1.</li></ul>
<ul><li><b>Fall Time</b>, adalah waktu yang dibutuhkan untuk perubahan nilai clock dari 1 ke 0.</li></ul>
<ul><li><b>Clock Frequency</b>(F), yaitu besaran untuk menilai kemampuan suatu sinyal clock dalam menciptakan satu siklus denyutan setiap detiknya atau dapat disebut dengan beberapa banyak cycle yang dapat dihasilkan oleh sinyal clock dalam satuan detik. Sesuai standar internasional, satuan yang digunakan untuk mengukurnya adalah Hertz = Hz, dimana Hz sama dengan satu cycle per detik.</li></ul>

Sebagai contoh, jika sinyal clock membutuhkan waktu 10ms dalam menyelesaikan satu siklus denyutan (cycle), maka clock frequency nya = 1 / 0,01 = 100 Hz = 0,1 KHz.

<center><h5><b>F = 1/T atau T = 1/F</b></h5></center>

<span></span>

## Timer dan Counter

*Timer* dan *Counter* merupakan fitur yang telah tertanam pada mikrokontroler yang memiliki fungsi terhadap waktu. Fungsi pewaktu yang dimaksud disini adalah penentuan kapan program tersebut dijalankan. Selain itu, fungsi Timer yang lainnya dapat ditemukan pada PWM, ADC dan oscillator. Prinsip kerja Timer dengan cara membagi frekuensi (prescaler) pada clock yang terdapat pada FPGA sehingga Timer dapat berjalan sesuai dengan frekuensi yang dikehendaki.

*Timer* merupakan fungsi waktu yang sumber clock-nya berasal dari clock internal. Sedangkan, Counter merupakan fungsi perhitungan yang berasal dari clock internal tersebut maupun eksternal. Salah satu contoh penggunaan Timer yaitu pada jam digital yang sumber clock-nya bisa menggunakan crystal oscillator. Sedangkan, contoh penggunaan counter pada penghitung barang konveyor yang sumber clock-nya berasal dari sensor yang mendeteksi barang tersebut.

Berikut ini merupakan contoh penggunaan *Timer*.

<ul><li>Melaksanakan tugas secara berulang.</li></ul>
<ul><li>Mengendalikan kecepatan motor DC (PWM).</li></ul>
<ul><li>Mengendalikan perhitungan (counter).</li></ul>
<ul><li>Membuat penundaan waktu (delay).</li></ul>

<span></span>

## Prescaler

Pada dasarnya Timer hanya menghitung denyutan clock. Frekuensi denyutan clock yang dihitung tersebut bisa sama dengan frekuensi crystal yang digunakan atau dapat diperlambat menggunakan prescaler dengan factor 8, 64, 256, 1024. **Contoh**:

Suatu mikrokontroler menggunakan crystal dengan frekuensi 8MHz dan timer yang digunakan adalah 16 bit. Maka, maksimum waktu timer yang dapat dihasilkan adalah :

**Diketahui :**

<ul><li>Fclk (frequency clock)          = 8MHz</li></ul>
<ul><li>FFFh (timer yang digunakan)     = 8MHz</li></ul>
<ul><li>Prescaler                       = 8MHz</li></ul>

Jawab :

TMax = 1/Fclk * FFFH
= 1/8 * 2^16
= 0.125 µs * 65536
= 0.008192 second

<span></span>

Untuk menghasilkan timer yang lebih lama, kita dapat menggunakan prescaler. Misalnya kita menggunakan 1024, maka waktu timer yang dapat dihasilkan adalah

TMax = 1/Fclk * FFFH * N
= 0.125 µs x 65536 x 1024
= 8.388735 second

## Pulse Width Modulation (PWM)

PWM (Pulse Width Modulation) secara umum adalah sebuah cara untuk memanipulasi lebar sinyal yang dinyatakan dengan pulsa dalam satu periode untuk mendapatkan tegangan rata-rata yang berbeda. Penggunaan PWM ini menggantikan output analog karena keterbatasan pada sebuah IC umumnya hanya dapat mengeluarkan sinyal digital. Beberapa contoh aplikasi PWM adalah pada kipas angin, AC, dll.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-8.png" alt="Gambar 5.6 - Grafik PWM" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.6</b> Grafik PWM</p>

Sinyal PWM umumnya memiliki amplitudo dan frekuensi dasar yang tetap, namun memiliki lebar pulsa yang bervariasi. Lebar pulsa PWM berbanding lurus dengan amplitudo sinyal asli yang belum termodulasi. Artinya, sinyal PWM memiliki frekuensi gelombang yang tetap namun duty cycle yang bervariasi antara 0-100%.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-9.png" alt="Gambar 5.7 - Perhitungan Vout PWM" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.7</b> Perhitungan Vout PWM</p>

Dari persamaan diatas, diketahui bahwa perubahan duty cycle akan merubah tegangan output atau tegangan rata-rata seperti gambar dibawah ini.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-10.png" alt="Gambar 5.8 - Hasil Vout Berdasarkan Panjang Pulsa" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.8</b> Hasil Vout Berdasarkan Panjang Pulsa</p>

Perubahan duty cycle akan merubah tegangan output atau tegangan rata-rata, untuk mengatur nilai duty cycle pada timer 8 bit, nilai pada parameter berkisar antara 0 hingga 255. Bila kita hendak mengatur duty cycle ke 0%, maka kita dapat mengatur nilai parameter ke 0 dan untuk duty cycle nya 100%. Dari sini kita akan mendapatkan set nilai dengan parameter ke 255. Sementara itu, jika kita ingin mengatur duty cycle ke 50%, maka nilai yang harus kita atur adalah 127 (50% x 255). Nilai-nilai inilah yang nantinya akan kita gunakan untuk mengatur panjang lebar pulsa tersebut.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-11.png" alt="Gambar 5.9 - Grafik Duty Cycle PWM" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.9</b> Grafik Duty Cycle PWM</p>

## TUGAS

### Kode Program Menampilkan Angka pada Seven Segment

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-12.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-13.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Seven Segment" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx leaf cells in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity sevseg is
    Port ( clk : in STD_LOGIC;
           pos_seg : out std_logic_vector (7 downto 0);
           led_seg : out STD_LOGIC_vector (7 downto 0));
end sevseg;

architecture Behavioral of sevseg is
signal delay : natural range 0 to 1000 := 0;
signal number : natural range 0 to 7 := 0;
begin
process (clk)
begin
if rising_edge(clk) then
    delay <= delay + 1;
    if delay >= 1000 then
        delay <= 0;
        
        number <= number + 1;
        if number >= 7 then
            number <= 0;
        end if;
    end if;
end if;
end process;

process (number)
    begin
        case number is
        when 0 => pos_seg <="01111111";
        when 1 => pos_seg <="10111111";
        when 2 => pos_seg <="11011111";
        when 3 => pos_seg <="11101111";
        when 4 => pos_seg <="11110111";
        when 5 => pos_seg <="11111011";
        when 6 => pos_seg <="11111101";
        when 7 => pos_seg <="11111110";
        end case;
end process;

process (number)
    begin
        case number is
        when 0 => led_seg <="11111001";
        when 1 => led_seg <="10100100";
        when 2 => led_seg <="10110000";
        when 3 => led_seg <="10011001";
        when 4 => led_seg <="10010010";
        when 5 => led_seg <="00000010";
        when 6 => led_seg <="11111000";
        when 7 => led_seg <="00000000";
        end case;
end process;
end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<h5>Port yang digunakan I/O Planning</h5>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-14.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

## Program Binary to BCD Seven Segment

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-15.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-16.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Binary to BCD" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx leaf cells in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity sevseg2 is
    Port ( bcd_input : in std_logic_vector(3 downto 0);
           seg_output : out STD_LOGIC_vector(6 downto 0);
           display_sel : out STD_LOGIC_vector(7 downto 0));
end sevseg2;

architecture Behavioral of sevseg2 is

begin
    process(bcd_input)
    begin
        case bcd_input is
            when "0001" => seg_output <= "1111001";
            when "0010" => seg_output <= "0100100";
            when "0011" => seg_output <= "0110000";
            when "0100" => seg_output <= "0011001";
            when "0101" => seg_output <= "0010010";
            when "0110" => seg_output <= "0000010";
            when "0111" => seg_output <= "1111000";
            when "1000" => seg_output <= "0000000";
            when others => seg_output <= "1111111";
        end case;
        
        case bcd_input is
            when "0001" => display_sel <= "11111110";
            when "0010" => display_sel <= "11111101";
            when "0011" => display_sel <= "11111011";
            when "0100" => display_sel <= "11110111";
            when "0101" => display_sel <= "11101111";
            when "0110" => display_sel <= "11011111";
            when "0111" => display_sel <= "10111111";
            when "1000" => display_sel <= "01111111";
            when others => display_sel <= "11111111";
        end case;           
    end process;
end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<h5>Port yang digunakan I/O Planning</h5>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babFive/Ba5-17.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>
