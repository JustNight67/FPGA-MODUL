---
weight: 18
title: "RTL Analysis, Synthesis, Impelmentation"
description: "Memahami definisi dan cara kerja dari RTL Analysis, Synthesis dan Implementation"
icon: "Data_Array"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

Pada bab ini, praktikan akan mempelajari konsep dasar RTL Analysis, Synthesize, dan Implementation. RTL (Register Transfer Level) menggambarkan aliran data dan kontrol dalam sirkuit digital, sementara proses synthesis mengubah deskripsi RTL menjadi gerbang logika yang siap diimplementasikan ke FPGA. Praktikan juga akan memahami cara analisis RTL dan implementasi desain secara fisik pada FPGA. Asisten praktikum atau praktikan diharapkan membaca tujuan dan persyaratan bab ini agar praktikum dapat berjalan sesuai dengan prosedur.

## Tujuan

{{< table "table-striped" >}}
| **TUJUAN** | **PENJELASAN** |
|---------|------|
| **Memahami Konsep RTL** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami fungsi RTL Analysis dalam proses desain sirkuit digital, termasuk bagaimana RTL menggambarkan aliran data dan kontrol di dalam sirkuit secara hierarkis.</p> |
| **Melakukan Proses Synthesize** | <p style="text-align: justify;>">Praktikan diharapkan mampu melakukan proses synthesis dari deskripsi RTL menjadi netlist, yaitu mengonversi desain logika dalam HDL (Hardware Description Language) menjadi gerbang logika yang lebih terstruktur dan siap untuk diimplementasikan.</p> |
| **Melakukan Proses Implementasi** | <p style="text-align: justify;>">Praktikan diharapkan mampu memahami dan menjalankan proses implementasi desain digital dari netlist ke dalam perangkat keras FPGA.</p> |
| **Menganalisis Hasil RTL dan Implementasi** | <p style="text-align: justify;>">Praktikan diharapkan dapat menganalisis hasil implementasi RTL, melakukan debugging, dan memahami bagaimana desain HDL direalisasikan secara fisik di FPGA.</p> |
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

## RTL Analysis

RTL atau *Register Transfer Level* adalah level abstraksi (penyederhanaan sistem) yang penting dalam pengembangan FPGA. RTL memungkinkan desainer untuk menspesifikasikan perilaku sirkuit digital yang berfokus pada aliran data dan operasi logika. Pada flow manager yang ada di aplikasi Vivado terdapat RTL Analysis yang berfungsi untuk mengubah kode VHDL yang telah dibuat menjadi desain Elaborated, atau penggambaran skematik berdasarkan dari kode program yang dibuat. Selain itu, RTL Analysis juga digunakan untuk memeriksa apakah kode yang dibuat sudah benar sebelum masuk ke proses Synthesis.

<div class="d-flex justify-content-center w-60">
<img src="/images/babThree/Ba3-1.png" alt="Gambar 3.1 - Hasil Skematik RTL Analysis" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 3.1</b> Hasil Skematik RTL Analysis</p>

<span></span>

## Synthesis

*Synthesis* adalah proses di mana kode RTL yang mendeskripsikan desain hardware diterjemahkan menjadi netlist gerbang logika dan dioptimalkan untuk diimplementasikan pada board FPGA. Netlist sendiri adalah koneksi dari suatu sirkuit elektronik, dan terdiri dari daftar komponen elektronik dalam sirkuit dan daftar node dimana komponen dalam rangkaian terhubung. Secara sederhana, Synthesis mengubah deskripsi perilaku sirkuit menjadi representasi fisik yang dapat di mapping ke resource yang ada pada board FPGA.

<div class="d-flex justify-content-center w-60">
<img src="/images/babThree/Ba3-2.png" alt="Gambar 3.2 - Hasil Skematik RTL Analysis" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 3.2</b> Hasil Skematik RTL Synthesis</p>

<span></span>

## Implementation

*Implementation* adalah tahapan dimana setelah netlist yang dihasilkan dari proses Synthesis dipetakan ke sumber daya fisik pada FPGA dan dirutekan. Tujuannya adalah menghasilkan bitstream yang dapat diprogram ke FPGA untuk mengimplementasikan desain atau rancangan yang telah dibuat. Pada bagian Implementation pengguna juga mendefinisikan user-constraint yang berisikan port dan ketentuan lainnya yang akan diimplementasikan pada board FPGA.

## Melakukan Synthesize dan Implementation Program VHDL

<div class="d-flex justify-content-center w-60">
<img src="/images/babThree/Ba3-3.png" alt="Gambar 3.3 - Tampilan Awal I/O Planning" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 3.3</b> Tampilan Awal I/O Planning</p>

<h5> Keterangan </h5>

<ul><li><b>Tab</b>, mengorganisasi dan menampilkan berbagai aspek dari desain yang akan digunakan pada board FPGA.</ul></li>
<ul><li><b>Main Viewing Area</b>, menampilkan ringkasan proyek dan tampilan grafis dari desain.</ul></li>
<ul><li><b>View Layout Selector</b>, mmenyediakan akses ke konfigurasi tata letak tampilan yang ditentukan.</ul></li>
<ul><li><b>Window</b>, berisi program yang sedang dijalankan.</ul></li>
<ul><li><b>Status Bar</b>, mmenampilkan informasi tentang projek yang sedang dibuka dan objek apa pun yang saat ini berada dibawah kursor.</ul></li>
<ul><li><b>Main Menu</b>, berisi perintah yang tersedia.</ul></li>
<ul><li><b>Project Status Bar</b>, menampilkan status projek dan perintah yang aktif berjalan.</ul></li>
<ul><li><b>Tcl Console and Message Area</b>, menunjukkan status perintah, pesan aplikasi, hasil kompilasi dan laporan.</ul></li>

## Praktek

### Synthesize

<span></span>

1.  Buka Aplikasi Vivado 2020.2

2.  Buka menu File > New Project dan lakukan langkahnya sama seperti pada **BAB** sebelumnya

3.  Buat Entity dengan nama **"BAB3"** kemudian masukan kode program seperti berikut,

    <center>
    <img src="/images/babThree/Ba3-4.png"class="img-fluid mb-3 responsive-img">
    </center>

4. Lalu, pada *Flow Manager* pada bagian *Synthesis* pilih *run Synthesis*,

    <center>
    <img src="/images/babThree/Ba3-5.png"class="img-fluid mb-3 responsive-img">
    </center>

5. Akan muncul menu seperti di bawah ini, lalu klik OK

    <center>
    <img src="/images/babThree/Ba3-6.png"class="img-fluid mb-3 responsive-img">
    </center>

6. Pada tab *Design Runs* akan muncul bahwa program sedang menjalankan *Synthesis* dan tunggu sampai proses menujukan tanda centang hijau seperti gambar dibawah.

    <center>
    <img src="/images/babThree/Ba3-7.png"class="img-fluid mb-3 responsive-img">
    </center>

7. Jika proses *Synthesis* gagal, maka akan muncul peringatan seperti Error dan Critial Warning pada tab messages seperti berikut. 

    <center>
    <img src="/images/babThree/Ba3-8.png"class="img-fluid mb-3 responsive-img">
    </center>

    <center>
    <img src="/images/babThree/Ba3-9.png"class="img-fluid mb-3 responsive-img">
    </center>

8. Jika proses *Synthesis* berhasil akan muncul tampilan seperti gambar dibawah, lalu pilih **Open Synthesized Design**, dan klik OK

    <center>
    <img src="/images/babThree/Ba3-10.png"class="img-fluid mb-3 responsive-img">
    </center>

9.	Langkah selanjutnya yaitu menentukan pin input dan output yang akan digunakan pada board. Pada pojok kanan atas, pilih I/O Planning.

    <center>
    <img src="/images/babThree/Ba3-11.png"class="img-fluid mb-3 responsive-img">
    </center>

10. I/O Planning digunakan untuk mengatur komponen input dan output sesuai dengan yang kita inginkan dengan memasukan pin yang ada pada board FPGA. Berikut adalah tampilan pada window I/O Planning.

    <center>
    <img src="/images/babThree/Ba3-12.png"class="img-fluid mb-3 responsive-img">
    </center>

11. Langkah selanjutnya adalah mengkonfigurasi pin input dan output yang akan digunakan dengan mengklik expand pada “Scalar Ports”, dan isikan seperti dibawah ini.

    <center>
    <img src="/images/babThree/Ba3-13.png"class="img-fluid mb-3 responsive-img">
    </center>

12. Setelah dikonfigurasi, kemudian simpan dengan cara klik tombol “CTRL + S” atau klik ikon save di kiri atas dan akan muncul window baru seperti gambar dibawah. Beri nama file **BAB3**, lalu klik OK

    <center>
    <img src="/images/babThree/Ba3-14.png"class="img-fluid mb-3 responsive-img">
    </center>

13.	Lihat pada bagian Sources, lalu expand (klik panah bawah) pada Constraints.

    <center>
    <img src="/images/babThree/Ba3-15.png"class="img-fluid mb-3 responsive-img">
    </center>

<span></span>

Pada expand Constraits diatas, terdapat file baru dengan format .xdc yang berisikan hasil konfigurasi yang telah dibuat di I/O Planning.

<div class="d-flex justify-content-center w-60">
<img src="/images/babThree/Ba3-16.png" class="img-fluid mb-3 responsive-img">
</div>

Dapat dilihat, file ini berisikan konfigurasi pin yang telah kita buat sebelumnya. Maksud dari file yaitu :

<ul><li>Pin A berada di lokasi V10.</ul></li>
<ul><li>Pin B berada di lokasi U11.</ul></li>
<ul><li>Pin C berada di lokasi V11.</ul></li>

<span></span>

Lokasi ketiga pin tersebut dapat dilihat juga pada board FPGA. Selanjutnya, terdapat IOSTANDARD yang merupakan sebuah deskripsi attribute, sedangkan LVCMOS (Low Voltage Complementary Metal Oxide Semiconductor) adalah sebuah teknologi tegangan rendah yang digunakan pada sirkuit FPGA untuk menjalankan komponen yang akan digunakan. Angka “18” sendiri menunjukkan berapa besar voltase yang digunakan. Pada kasus ini, angka “18” menunjukkan tegangan sebesar 1,8V. Berikut ini merupakan tabel dari LVCMOS tersebut.

<p style="text-align: center;"><b>Tabel 3.1</b> Tabel LVCMOS</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>Logic Volts</b></p> | <p style="text-align: Center;"><b>Tolerance Volts</b></p> | <p style="text-align: center;"><b>Tolerance Percent</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;"><b> 5.0V </b></p> | <p style="text-align: Center;"><b> +/-0.5V </b></p> | <p style="text-align: center;"><b> +/-10.0% </b></p> |
| <p style="text-align: center;"><b> 3.3V </b></p> | <p style="text-align: Center;"><b> +/-0.3V </b></p> | <p style="text-align: center;"><b> +/-9.09% </b></p> |
| <p style="text-align: center;"><b> 2.5V </b></p> | <p style="text-align: Center;"><b> +/-0.2V </b></p> | <p style="text-align: center;"><b> +/-8.00% </b></p> |
| <p style="text-align: center;"><b> 1.8V </b></p> | <p style="text-align: Center;"><b> +/-0.15V </b></p> | <p style="text-align: center;"><b> +/-8.33% </b></p> |
| <p style="text-align: center;"><b> 1.5V </b></p> | <p style="text-align: Center;"><b> +/-0.1V </b></p> | <p style="text-align: center;"><b> +/-8.33% </b></p> |
| <p style="text-align: center;"><b> 1.2V </b></p> | <p style="text-align: Center;"><b> +/-0.1V </b></p> | <p style="text-align: center;"><b> +/-8.33% </b></p> |
| <p style="text-align: center;"><b> 1.0V </b></p> | <p style="text-align: Center;"><b> +/-0.1V </b></p> | <p style="text-align: center;"><b> +/-8.33% </b></p> |
| <p style="text-align: center;"><b> 0.9V </b></p> | <p style="text-align: Center;"><b> +/-0.045V </b></p> | <p style="text-align: center;"><b> +/-5.00% </b></p> |
| <p style="text-align: center;"><b> 0.8V </b></p> | <p style="text-align: Center;"><b> +/-0.04V </b></p> | <p style="text-align: center;"><b> +/-5.00% </b></p> |
| <p style="text-align: center;"><b> 0.7V </b></p> | <p style="text-align: Center;"><b> +/-0.05V </b></p> | <p style="text-align: center;"><b> +/-7.14  % </b></p> |

{{< /table >}}

Setelah membuat file .xdc untuk konfigurasi input dan output, langkah selanjutnya yaitu melakukan Implementation. Jalankan hal tersebut dengan cara klik run implementation, lalu tunggu hingga proses running selesai dan statusnya menjadi centang berwarna hijau.

<center>
    <img src="/images/babThree/Ba3-17.png"class="img-fluid mb-3 responsive-img">
    </center>

<center>
    <img src="/images/babThree/Ba3-18.png"class="img-fluid mb-3 responsive-img">
    </center>

Proses ini dapat diartikan bahwa input dan output yang sudah dikonfigurasikan sebelumnya telah diimplementasikan atau digabungkan dengan source code yang sudah dibuat sebelumnya.

<span></span>

### Implementation

1. Setelah proses Implementation selesai, selanjutnya menjalankan proses **Generate Bitstream** dengan klik Generate Bitstream lalu tunggu hingga proses selesai. Setelah proses berhasil, maka akan muncul tampilan window baru seperti dibawah ini, lalu klik OK.

    <center>
    <img src="/images/babThree/Ba3-19.png"class="img-fluid mb-3 responsive-img">
    </center>

    **Bitstream** adalah sebuah file yang berisi informasi dari konfigurasi yang telah dibuat sebelumnya dan memiliki ekstensi .bit. Pada proses kali ini, Vivado akan men-streaming file bit tersebut ke port yang ada pada board FPGA, dan kita dapat memprogram FPGA sesuai dengan konfigurasi yang diinginkan.

2. Setelah **Bitstream** berhasil dibuat, selanjutnya adalah mengunggah Bitstream tersebut ke board FPGA yang sudah terhubung dengan komputer menggunakan kabel micro USB. Pastikan board FPGA sudah menyala dan benar-benar terhubung.

    <center>
    <img src="/images/babThree/Ba3-20.png"class="img-fluid mb-3 responsive-img">
    </center>

    Expand pada bagian Open Hardware Manager, pilih Open Target, kemudian klik
    Auto Connect dan tunggu hingga prosesnya selesai.

    <center>
    <img src="/images/babThree/Ba3-21.png"class="img-fluid mb-3 responsive-img">
    </center>

3. Setelah proses selesai, masih pada bagian Hardware Manager. Klik **Program Device** dan otomatis akan muncul jenis board yang telah terhubung melalui kabel USB dan pilih “Xc7a100t_0”

    <center>
    <img src="/images/babThree/Ba3-22.png"class="img-fluid mb-3 responsive-img">
    </center>
    
4.	Akan muncul **Window** baru seperti gambar dibawah, lalu klik Program.

    <center>
    <img src="/images/babThree/Ba3-23.png"class="img-fluid mb-3 responsive-img">
    </center>

5. Ketika berhasil pada bagian **Hardware**, akan muncul Programmed yang menandakan bahwa file Bitstream yang telah dibuat berhasil diunggah pada board FPGA.

    <center>
    <img src="/images/babThree/Ba3-24.png"class="img-fluid mb-3 responsive-img">
    </center>

Proses-proses tersebut merupakan langkah akhir untuk menjadikan file program yang dapat digunggah ke board FPGA. Nantinya, file inilah yang dapat dipakai berulang-ulang sesuai dengan kebutuhan dalam menggunakan FPGA. Karena seperti yang kita tahu, FPGA memiliki sifat volatile, yaitu sifat dimana apabila sumber dayanya dicabut maka program yang sudah ditanam sebelumnya akan hilang. Namun, jika sudah memiliki file program ini, kita hanya perlu memasukannya kembali atau melakukan flash program kedalam FPGA tersebut.
