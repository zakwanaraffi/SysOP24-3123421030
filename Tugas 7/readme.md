# Tugas 7

## Daftar Tugas
- [Forking](https://github.com/zakwanaraffi/SysOP24-3123521030/tree/main/Tugas%207#forking)
- [Orphan](https://github.com/zakwanaraffi/SysOP24-3123521030/tree/main/Tugas%207#orphan)
- [Zombie](https://github.com/zakwanaraffi/SysOP24-3123521030/tree/main/Tugas%207#zombie)

## Forking
![f](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/7763fafb-bb0f-4741-a6e2-b3baf54a11e0)


masuk ke directory operatingsystem dengan mengetik cd operatingsyystem lalu menjalankan prooses forking dengan mengetikan perintah ./forking.exe, Perintah g++ forking.c -o forking.exe adalah perintah untuk mengompilasi file sumber C yang disebut forking.c menggunakan compiler g++ dan menghasilkan executable dengan nama forking.exe. untuk orphan dan zombie proses nya sama

## Orphan
![o](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/840cba60-40ce-46b5-89e9-4a113faf92e1)

Program diatas untuk menjalankan child process


## Zombie
![WhatsApp Image 2024-05-05 at 12 42 45](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/70e2ed11-3b53-48b4-8c59-4094f7b79cfb)


zombie.c output program tersebut yaitu Program ini membuat proses menggunakan fork(), dan jika proses tersebut parent process, maka ia akan tidur selama 60 detik (sleep(60)). Namun, jika proses tersebut adalah child process, maka program akan keluar secara langsung

