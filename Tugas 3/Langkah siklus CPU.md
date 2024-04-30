<img width="717" alt="Tangkapan Layar 2024-03-25 pukul 21 38 40" src="https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/4111298e-625a-4475-9508-f555485bbab0">

Ambil alamat 0 kemudian baca nilainya di alamat 0 load 6 dan jalankan di alamat 6
 Alamat 6 mempunyai value 1 dan ditempatkan di akumulator

<img width="717" alt="Tangkapan Layar 2024-03-25 pukul 21 39 23" src="https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/4c571a56-779c-412a-befb-dee2a0f0838a">

setelah looping kembali lagi fetch menambil alamat dalam memori yaitu 1 kemudian alamat 1 dilakukan pengkodean membaca perintah ADD 7 selanjutnya dilakukan eksekusi perintah pada alamat 7 nilai 1 ditambahkan ke accumulator sehingga yang awalnya 1 ditambah value dari address 7 menjadi 2.

<img width="717" alt="Tangkapan Layar 2024-03-25 pukul 21 39 49" src="https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/7b5473ef-13e8-48dd-8a20-d2d621f26b87">
 
proses fetch menggunakan addres 2, dekode, dan baca nilai di addres 2, yang memiliki penyimpanan value 6  kemudian dijalankan sebagai instruksi untuk memasukkan nilai akumulator ke addres 6, menciptakan addres 6 di mana nilai aslinya berada
 Tadinya 1, tapi akan diubah menjadi 2

<img width="717" alt="Tangkapan Layar 2024-03-25 pukul 21 40 16" src="https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/35447e1d-bda2-4307-83d4-dac81c62130a">

Proses fetch mengambil nilai 3, membaca instruksi di addres 3, jump 1, dan kemudian melakukan value jump dengan kata lain, ia melompat ke addres 1, sehingga nilai di addres 0 tidak lagi diambil. Proses ini adalah yang terakhir dan proses  kembali  ke value add 7 seperti proses 2
