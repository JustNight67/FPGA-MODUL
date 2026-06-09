---
weight: 14
title: "Tipe Data"
description: "Memahami Definisi dan jenis Tipe Data pada VHDL"
icon: "Type_Specimen"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

Pada bab ini, praktikan akan mempelajari konsep dasar architecture dalam VHDL, yang digunakan untuk mendeskripsikan perilaku internal dari sebuah entity. Praktikan akan mempelajari cara membuat architecture sederhana dan bagaimana architecture berfungsi dalam merancang desain yang lebih besar dan kompleks. Asisten praktikum atau praktikan diharapkan membaca tujuan dan persyaratan bab ini agar praktikum dapat berjalan sesuai prosedur.

## Tujuan

{{< table "table-striped" >}}
| **TUJUAN** | **PENJELASAN** |
|---------|------|
| **Mengenal tipe data pada VHDL** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami berbagai tipe data yang tersedia dalam VHDL, seperti std_logic, bit, integer, dan boolean, serta bagaimana setiap tipe data berfungsi dalam mendesain
rangkaian digital.</p> |
| **Membedakan penggunaan tipe data** | <p style="text-align: justify;>">Praktikan diharapkan dapat membedakan penggunaan berbagai tipe data sesuai dengan kebutuhan desain, memahami kapan menggunakan tipe data tertentu untuk memodelkan perilaku dan karakteristik rangkaian yang berbeda. </p> |
| **Menggunakan tipe data array untuk membuata architecture** | <p style="text-align: justify;>">Praktikan diharapkan dapat menggunakan tipe data array dalam VHDL untuk membuat architecture yang lebih kompleks. </p> |
{{< /table >}}

## Persyaratan

<span></span>

Disarankan praktikan menggunakan hardware dan software sesuai pada dokumentasi ini. Apabila terdapat versi hardware atau software yang cukup lama dari versi yang direkomendasikan maka sebaiknya bertanya kepada Asisten Mengajar Shift.

{{< table "table-striped" >}}
| **HARDWARE YANG DIBUTUHKAN PRAKTIKUM** |
|--|--|
| **PC / Laptop** | 
| **FPGA Board Nexys A7 dan Nexys 4** | 
| **Kabel Power USB** | 
{{< /table >}}

{{< table "table-striped" >}}
| **SOFTWARE YANG DIBUTUHKAN PRAKTIKUM** |
|--|--|
| **Vivado Design Suite**|
{{< /table >}}

{{< alert context="info" text="Diusahakan untuk memakai **Versi** dan **Aplikasi** yang sama agar tidak terjadinya kesalahan yang tidak diinginkan!." />}}


## Pengertian

Tipe data adalah atribut yang dilampirkan ke data untuk menyusun VHDL dalam memahami cara memperlakukan data tersebut. Sederhananya, ini merupakan perintah khusus yang memberi tahu compiler pada VHDL apa yang harus dilakukan pada data tersebut dan bagaimana mengolahnya. Pada VHDL, kita mendefinisikan tipe data pada saat menginisialisasi sinyal, variabel, konstanta, dan generik. Untuk menuliskan kode VHDL secara efisien, sangatlah penting untuk mengetahui tipe-tipe data yang diperbolehkan, bagaimana, serta kapan penggunaannya.

## Tipe Data VHDL

VHDL memiliki seperangkat tipe data standar (predefined/built-in) dan juga terdapat tipe data dan subtipe yang didefinisikan pengguna (user defined). Artinya, dalam VHDL tipe data dapat diklasifikasikan sebagai berikut.

## Tipe Data Predefined

VHDL memiliki beberapa tipe data standar (predefined) yang sudah didefinisikan sebelumnya oleh bahasa pemrograman. Tipe data ini menyediakan dasar yang kuat untuk membangun berbagai jenis rangkaian digital. Berikut adalah beberapa tipe data standar yang umum digunakan dalam VHDL :

### Bit

Bit merupakan tipe data paling sederhana dan terpenting untuk sistem digital dan memiliki nilai '0' dan '1'. Setiap objek data dapat dideklarasikan sebagai tipe bit sebelum digunakan sebagai Sinyal, Variabel, atau Konstanta.

<h5>Variable temp : BIT := 0;</h5>

<span></span>

<h5>Variable temp : BIT := 0;</h5>

<span></span>

### Boolean

Boolean hanya memiliki satu nilai yaitu “TRUE” atau “FALSE”. Operasi yang dapat dilakukan pada variabel Boolean dengan gerbang logika adalah gerbang “AND, OR, NOT, NAND, NOR, dan XOR”.

<h5>Variable DONE : BOOLEAN := FALSE;</h5>

<span></span>

<h5>Signal enable : BOOLEAN := TRUE;</h5>

<span></span>

### Numeric

Sesuai dengan namanya, tipe data ini hanya dapat menampung nilai-nilai numerik. Tipe data numerik terdiri dari :

<h5><ul><li>Integer</li></ul></h5>

Tipe data ini dapat menampung nilai dari -2.147.483.647 s/d +2.147.483.647. Selain itu, integer juga memiliki dua buah sub tipe yang sudah didefinisikan pada library, yaitu:

1. Natural, memiliki range nilai dari 0 s/d +2.147.483.647.
2. Positif, memiliki range 1 s/d +2.147.483.647.

<span></span>

<h5><ul><li>Real</li></ul></h5>

Tipe data ini dapat menampung floating point mulai dari -1.0E38 hingga +1.0E38. Selain itu, tipe data ini juga dapat membaca bilangan pi (π) untuk beberapa perhitungan. Bilangan real dapat menyimpan hingga 6 angka dibelakangkoma. Contoh :

**Variable VAL : character := '$';

<span></span>

Semua karakter yang termasuk dalam tipe data ini adalah sebagai berikut :

<div class="d-flex justify-content-center w-100">
<img src="/images/babTwo/Batw-1.png"
class="img-fluid mb-3 responsive-img">
</div>

## Tipe Data User Defined

Tipe data user defined dalam VHDL memungkinkan pengguna untuk mendefinisikan sendiri tipe data khusus yang sesuai dengan rangkaian yang akan dibuat. Ini memberikan fleksibilitas yang lebih besar dalam memodelkan dan mengelola data dalam desain rangkaian digital. Tipe data user defined dibagi menjadi 4 tipe yaitu :

### Tipe Scalar

Tipe scalar adalah jenis data yang hanya dapat menyimpan satu nilai pada satu waktu, maksudnya adalah bahwa sebuah variabel atau sinyal yang dideklarasikan dengan tipe data skalar hanya bisa menyimpan satu nilai tunggal pada saat tertentu, bukan beberapa nilai sekaligus.

<ul><li><b>Enumerated</b>, sangat fleksibel dan dapat digunakan untuk merepresentasikan berbagai jenis data yang memiliki jumlah nilai yang terbatas dan terdefinisi. Tipe data ini dapat berupa Bit, Boolean, Numeric dan character.</ul></li>

**signal bit val : std_logic;**

**bit_val <= '1';**

<span></span>

<ul><li><b>Physical</b>, berisi nilai-nilai yang mewakili pengukuran suatu kuantitas fisik, seperti waktu, panjang, tegangan, dan arus. Nilai-nilai dari tipe ini dinyatakan sebagai kelipatan bilangan bulat dari satuan dasar.</ul></li>

type CURRENT is range 0 to 1 E-9

units

nA; -- (base unit) nano-ampere 

uA = 1000 nA; -- micro-ampere 

mA = 1000 μA; --milli-ampere Amp = 1000 mA; -- ampere

end units;

dan

type TIMEis range 0 to -1 E18 to 1 E18 

units
pS; -- (base unit) Pico Sec 

nS = 1000pS;

µS = 1000nS; 

mS = 1000µS; 

Sec= 1000mS 

Min= 60Sec 

end units;

<span></span>

### Tipe Composites

Ini adalah tipe data yang digunakan untuk menggabungkan beberapa nilai, selain tipe data standar. memungkin representasi struktur data yang lebih kompleks dalam desain rangkaian digital. tipe data ini memiliki dua macam yaitu:

<ul><li><b>Array</b>, digunakan untuk merepresentasikan sebuah objek yang berisi lebih dari satu nilai dengan tipe yang sama. Misalnya, sebuah register delapan bit dapat diwakili sebagai sebuah objek dari tipe array yang terdiri dari nilai-nilai delapan bit. Jadi, delapan nilai dari tipe bit dikelompokkan menjadi satu objek dari tipe array.</ul></li>

**typeADDRESS_WORD is array (0 to 7) of BIT**

<span></span>

<ul><li><b>Record</b>, memungkinkan pengelompokan beberapa elemen yang berbeda jenis menjadi satu entitas tunggal. Dengan kata lain, record memungkinkan kita untuk menggabungkan berbagai tipe data (seperti integer, boolean, std_logic, dll.) dalam satu struktur, yang memudahkan organisasi dan pengelolaan data yang kompleks dalam desain perangkat keras.</ul></li>

type MODULE is 

record
SIZE: INTEGER range 20 to 200; 

CRITICAL_DLY: TIME;

NO_INPUTS: PIN_TYPE;

NO_OUTPUTS: PIN_TYPE;

end record; 

type DATE is 

record
DAY: integer_range 1 to 31; 

MONTH:month_name;

YEAR:integer_range0 to 4000; 

end record;

<span></span>

<ul><li><b>Tipe access</b>, digunakan untuk mendeklarasikan pointer, yaitu referensi ke objek lain dalam memori. Tipe data access memungkinkan akses dinamis ke objek dan data.</ul></li>

variable p : int_ptr; 

p := new integer;
p.all := 5; -- Mengisi nilai 5 ke memori yang ditunjuk oleh p

report integer'image(p.all); -- Menampilkan nilai yang dirujuk oleh p, yaitu 5

<span></span>

<ul><li><b>Tipe File</b>, digunakan untuk membaca dan menulis data dari dan ke file eksternal selama proses simulasi. Ini memungkinkan pengujian, debugging, dan pengumpulan data dengan cara yang lebih fleksibel dan terstruktur.</ul></li>

file my_file : text is in "input_data.txt";
