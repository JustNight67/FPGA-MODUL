---
weight: 3
title: "Sejarah Field Programmable Gate Array"
description: "Memahami awal sejarah Field Programmable Gate Array Diciptakan"
icon: "captive_portal"
date: "2026-05-15T11:44:30+07:00"
lastmod: "2026-05-15T11:44:30+07:00"
toc: true
---

Pada bab briefing ini, praktikan akan mempelajari tentang sejarah awal FPGA, konsep dasar dan cara kerja FPGA, konsep dasar gerbang logika, serta software dan hardware yang akan digunakan dalam praktikum FPGA. Asisten praktikum atau praktikan dapat membaca tujuan dan persyaratan praktikum bab ini agar praktikum dapat berjalan sesuai prosedur.

## Tujuan

{{< table "table-striped" >}}
| **TUJUAN** | **PENJELASAN** |
|---------|------|
| **Memahami sejarah perkembangan FPGA** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami sejarah awal perkembangan FPGA dan bagaimana teknologi ini berevolusi hingga digunakan secara luas saat ini.</p> |
| **Memahami konsep dasar dan cara kerja FPGA** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami komponen FPGA dan cara kerja pada FPGA. </p> |
| **Memahami jenis-jenis software dan hardware FPGA** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami software dan hardware yang akan digunakan untuk desain dan simulasi FPGA.</p> |
| **Memahami konsep dasar dari gerbang logika** | <p style="text-align: justify;>">Praktikan diharapkan dapat mengenali dan menjelaskan fungsi dasar gerbang logika seperti AND, OR, NOT, NAND, NOR, XOR, XNOR dan bagaimana gerbang-gerbang ini digunakan dalam desain FPGA.</p> |
{{< /table >}}

## Persyaratan

<span class=""> </span>

Disarankan praktikan menggunakan hardware dan software sesuai pada dokumentasi ini. Apabila terdapat versi hardware atau software yang cukup lama dari versi yang direkomendasikan maka sebaiknya bertanya kepada Asisten Mengajar Shift.

{{< table "table-striped" >}}
| **HARDWARE YANG DIBUTUHKAN PRAKTIKUM** | **JENIS** |
|--|--|
| **PC / Laptop CPU** | **≥ 4 Cores** |
| **PC / Laptop RAM** | **≥ 4 GB** |
| **PC / Laptop Storage** | **≥ 50GB** |
{{< /table >}}

{{< table "table-striped" >}}
| **SOFTWARE YANG DIBUTUHKAN PRAKTIKUM** |
|--|--|
| **Vivado Design Suite**|
{{< /table >}}

{{< alert context="info" text="Diusahakan untuk memakai **Versi** dan **Aplikasi** yang sama agar tidak terjadinya kesalahan yang tidak diinginkan!." />}}

## Sejarah FPGA

<span class=""> </span>

FPGA (Field Programmable Gate Array) merupakan sebuah IC digital yang digunakan untuk merangkai rangkaian digital. FPGA ini mulai diperkenalkan pada tahun 1980 dan dikembangkan sejak tahun 1985 oleh perusahaan Xilinx yang berbasis di San Jose, California yang menciptakan FPGA pertama adalah XC2064 pada tahun 1985. Perangkat ini sangat primitif, dengan hanya 800 gerbang, hanya sebagian kecil jika dibandingkan dengan jutaan operasi gerbang yang dapat dilakukan pada FPGA saat ini. Perangkat ini juga relatif mahal, yaitu $55, yang jika disesuaikan dengan inflasi akan menjadi sekitar $145 saat ini. Meskipun demikian, XC2064 telah memulai seluruh industri, dan Xilinx telah menjadi salah satu perusahaan dominan di pasar FPGA selama lebih dari
30 tahun. Selain Xilinx, terdapat juga beberapa perusahaan lain yang memproduksi FPGA seperti Altera, Lattice, dan Quicklogic.

## Versi Produk FPGA Xilinx

1. Virtex Family
2. Kintex Family
3. Artix Family
4. Zynq Family
5. Spartan Family
6. Easy Path
7. Versal

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-1.png" alt="Gambar B.1 - Nexys Board A7" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.1</b> Nexys Board A7</p>

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-2.png" alt="Gambar B.2 - Nexys Board A4" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.2</b> Nexys Board A4</p>