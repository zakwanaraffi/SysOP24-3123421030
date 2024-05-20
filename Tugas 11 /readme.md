
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

## Readers and Writers Problem

Reader-Writer Problem ini menggambarkan situasi di mana beberapa proses (pembaca dan penulis) harus mengakses sumber daya bersama (misalnya, basis data) dengan cara tertentu.

Pembaca: Beberapa pembaca dapat membaca data secara bersamaan.

Penulis: Penulis membutuhkan akses eksklusif ke data. Ketika penulis sedang menulis, tidak ada pembaca atau penulis lain yang boleh mengakses data.

Untuk menangani masalah ini, harus dipastikan bahwa tidak ada proses bersamaan yang menyebabkan segala bentuk ketidakkonsistenan data dalam sistem operasi.

![Tangkapan Layar 2024-05-20 pukul 22 14 58](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/cca53f05-fc1a-4c1e-aded-21518d5cfffc)

Untuk mengatasi permasalahan ini , terdapat 3 solusi yang dapat dilakukan.
1.solusi dengan memprioritaskan pembaca. Solusi ini tepat digunakan jika tujuan yang ingin dicapai adalah memperoleh throughput semaksimal mungkin Solusi ini bekerja dengan lebih memprioritaskan pembaca meskipun sudah banyak writer yang mengantri.

2.solusi dengan memprioritaskan penulis. Pada solusi ini, jika tidak ada yang mengaksess berkas maka penulis akan mengakses berkas dan pembaca akan dibiarkan mengantri sampai semua penulis menyelesaikan tugasnya . Keuntungan solusi ini adalah pembaca dapat memperoleh informasi yang selau up-to-date. Namun , kedua solusi tersebut tidak memenuhi syarat bahwa setiap thread tidak boleh dibiarkan menunggu untuk waktu yang tidak terbatas.

3.Solusi yang ketiga adalah pembaca dan penulis memperoleh prioritas yang sama secara bergantian. Pada solusi ini, penulis dan pembaca diberi giliran yang adil dalam hal pengaksesan berkas . Jika tidak ada thread pembaca yang sedang mengakses penulis dapat mengaksesnya. Dan jika selesai maka akan memberikan gilira pembaca untuk mengakses berkas . Dengan solusi ini., tidak ada thread yang dalam waktu yang tidak terbatas maka cara ini merupakan cara yang tepat ui menyelesaikan masalah konkurensi.

## Dining Philosopher s Problem

Dining Philosopher s Problem adalah masalah klasik dalam ilmu komputer yang menggambarkan sinkronisasi dan deadlock dalam sistem konkuren. Diperkenalkan oleh Edsger Dijkstra pada tahun 1965, masalah ini menggambarkan situasi di mana lima filsuf duduk di meja bundar dengan satu piring spaghetti di depan masing-masing. Ada garpu di antara setiap dua filsuf, dan setiap filsuf membutuhkan dua garpu untuk makan.

![Tangkapan Layar 2024-05-20 pukul 22 16 06](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/ed0494de-dca9-4c28-8d1a-4523a1a6c9ae)

Solusi Waiter Solusi sederhana ini dilakukan dengan mengadakan seorang waiter yang senantiasa mengawasi penggunaan sumpit di meja makan. Ketika empat buah (dua pasang) sumpit sedang dipakai, orang berikutnya yang ingin memakai sumpit harus meminta izin kepada sang waiter, yang hanya dapat diberi ketika salah satu sumpit telah selesai terpakai.

Contoh: Misalkan ke-lima orang tersebut dinamakan dari A sampai E secara berurutan.

Ketika A dan C sedang makan, 4 buah sumpit sedang terpakai. B tidak memiliki kedua sumpit, dan D dan E memiliki satu buah sumpit diantara mereka.

Apabila D ingin makan dan mengambil sumpit ke-lima, deadlock sangat mungkin terjadi . Maka waiter akan meminta D untuk menunggu, hingga pada saat salah satu sumpit telah selesai dipakai.






