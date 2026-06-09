---
weight: 8
title: "Jenis - Jenis Gerbang Logika"
description: "memahami jenis dan Definisi dari Gerbang Logika"
icon: "Gate"
date: "2026-05-15T11:44:25+07:00"
lastmod: "2026-05-15T11:44:25+07:00"
toc: true
---

## Gerbang AND

Gerbang AND adalah gerbang logika dasar yang melakukan perkalian logika berdasarkan dari input yang diterapkan padanya. Gerbang ini menghasilkan output HIGH atau bernilai 1, hanya ketika semua input atau masukan bernilai 1. Jika tidak, output gerbang AND akan memiliki nilai LOW atau 0.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-11.png" alt="Gambar B.11 - Gerbang Logika AND" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.11</b> Gerbang Logika AND</p>

<p style="text-align: center;"><b>Tabel B.4</b> Truth Table AND</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>A</b></p> | <p style="text-align: Center;"><b>B</b></p> | <p style="text-align: center;"><b>OUT</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |

{{< /table >}}

## Gerbang OR

Gerbang OR adalah gerbang logika dasar yang melakukan penjumlahan logika berdasarkan nilai dari input yang diterapkan pada gerbang. Gerbang ini akan menghasilkan nilai 1 apabila salah satu atau semua input memiliki nilai 1. Apabila tidak terdapat nilai 1 dari input, maka output gerbang OR akan bernilai 0.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-12.png" alt="Gambar B.12 - Gerbang Logika OR" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.12</b> Gerbang Logika OR</p>

<p style="text-align: center;"><b>Tabel B.5</b> Truth Table OR</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>A</b></p> | <p style="text-align: Center;"><b>B</b></p> | <p style="text-align: center;"><b>OUT</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |

{{< /table >}}

## Gerbang NOT

Gerbang NOT atau disebut juga sebagai inverter, akan menghasilkan output yang komplemen dengan hasil inputnya. Jika inputnya bernilai 1 maka output akan bernilai 0 dan sebaliknya.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-13.png" alt="Gambar B.13 - Gerbang Logika NOT" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.13</b> Gerbang Logika NOT</p>

<p style="text-align: center;"><b>Tabel B.6</b> Truth Table NOT</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>A</b></p> | <p style="text-align: center;"><b>OUT</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | 

{{< /table >}}

## Gerbang NAND

Gerbang NAND adalah gabungan dari gerbang logika AND dan juga gerbang logika NOT. Hasil dari gerbang logika NAND adalah kebalikan dari gerbang AND.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-14.png" alt="Gambar B.14 - Gerbang Logika NAND" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.14</b> Gerbang Logika NAND</p>

<p style="text-align: center;"><b>Tabel B.7</b> Truth Table NAND</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>A</b></p> | <p style="text-align: Center;"><b>B</b></p> | <p style="text-align: center;"><b>OUT</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |

{{< /table >}}

## Gerbang NOR

Gerbang NOR adalah gabungan dari gerbang logika OR dan juga gerbang logika NOT. Hasil dari gerbang logika NOR adalah kebalikan dari gerbang OR.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-15.png" alt="Gambar B.15 - Gerbang Logika NOR" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.15</b> Gerbang Logika NOR</p>

<p style="text-align: center;"><b>Tabel B.8</b> Truth Table NOR</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>A</b></p> | <p style="text-align: Center;"><b>B</b></p> | <p style="text-align: center;"><b>OUT</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |

{{< /table >}}

## Gerbang XOR

Gerbang XOR (Exclusive OR) adalah gerbang logika paritas ganjil yang akan menghasilkan nilai 1 apabila kedua inputnya memiliki nilai yang berbeda.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-16.png" alt="Gambar B.16 - Gerbang Logika XOR" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.16</b> Gerbang Logika XOR</p>

<p style="text-align: center;"><b>Tabel B.9</b> Truth Table XOR</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>A</b></p> | <p style="text-align: Center;"><b>B</b></p> | <p style="text-align: center;"><b>OUT</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |

{{< /table >}}

# Gerbang XNOR

Gerbang XNOR (Exclusive NOR) adalah gerbang logika paritas genap yang akan menghasilkan nilai 1 apabila kedua inputnya memiliki nilai yang sama.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-17.png" alt="Gambar B.17 - Gerbang Logika NOR" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.17</b> Gerbang Logika XNOR</p>

<p style="text-align: center;"><b>Tabel B.10</b> Truth Table XNOR</p>

{{< table "table-striped" >}}
| <p style="text-align: center;"><b>A</b></p> | <p style="text-align: Center;"><b>B</b></p> | <p style="text-align: center;"><b>OUT</b></p> |
|---------|------|-------------|----|
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |
| <p style="text-align: center;"><b> 0 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 0 </b></p> | <p style="text-align: center;"><b> 0 </b></p> |
| <p style="text-align: center;"><b> 1 </b></p> | <p style="text-align: Center;"><b> 1 </b></p> | <p style="text-align: center;"><b> 1 </b></p> |

{{< /table >}}