# Tugas 5

## Daftar Tugas
- [Cloning Repository](https://github.com/zakwanaraffi/SysOP24-3123521030/tree/main/Tugas%205#cloning-repository)
- [fork01](https://github.com/zakwanaraffi/SysOP24-3123521030/tree/main/Tugas%205#fork01)
- [fork02](https://github.com/zakwanaraffi/SysOP24-3123521030/tree/main/Tugas%205#fork02)
- [fork03](https://github.com/zakwanaraffi/SysOP24-3123521030/tree/main/Tugas%205#fork03)

## Cloning Repository
Buat tulisan tentang konsep fork dan implementasinya dengan menggunakan bahasa pemrograman C! (minimal 2 paragraf disertai dengan gambar)
Akses dan clonning repo : https://github.com/ferryastika/operatingsystem.git
Deskripsikan dan visualisasikan pohon proses hasil eksekusi dari kode program fork01.c, fork02.c, fork03.c,

<img width="814" alt="Tangkapan Layar 2024-04-22 pukul 20 28 00" src="https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/521b11a1-7db2-4b50-9b7c-fa076c4534d3">

Langkah pertama adalah masuk ke superuser dengan mengetikkan su -, kemudian ketikkan sudo apt install gcc g++. Jika mengalami kesalahan atau tidak memiliki akses karena tidak terdaftar dalam file sudoers, Anda dapat menambahkan pengguna ke grup sudo dengan menggunakan perintah sudo usermod -aG sudo (username). Sebagai contoh, jalankan perintah sudo usermod -aG sudo zakwanaraffi untuk menambahkan pengguna dengan nama "zakwanaraffi" ke grup "sudo". Setelah perintah ini dieksekusi, pengguna "zakwanaraffi" akan memiliki akses sudo di sistem tersebut.

Setelah menambahkan pengguna ke grup sudo, dapat kembali mencoba menginstal gcc dan g++ dengan mengetikkan sudo apt install gcc g++

## fork01
Perintah sudo apt install gcc g++ digunakan untuk menginstal compiler GNU untuk bahasa pemrograman C dan C++ di sistem operasi berbasis Debian atau Ubuntu. gcc adalah compiler untuk bahasa pemrograman C, sedangkan g++ adalah compiler untuk bahasa pemrograman C++.

<img width="814" alt="Tangkapan Layar 2024-04-22 pukul 20 31 50" src="https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/067d8fa3-68ba-4fbe-8f36-6fcd8dda85c4">

![1](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/6c1ab502-3c4c-487f-8390-6c43e02c7fd5)


![f 1](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/e3ae6098-7d9b-4a7b-b66d-147eaa454fb2)


Output dari program menampilkan ID proses (PID), ID proses induk (PPID), dan ID pengguna (UID) dari setiap proses. Setelah mencetak informasi tersebut, program akan menunda eksekusi selama tiga detik sebelum mencetak informasi lagi. Program ini akan diulang sebanyak tiga kali.

setelah itu ketikan nano fork01.cpp kemudian ketikan program berikut :
using namespace std;

#include
#include <sys/types.h>
#include <unistd.h>

/* getpid() adalah system call yg dideklarasikan pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
/
int main(void) {
pid_t mypid;
uid_t myuid;
for (int i = 0; i < 3; i++) {
mypid = getpid();
cout << "I am process " << mypid << endl;
cout << "My parent process ID is " << getppid() << endl;
cout << "The owner of this process has uid " << getuid()
<< endl;
/ sleep adalah system call atau fungsi library
yang menghentikan proses ini dalam detik
*/
sleep(3);
}
return 0;
}

lalu untuk keluar krtikan ctrl x untuk exit lalu pilih y untuk mrngrsave dan enter
lalu ketikan Perintah g++ fork01.cpp -o forko1.exe
perintah tersebut untuk mengkompilasi program C++ yang disebut "fork01.cpp" menggunakan compiler g++ dan memberikan output dengan nama "fork01.exe".
lalu ketikan ./fork01.exe untuk menjalankan program tersebut
Analisa

Output program menampilkan ID proses (PID) mereka sendiri dan nilai variabel x dalam loop tak terbatas. Program menggunakan system call fork() untuk membuat proses saat ini, dan menciptakan child process.

## fork02
![2](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/637015d1-991b-4db7-8c13-84dcd7f6221a)

![f2](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/c77d8acb-8d7f-43e5-b04e-3b4efdcf18d2)

Program di atas melakukan proses forking secara berulang sebanyak lima kali. Setiap kali proses forking dilakukan, program mencatat ID proses (PID) dari setiap proses yang dihasilkan. Jika terdapat PID yang berulang, itu menandakan bahwa proses utama telah melakukan forking beberapa kali, menghasilkan beberapa proses anak dengan PID yang sama.

## fork03
![3](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/ef38a95c-7914-467a-b845-1021f6b3d8d8)

![f3](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/39d3f4d0-84c3-4aca-87fd-f7051a4f3e23)

Output program diatas melakukan proses forking secara looping (berulang) sebanyak 5 kali, yang menghasilkan proses-proses baru dengan pesan yang mencatat ID proses (PID) masing-masing. Adanya beberapa PID yang berulang menandakan bahwa parent process melakukan fork beberapa kali, menghasilkan proses-proses child dengan PID yang sama.

