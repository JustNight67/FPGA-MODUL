---
weight: 7
title: "Hardware Description Language"
description: "Memahami jenis bahasa apa saja yang digunakan pada HDL"
icon: "captive_portal"
date: "2026-05-15T11:44:26+07:00"
lastmod: "2026-05-15T11:44:26+07:00"
toc: true
---

## Definisi HDL (Hardware Description Language)

Salah satu metode untuk perancangan rangkaian adalah menggunakan HDL (Hardware Description Language). Nantinya, tiap-tiap komponen serta jalur yang menghubungkannya akan dideskripsikan lewat tulisan atau kode tertentu. Tiap vendor FPGA memiliki aturan mengenai penggunaan kode dalam hal implementasi di dalam FPGA. Namun, sejak sekitar 10 tahun lalu, telah muncul kode baru yang dapat diimplementasikan ke dalam semua jenis FPGA buatan vendor manapun. Kode baru tersebut ada 2 yakni Verilog dan VHDL. Baik verilog maupun VHDL ternyata lebih terkenal karena mudah dipahami dan dimengerti. Selanjutnya, dua kode ini kemudian menjadi acuan utama dalam proses implementasi rancangan rangkaian ke dalam FPGA (apapun jenis vendornya). Hingga saat ini, metode perancangan menggunakan HDL (baik verilog maupun VHDL) lebih banyak digunakan daripada metode schematic.

### Verilog

Verilog adalah bahasa HDL yang dikembangkan oleh IEEE (Institute of Electrical and Electronic Engineering) dan formatnya berbentuk teks untuk mendeskripsikan rangkaian dan sistem elektronik. Dalam desain elektronik, Verilog digunakan dalam verifikasi melalui simulasi, analisis waktu, analisis uji (penilaian kesalahan), dan sintesis logika.

### VHDL

Pada praktikum ini, kita akan menggunakan VHDL untuk membuat desain program kedalam FPGA tersebut. VHDL (VHISC Hardwere Description Language); VHSIC (Very High Speed Integrated Circuit) adalah sebuah bahasa pemrograman yang dikembangkan oleh IEEE (Institute of Electrical and Electronic Engineering). VHDL juga digunakan sebagai bahasa pemrograman untuk simulasi rangkaian dari komponen-komponen digital. Pada VHDL, konsep serta sintaks banyak diperlukan untuk mengerti bagaimana rancangan VHDL sebagai bagian dari pemrograman FPGA. Dalam kebanyakan kasus, keputusan memilih dan menggunakan kode VHDL daripada kode Verilog atau SystemC, sangat tergantung pada pilihan perancang itu sendiri dan lebih kepada ketersediaan software pendukung serta kebutuhan perusahaan. Untuk mempelajari VHDL, terdapat 5 komponen penting dalam menulis desain programnya, yaitu :

1. Entity
2. Architecture
3. Configuration
4. Package Declaration
5. Package Body

## Perbedaan Bahasa Verilog dan VHDL

Verilog dan VHDL adalah bahasa HDL yang digunakan untuk merancang sirkuit digital. Keduanya memiliki tujuan yang sama, namun memiliki pendekatan yang sedikit berbeda. Verilog cenderung lebih intuitif dan mirip dengan bahasa pemrograman tingkat tinggi, sehingga lebih disukai oleh para engineer yang memiliki latar belakang software. Bahasa ini sering digunakan untuk merancang sirkuit pada tingkat yang lebih rendah. Di sisi lain, VHDL memiliki struktur yang lebih formal dan matematis, membuatnya lebih cocok untuk verifikasi dan simulasi yang kompleks. Bahasa ini sering digunakan dalam proyek-proyek besar dan kompleks yang membutuhkan tingkat abstraksi yang lebih tinggi.

<p style="text-align: center;"><b>Tabel B.3</b> Perbedaan Verilog dan VHDL</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b> Verilog </b></p> | <p style="text-align: Center;"><b> VHDL </b></p> |
|---------|------|-------------|----|
| <p>Bahasa HDL yang digunakan untuk memodelkan sistem elektronik</p> | Bahasa HDL yang digunakan untuk mendeskripsikan sistem digital dan campuran sinyal </p> |
| <p>Berdasarkan bahasa C</p> | Berdasarkan bahasa Pascal </p> |
| <p> *Case Sensitive* </p> | Tidak *Case Sensitive* </p> |
| <p> Tidak mendukung Array multidimensi </p> | Mendukung Array multidimensi </p> |
| <p> Verilog tidak mengizinkan pemanggilan tugas secara bersamaan </p> | VHDL mengizinkan pemanggilan prosedur secara bersamaan </p> |
| <p> Memiliki tipe data yang sederhana </p> | Memiliki tipe data yang kompleks </p> |
| <p> Tidak memiliki *Library* </p> | Terdapat *Library* </p> |

{{< /table >}}
