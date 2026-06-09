---
weight: 4
title: "Komponen Field Programmable Gate Array"
description: "Memahami komponen yang digunakan pada Field Programmable Gate Array"
icon: "device_hub"
date: "2026-05-15T11:44:29+07:00"
lastmod: "2026-05-15T11:44:29+07:00"
toc: true
---

Bila dilihat dari namanya, (Field Programmable) dapat diartikan bahwa FPGA ini bersifat dapat dirancang sesuai dengan keinginan dan kebutuhan user atau pemakai. Sedangkan (Gate Array) artinya FPGA ini terdiri atas gerbang- gerbang digital dimana masing-masing dari gerbang tersebut dapat dikonfigurasikan antara satu sama lain. FPGA ini juga memiliki sifat volatile, yaitu sifat dimana apabila sumber dayanya dicabut maka program yang sudah ditanam sebelumnya akan hilang. Namun dibeberapa perangkat, sudah ada yang ditanamkan ROM untuk dapat menyimpan program yang sudah dibuat.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-3.png" alt="Gambar B.3 - Komponen FPGA" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.3</b> Komponen FPGA</p>

Dalam FPGA terdapat komponen-komponen yang memiliki fungsinya masing-masing yaitu:

## Configure Logic Blocks 

adalah komponen utama dari FPGA yang berfungsi memproses segala bentuk logika yang di blok user atau pengguna. CLB biasanya terdiri dari beberapa elemen logika (gerbang logika, LUT (Look Up Tables), Flip-Flop, dan multiplexer) dan digunakan untuk memproses rangkaian logika yang dibuat oleh pengguna.

## I/O Blocks 

Berfungsi sebagai interface yang dapat diprogram untuk input dan output transfer data dalam FPGA.

## Block RAM 


Blok memori yang berfungsi sebagai penyimpanan data dalam FPGA.

## Programmable Interconect 


Bagian ini berfungsi sebagai saklar yang menghubungkan antara satu CLB dengan CLB lainnya.