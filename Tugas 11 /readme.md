
**Daftar Tugas**

## Perbedaan Serial, Parallel, Concurent dan Concurent Parallel

1. [ Parallel ](https://github.com/zakwanaraffi/SysOP24-3123521030/blob/main/Tugas%2011%20/readme.md#parallel)
2. [ Concurent ](https://github.com/zakwanaraffi/SysOP24-3123521030/blob/main/Tugas%2011%20/readme.md#concurent)
3. [ Parallel dan Concurent ](https://github.com/zakwanaraffi/SysOP24-3123521030/blob/main/Tugas%2011%20/readme.md#paraller-dan-concurent)

## Problem

1. [ Bounded-Buffer Problem ](https://github.com/zakwanaraffi/SysOP24-3123521030/blob/main/Tugas%2011%20/readme.md#bounded-buffer-problem)
2. [ Readers and Writers Problem ]()
3. [ Dining Philosopher s Problem ]()

![Tangkapan Layar 2024-05-17 pukul 07 49 55](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/d15ab585-5c27-4db8-ae2b-70ed64b8cc64)

## Parallel

Parallel adalah beberapa proses / proses yang dilakukan secara bersamaan Seperti contoh pada gambar diatas dimana core1 menjalankan task 1 dan core 2 menjalankan task 2 secara bersamaan.



## Concurent

Concurrent adalah sebuah proses yang dijalankan secara sekaligus secara bergantian , bukan seacara bersamaan tapi secara sekaligus. pada gambar {diatas} Core 1 menjalankan task 1.1 core 2 menjalankan task 2.1 lalu core 1 menjalankan task 2.2 core 2 menjalankan task 1.2 dikarenakan proses task 1.2 belum selesai maka core 1 menjslankan task 2.3 lalu core 2 setelah proses dari task 1.2 selesai maka menjalankan proses task 1.3 lalu setelah core 1 selesai makan akan menjalankan proses setelahnya.



## Paraller dan Concurent

Concurrent and Parallel dijalankan secara bersamaan dan bergantian pada dua core. seperti contoh pada gambar judul di atas core 1 menjalankan task 1.1 core 2 menjalankan task 2.1 lalau setelah task 1.1 proses selesai lanjut mrnjalankan task 2.2 dan dan 2.3 secara urut lalu pada core 2 selewsai menjalankan task 2.1 makan akan menjalankan task 1.2 dikarenakan task 1.1 sudah terisi oleh task 2.2 maka core 2 menjalankan task 1.2 dan 1.3 dan seterusnya

## Problem

## Bounded-Buffer Problem

![Tangkapan Layar 2024-05-17 pukul 07 55 24](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/6a14b1d1-ffa7-499a-a717-09d879c32fd1)

Masalah bounded buffer ini adalah proses di antara produsen dan konsumen. Kendala yang dari masalah ini yaitu penjadwalan (scheduling) dan mutual exclusion (mutex) seperti konsumen harus menunggu jika ada buffer kosong , produsen harus menunggu jika buffer sedang penuh, dan hanya satu buffer yang dapat memanipulasi buffer tersebut .Dengan kata lain, terdapat samber daya yang terbatas dan produsen mengisikan (write)harus produknya ke dalam sumber daya tersebut . Sedangkan konsumen akan mengambil (read)) sumber daya yang penuh tersebut dan meninggalkannya pada sumber daya yang kosong. Kompleksitas utama dari masalah tersebut adalah menjaga perhitungan jumlah ketersediaan sumber daya yang kosong ataupun penuh
Untuk mengatasi masalah tersebut.dibutuhkan semaphore yang berfungsi sebagai penjaga agar produsen tidak mengakses sumber Untuk mengatasi masalah sinkronisasi pada bounded buffer problem yaitu Semaphore, Semaphore digunakan untuk mengatur akses produsen dan konsumen terhadap sumber daya. semaphore membantu menjaga ketersediaan sumber daya yang kosong atau penuh serta mengatur akses produsen dan konsumen secara aman.




