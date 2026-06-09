---
weight: 33
title: "State Encoding"
description: "Memahami konsep State Encoding pada Finite State Machine"
icon: "Code"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

Dalam VHDL, Finite State Machine (FSM) dapat dituliskan dengan berbagai cara. State Encoding pada sebuah FSM memengaruhi kinerjanya dalam hal kecepatan, penggunaan sumber daya (register, logika), dan juga konsumsi daya.

Algortima pengkodean state meliputi :

<ul><li><b>Binary encoding :</b> setiap state diwakili dengan angka biner yang terenkode, misalnya: "000", "001", "010", "011", "100" …</li></ul>
<ul><li><b>One-hot encoding :</b> setiap state direpresentasikan dengan pola bit yang hanya memiliki satu '1', misalnya: "000001", "000010", "000100",
"001000", "010000".
</li></ul>
<ul><li><b>Gray coding :</b> pengkodean di mana setiap transisi antar state hanya berbeda satu bit, misalnya: "000", "001", "011", "010", "110".</li></ul>

Pengkodean yang dipilih sangat bergantung pada sifat desain:

<ul><li>Binary encoding meminimalkan panjang vektor state, sehingga cocok untuk desain berbasis CPLD (Complex Programmable Logic Device).</li></ul>
<ul><li>One-hot encoding biasanya lebih cepat, menggunakan lebih banyak register tetapi lebih sedikit logika, Hal ini membuat one-hot encoding lebih cocok untuk desain berbasis FPGA, di mana register biasanya banyak digunakan.</li></ul>
<ul><li>Gray encoding dapat mengurangi glitches pada FSM yang memiliki cabang terbatas atau bahkan tidak memiliki cabang.</li></ul>

<center>
    <div class="d-flex justify-content-center w-60">
    <img src="/images/babSix/Ba6-5.png" class="img-fluid mb-3 responsive-img" >
    </div>
    </center>

Contoh FSM pada kode di atas bekerja dengan cara berpindah dari satu state ke state berikutnya secara berurutan dan terus berulang. Awalnya, sistem berada pada state IDLE, kemudian pada siklus berikutnya ia akan bertransisi ke state START. Setelah itu, FSM melanjutkan ke state RUN, lalu berpindah ke state DONE. Dari state DONE, FSM kembali lagi ke state IDLE sehingga membentuk suatu siklus yang berulang tanpa henti. Dengan demikian, FSM ini dapat dikatakan sebagai mesin keadaan yang berjalan dalam pola lingkaran, di mana setiap state memiliki transisi yang sudah pasti menuju state berikutnya sesuai urutan yang telah ditentukan.
