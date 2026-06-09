---
weight: 11
title: "Library dan Architecture"
description: "Memahami Jenis-jenis Library dan Architecture pada Vivado"
icon: "Library_Books"
date: "2025-08-24T18:41:23+07:00"
lastmod: "2025-08-24T18:41:23+07:00"
toc: true
---

## Library

Pada pemrograman dikenal pula istilah *library* atau pustaka yang biasanya terdapat pada bahasa pemrograman yang lain seperti C atau header pada Pascal. Sebuah *library* adalah sebuah direktori, dan setiap *package* adalah file di dalam direktori tersebut. *File Package* merupakan basis data yang berisi informasi tentang komponen-komponen dalam paket tersebut (*input* komponen, *output*, tipe, dan lain-lain yang berfungsi untuk menggunakan komponen dalam sebuah desain dengan *library*). untuk menentukan pustaka yang akan dicari dan pernyataan use untuk setiap paket yang akan digunakan. Di dalam *Library* tersebut terdapat sub-tree yang disebut sebagai *package*, diantaranya :

<div class="d-flex justify-content-center w-60">
<img src="/images/babOne/Bao-15.png" alt="Gambar 1.4 - Jenis-jenis Library" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 1.4</b> Jenis-jenis Library</p>

<span class=""> </span>

<ul><li>IEEE.STD_LOGIC_1164 : Library ini menyediakan tipe data standar untuk sinyal digital, seperti '0', '1', 'X' (unknown), 'Z' (high impedance), dan lain- lain. Juga menyediakan operasi logika dasar (AND, OR, NOT, dll.).</li>
<ul><li>IEEE.NUMERIC_STD : Library ini menyediakan tipe data numerik yang digunakan untuk operasi aritmetika, seperti integer, unsigned, dan signed.</li>
<ul><li>IEEE.STD_LOGIC_ARITH : Library ini menyediakan operasi aritmetika pada tipe data std_logic_vector.</li>

## Jenis-jenis Architecture

<span class=""> </span>

### Dataflow

*Dataflow* menggambarkan suatu sistem berdasarkan bagaimana data mengalir melalui sistem. Deskripsi *Dataflow* secara langsung mengimplikasikan implementasi pada level gerbang yang sesuai dengan deskripsi gerbang logika yang digunakan. *Dataflow* terdiri dari satu atau lebih pernyataan penugasan sinyal yang berjalan secara bersamaan dan biasanya digunakan pada desain program yang lebih kecil atau sederhana.

<div class="d-flex justify-content-center w-60">
<img src="/images/babOne/Bao-16.png" alt="Gambar 1.5 - Architecture Dataflow" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 1.5</b> Architecture Dataflow</p>

<span class=""> </span>

Gambar tersebut merupakan rangkaian half adder yang terdapat dua input (A, B) dan dua output (S, C). Half adder merupakan rangkaian elektronika yang bekerja melakukan perhitungan penjumalahan dari 2 buah bilangan biner yang masing-masing terdiri dari 1 bit.

**S = *sum***

<span class=""> </span>

**C = *carry***

Berikut adalah kode program untuk membuat rangkaiannya;

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babOne/Bao-17.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Structural" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity half_adder is
	Port (	A : in STD_LOGIC;
		    B : in STD_LOGIC;
		    C : out STD_LOGIC;
		    S : out STD_LOGIC);
end half_adder;

architecture dataflow of half_adder is

begin
S <= A xor B;
C <= A and B;

end dataflow;
		
```

{{% /tab %}}

{{< /tab >}}


### Structural

Architecture jenis ini memerlukan definisi dari setiap komponen yang dipakai. Setiap komponen, harus didefinisikan satu persatu untuk dapat menjadi sebuah rangkaian yang utuh. Structural menggambarkan struktur internal suatu

rangkaian dengan mendeskripsikan komponen-komponen yang lebih kecil (entity).

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babOne/Bao-18.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Structural" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity BAB1_Structural is
    Port (  A : in bit;
            B : in bit;
            C : out bit;
            S : out bit);
end BAB1_Structural;

architecture structural of BAB1_Structural is

    component XOR1
    port (P,Q : in bit; R : out bit);
    end component;

    component AND1
    port (X,Y : in bit; Z : out bit);
    end component;

begin
X1 : XOR1 port map (A,B,S);
A1 : AND1 port map (A,B,C);

end structural;

```

{{% /tab %}}

{{< /tab >}}

### Behavioral

*Architecture Behavioral* menggambarkan perilaku suatu rangkaian secara keseluruhan tanpa mendefinisikan struktur internalnya. *Behavioral* didefinisikan menggunakan kode prosedural yang dieksekusi secara berurutan dan mekanisme utama yang digunakan adalah pernyataan proses. Jenis *architecture* ini biasanya digunakan untuk program yang lebih rumit dan kompleks.

Berikut adalah *truth table* dari rangkaian *half adder* :

<p style="text-align: center;"><b>Tabel 1.1</b> Truth Table Half Adder</p>

{{< table "table-striped" >}}

| <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> |
| :---: | :---: | :---: | :---: |
| **A** | **B** | **Sum** | **Carry** |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

{{< /table >}}

<span class=""> </span>

Jika hasil dari table tersebut diimplementasikan menggunakan architecture Behavioral pada bahasa VHDL maka programnya :

{{< tabs tabTotal="3" tabRightAlign="" >}}
{{% tab tabName="Example" %}}

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babOne/Bao-19.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

{{% /tab %}}

{{% tab tabName="Code Behavioral" %}}

```

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity BAB1_Behavioral is
    Port (  A : in bit;
            B : in bit;
            C : out bit;
            S : out bit);
end BAB1_Behavioral;

architecture Behavioral of BAB1_Behavioral is

begin
    process (a, b)
    begin
        if A&B = "00" then
        S <= '0';
        C <= '0';

        elsif A&B = "10" or A&B = "01" then
        S <= '1';
        C <= '0';

        else
        S <= '0';
        C <= '1';

        end if;
    end process;

end Behavioral;

```

{{% /tab %}}

{{< /tab >}}

<span class=""> </span>

Dari program tersebut, terlihat jelas bahwa jenis ini lebih mengacu pada perilaku dari masing-masing komponen (XOR & AND gate). Perilaku tersebut harus didefinisikan semua untuk mendapatkan hasil yang diinginkan yaitu rangkaian *half adder*. Dalam suatu desain program VHDL, sangat memungkinkan untuk menggunakan lebih dari satu architecture tergantung dari kebutuhan. Namun beberapa architecture tersebut tetap harus memiliki sebuah entity **“One Entity Multiple Architecture”**.


<div class="d-flex justify-content-center w-60">
<img src="/images/babOne/Bao-20.png" alt="Gambar 1.2 -  One Entity Multiple Architecture" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 1.2</b> One Entity Multiple Architecture</p>
