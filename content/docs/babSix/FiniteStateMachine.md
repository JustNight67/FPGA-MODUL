---
weight: 31
title: "Finite State Machine"
description: "Memahami Definisi dan Komponen apa saja yang digunakan Finite State Machine pada FPGA "
icon: "Developer_Board"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

Pada bab ini, praktikan akan mempelajari Finite State Machine (FSM) dan bagaimana mengimplementasikannya dalam FPGA Nexys A7 menggunakan VHDL. FSM adalah model matematika yang digunakan untuk mendeskripsikan sistem berbasis keadaan (state), yang banyak digunakan dalam kontrol digital, komunikasi, dan otomasi.

## Tujuan

{{< table "table-striped" >}}
| **TUJUAN** | **PENJELASAN** |
|---------|------|
| **Memahami Konsep Finite State Machine (FSM)** | <p style="text-align: justify;>">Praktikan diharapkan memahami konsep dasar FSM, bagaimana cara kerja sistem berbasis keadaan, serta penerapannya dalam sistem digital.</p> |
| **Memahami komponen utama dalam FSM** | <p style="text-align: justify;>">Praktikan diharapkan memahami komponen utama dalam FSM seperti states, transitions, inputs, dan outputs.</p> |
| **Memahami tipe-tipe FSM (Moore & Mealy Machine)** | <p style="text-align: justify;>">Praktikan diharapkan memahami perbedaan antara Moore dan Mealy Machine, termasuk representasi dengan state diagram dan state table.</p> |
| **Memahami metode state encoding** | <p style="text-align: justify;>">Praktikan diharapkan memahami cara mengkodekan keadaan (state encoding) dalam FSM untuk efisiensi implementasi pada FPGA.</p> |
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

Dalam sistem digital, terdapat dua jenis rangkaian dasar. Jenis pertama adalah rangkaian logika kombinasional. Pada rangkaian logika kombinasional, keluaran hanya bergantung pada masukan. Contoh dari rangkaian logika kombinasional antara lain adder, encoder, dan multiplexer. Pada adder, misalnya, keluarannya hanyalah hasil penjumlahan dari masukan; tidak peduli apa masukan atau keluaran sebelumnya.

Jenis kedua dari rangkaian logika digital adalah rangkaian logika sekuensial. Pada rangkaian logika sekuensial, keluaran tidak hanya bergantung pada masukan, tetapi juga pada keadaan (state) sistem saat ini (yaitu nilai keluaran dan sinyal atau variabel internal). Rangkaian logika sekuensial dapat berupa rangkaian sederhana seperti counter yang berpindah dari satu state ke state lainnya dalam urutan dasar (misalnya 0,1,2,3… kemudian kembali ke 0,1,2,3…) hingga rangkaian berskala besar seperti mikroprosesor dengan jutaan state yang berbeda atau lebih. Sistem logika sekuensial merupakan Finite State Machine (FSM). Sebagai FSM, sistem ini terdiri atas sekumpulan state, sejumlah masukan, sejumlah keluaran, serta sekumpulan aturan untuk berpindah dari satu state ke state lainnya.

## Komponen Finite State Machine

Sebuah Finite State Machine terdiri dari beberapa komponen utama yaitu sebagai berikut:

### Finite States

Finite states adalah mode atau kondisi yang berbeda dalam suatu sistem. Setiap state merepresentasikan perilaku tertentu. Dalam representasi sistem digital, state biasanya digambarkan menggunakan simbol atau label.

### State Transitions

Dalam konteks FSM, transisi state didefinisikan sebagai perubahan dari satu state ke state lainnya. Perubahan ini terjadi berdasarkan input atau kondisi tertentu. Transisi state umumnya dipicu oleh suatu peristiwa (event) yang terkait dengan aturan atau kondisi, yang menentukan state berikutnya dari sistem.

### State Diagram

Transisi state dan perilaku dari FSM dapat direpresentasikan dalam bentuk grafis yang dikenal sebagai diagram state. Diagram ini membantu memvisualisasikan bagaimana sistem berpindah dari satu state ke state lain.

### Inputs

Masukan pada FSM adalah sinyal eksternal yang memicu transisi state dalam sistem. Masukan ini bisa berasal dari sensor, perangkat input pengguna seperti mikrofon, keyboard, dan lain-lain.

### Outputs

Keluaran adalah hasil yang dihasilkan oleh sistem berdasarkan masukan dan state saat ini. Keluaran ini dapat digunakan untuk memicu suatu peristiwa, mengendalikan aktuator, atau memberikan umpan balik ke lingkungan eksternal.
