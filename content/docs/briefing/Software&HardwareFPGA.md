---
weight: 6
title: "Software dan Hardware"
description: "Software dan Hardware yang digunakan pada FPGA"
icon: "Hardware"
date: "2026-05-15T11:44:27+07:00"
lastmod: "2026-05-15T11:44:27+07:00"
toc: true
---

## Software

Pada umumnya, perusahaan pembuat FPGA memberikan perangkat lunak secara gratis yang sudah termasuk kedalam paket pembelian produk mereka. Namun, software yang gratis ini hanya untuk jenis FPGA tingkat rendah- menengah saja, tetapi sudah cukup mendukung untuk digunakan dalam pembelajaran. Berikut beberapa software pendukung yang gratis :

<span class=""> </span>

1.	Xilinx, terkenal dengan software miliknya yang bernama ISE Design Suite dan Vivado.
2.	Altera, terkenal dengan software miliknya yang bernama Quartus.

### Xilinx

Xilinx, Inc. adalah sebuah perusahaan teknologi asal Amerika yang terutama memasok perangkat logika terprogram. Perusahaan ini merupakan pencipta FPGA. Xilinx juga merupakan perusahaan semikonduktor yang menciptakan model manufaktur nirfabrikasi pertama. Didirikan bersama-sama oleh Ross Freeman, Bernard Vonderschmitt, dan James V Barnett II pada tahun 1984, perusahaan ini resmi melantai di NASDAQ pada tahun 1989. Pada bulan Oktober 2020, AMD mengumumkan akuisisi terhadap Xilinx. Akuisisi ini selesai pada tanggal 14 Februari 2022.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-8.png" alt="Gambar B.8 - Logo Vivado" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.8</b> Logo Vivado</p>

<span class=""> </span>

Pembelajaran praktikum sebelumnya menggunakan software ISE Design Suite yang kini diganti menjadi Vivado. Vivado merupakan generasi penerus dari ISE Design Suite, menawarkan sejumlah keunggulan yang membuatnya lebih cocok untuk pembelajaran FPGA saat ini terlebih antarmuka pengguna yang lebih modern dan user-friendly dibandingkan dengan ISE Design Suite.

Vivado mendukung sepenuhnya kedua bahasa pemrograman HDL (Hardware Description Language) yang paling umum digunakan, yaitu VHDL dan Verilog. Ini memungkinkan pengguna untuk mempelajari dan mengimplementasikan desain FPGA menggunakan bahasa yang mereka kuasai atau yang paling sesuai dengan kebutuhan proyek. Software ini dilengkapi dengan alat pengecekan sintaks dan semantik yang kuat. Ini membantu pengguna mengidentifikasi kesalahan dalam kode sebelum proses sintesis, sehingga mempercepat proses debugging dan meningkatkan produktivitas. Hierarki desain dari Vivado membuat pengguna untuk mengorganisasi kode menjadi modul-modul yang lebih kecil dan lebih mudah dikelola.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-9.png" alt="Gambar B.9 - Tampilan Awal Software Vivado" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.9</b> Tampilan Awal Software Vivado</p>

<span class=""> </span>

### Proses Status

<h5> •	Running <img src="/images/briefing/vivado-1.jpg" width="35" class="align-middle me-1"> </h5>

Ikon ini menunjukkan bahwa proses sedang berjalan.

<h5> •	Up-To-Date <img src="/images/briefing/vivado-2.jpg" width="35" class="align-middle me-1"> </h5>

Ikon ini menunjukkan bahwa proses berhasil berjalan dengan tidak ada kesalahan atau peringatan dan tidak perlu mengulangi. Jika ikon di samping proses laporan adalah laporan yang up-to-date, namun tugas-tugas terkait dapat memiliki peringatan atau kesalahan. Jika hal ini terjadi, pengguna dapat membaca laporan tersebut untuk menentukan penyebab dari peringatan atau kesalahan.

<h5> •	Warning Reported <img src="/images/briefing/vivado-3.jpg" width="35" class="align-middle me-1"> </h5>

Ikon ini menunjukkan bahwa proses itu berjalan berhasil tetapi ada peringatan yang muncul.

<h5> •	Error Reported <img src="/images/briefing/vivado-4.jpg" width="35" class="align-middle me-1"> </h5>

Ikon ini menunjukkan bahwa proses itu berjalan, tetapi mengalami error
dan harus di perbaiki.

<h5> •	Out-Of-Date <img src="/images/briefing/vivado-5.jpg" width="35" class="align-middle me-1"> </h5>

Ikon ini menunjukkan bahwa pengguna membuat perubahan desain, yang mengharuskan proses dijalankan ulang. Jika ikon ini berada di samping proses laporan, pengguna dapat menjalankan kembali proses tugas yang terkait untuk membuat versi up-to-date laporan.

<span class=""> </span>

## Hardware

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-10.png" alt="Gambar B.10 - Pin Callout Nexys A7" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.10</b> Pin Callout Nexys A7</p>

<p style="text-align: center;"><b>Tabel B.1</b> Pin Callout dan keterangannya</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>Callout</b></p> | <p style="text-align: Center;"><b>Component Description</b></p> | <p style="text-align: center;"><b>Callout</b></p> | <p style="text-align: Center;"><b>Component Description</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;">**1**</p> | <p style="text-align: center;"> Power Jack </p> | <p style="text-align: center;">**16**</p> | <p style="text-align: center;">JTAG port for (optional) external cable</p> |
| <p style="text-align: center;">**2**</p> | <p style="text-align: center;"> Power Switch </p> | <p style="text-align: center;">**17**</p> | <p style="text-align: center;">Tri-color (RGB) LEDs</p> |
| <p style="text-align: center;">**3**</p> | <p style="text-align: center;"> USB host connector </p> | <p style="text-align: center;">**18**</p> | <p style="text-align: center;">Slide switches</p> |
| <p style="text-align: center;">**4**</p> | <p style="text-align: center;"> PIC24 programming port (factory use) </p> | <p style="text-align: center;">**19**</p> | <p style="text-align: center;">LEDs</p> |
| <p style="text-align: center;">**5**</p> | <p style="text-align: center;"> Ethernet connector </p> | <p style="text-align: center;">**20**</p> | <p style="text-align: center;">Power supply test point(s)</p> |
| <p style="text-align: center;">**6**</p> | <p style="text-align: center;"> FPGA programming done LED </p> | <p style="text-align: center;">**21**</p> | <p style="text-align: center;">Eight digit 7-seg display</p> |
| <p style="text-align: center;">**7**</p> | <p style="text-align: center;"> VGA connector </p> | <p style="text-align: center;">**22**</p> | <p style="text-align: center;">Microphone </p> |
| <p style="text-align: center;">**8**</p> | <p style="text-align: center;"> Audio connector </p> | <p style="text-align: center;">**23**</p> | <p style="text-align: center;">External configuration jumper (SD / USB)</p> |
| <p style="text-align: center;">**9**</p> | <p style="text-align: center;"> Programming mode jumper </p> | <p style="text-align: center;">**24**</p> | <p style="text-align: center;">MicroSD card slot </p> |
| <p style="text-align: center;">**10**</p> | <p style="text-align: center;"> Analog signal Pmod port (XADC) </p> | <p style="text-align: center;">**25**</p> | <p style="text-align: center;">Shared UART/ JTAG USB port </p> |
| <p style="text-align: center;">**11**</p> | <p style="text-align: center;"> FPGA configuration reset button </p> | <p style="text-align: center;">**26**</p> | <p style="text-align: center;">Power select jumper and battery header </p> |
| <p style="text-align: center;">**12**</p> | <p style="text-align: center;"> CPU reset button (for soft cores) </p> | <p style="text-align: center;">**27**</p> | <p style="text-align: center;">Power-good LED</p> |
| <p style="text-align: center;">**13**</p> | <p style="text-align: center;"> Five pushbuttons </p> | <p style="text-align: center;">**28**</p> | <p style="text-align: center;">Xilinx Artix-7 FPGA </p> |
| <p style="text-align: center;">**14**</p> | <p style="text-align: center;"> Pmod port(s) </p> | <p style="text-align: center;">**29**</p> | <p style="text-align: center;">DDR2 memory </p> |
| <p style="text-align: center;">**15**</p> | <p style="text-align: center;"> Temperature sensor </p> | 


{{< /table >}}

### Artix-7

Artix-7 merupakan salah satu seri board FPGA (Field Programmable Gate Array) yang diproduksi oleh Xilinx. Artix-7 dirancang khusus untuk memberikan performa yang optimal dengan biaya yang terjangkau. Seri ini sangat populer digunakan dalam berbagai aplikasi karena memiliki fitur yang lengkap dan memiliki konsumsi daya yang rendah, serta mudah untuk digunakan.

### Nexys A7

Nexys™A7, yang berbasis pada FPGA Artix-7, memiliki performa dan desain yang berfokus untuk digunakan oleh pelajar. Dengan FPGA berkapasitas besar, memori eksternal yang luas, dan berbagai port seperti USB, Ethernet, dan lainnya, Nexys A7 dapat digunakan untuk mendesain rangkaian digital dasar hingga proses yang kompleks.

<p style="text-align: center;"><b>Tabel B.2</b> Spesifikasi Neyxs A7</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b> FPGA </b></p> | <p style="text-align: left;"><b> XC7A100T-1CSG324C </b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;">I/O Interfaces</p> | <ul><li>USB-UART</li><li>One 10/100 Ethernet</li><li>USB OTG 2.0</li><li>USB-UART bridge</li><li>12-bit VGA</li><li>3-axis accelerometer</li><li>PWM audio output</li><li>Temperature sensor</li><li>PDM microphone</li><li>USB HID</li></ul> |
| <p style="text-align: center;">Memory</p> | <ul><li>128 Mbyte DDR2</li><li>128 Mbit Serial Flash</li><li>Micro SD card connector</li></ul> |
| <p style="text-align: center;">Display</p> | <ul><li>2 4-digit 7-segment display</li></ul> |
| <p style="text-align: center;">Switch LED</p> | <ul><li>16 Slide switches</li><li>16 LEDs</li><li>2 tri-color LEDs</li><li>5 Push-buttons</li></ul> |


{{< /table >}}
