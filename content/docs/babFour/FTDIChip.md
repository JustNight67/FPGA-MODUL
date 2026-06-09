---
weight: 22
title: "FTDI (Future Technology Devices International)"
description: "Memahami definisi dan cara kerja dari FTDI Chip"
icon: "Memory"
date: "2025-10-13T12:24:40+07:00"
lastmod: "2025-10-13T12:24:40+07:00"
toc: true
---

## FTDI Chip

FTDI (Future Technology Devices International) adalah perusahaan yang memproduksi chip konverter USB-to-serial. Komunikasi UART tidak bisa diterapkan melalui jalur USB secara langsung tanpa menggunakan sebuah modul FTDI. Modul ini mengelola transaksi data dengan menerapkan protokol USB dari data yang ditransfer melalui serial asinkron. Ini memungkinkan perangkat modern dengan port USB untuk berkomunikasi dengan perangkat yang menggunakan antarmuka serial tradisional seperti RS-232, RS-485, atau TTL. Tanggung jawab perangkat ini adalah untuk memberitahu PC bahwa perangkat yang digunakan dengan menambahkan beberapa informasi identifikasi, sehingga PC dapat memuat driver yang tepat.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFour/Ba4-4.png" alt="Gambar 4.4 - FTDI Chip" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 4.4</b> FTDI Chip</p>

<span></span>

### Cara Kerja FTDI Chip

<ul><li>Ketika data serial diterima, FTDI Chip mengubahnya menjadi format USB yang dapat dipahami oleh komputer.</li></ul>
<ul><li>Sebaliknya, ketika komputer mengirimkan data USB, FTDI Chip mengubahnya menjadi format serial yang dapat dipahami oleh perangkat yang terhubung.</li></ul>

FTDI Chip juga melakukan konversi level logika antara 3.3V atau 5V (umumnya digunakan oleh perangkat serial) dan 5V (umumnya digunakan oleh port USB).