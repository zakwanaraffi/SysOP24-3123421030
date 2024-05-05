## Menerjemahkan Artikel

printf (“HELLO WORD!”); Bagian terbaik tentang pemrograman komputer adalah semua masalahnya berhubungan dengan dunia nyata; program dan perangkat lunak komputer adalah solusi untuk memenuhi kebutuhan sehari-hari Anda dan saya mulai dari pemesanan makanan online, belanja, media sosial, pemesanan tiket, dan lainnya!

Jadi, Misalkan Anda adalah pemilik toko Roti bernama “Bakes and Bytes”; dan kamu bisa membuat maksimal 50 kue karena kamu belum mempunyai oven yang besar. Sekarang, Anda memiliki beberapa pelanggan untuk membelinya, tapi mari kita pertimbangkan hanya satu pelanggan. Toko roti Anda canggih dan karenanya memiliki sistem manajemen yang hebat seperti kode yang diberikan.

//Reference: https://en.wikipedia.org/wiki/Producer%E2%80%93consumer_problem

int OVEN_SIZE = 50;
int cakes = 0;

procedure baker()
{
while (true)
{
cakes = bake_cake();

![Tangkapan Layar 2024-05-05 pukul 12 26 00](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/d6d7ffbf-71ee-4cac-b740-dd3e5773731b)

}

procedure customer()
{
while (true)
{

![Tangkapan Layar 2024-05-05 pukul 12 26 39](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/befebba1-f133-460e-a6cc-03a3db855b1f)

penjelasan dari kode di atas

Jika toko roti Anda memiliki kue==0; lalu Anda mengirim pesan ke semua pelanggan Anda bahwa “sleep();”
Sampai oven Anda belum penuh (kue != 50), pembuat roti Anda terus membuat kue segar.
Namun, jika oven sudah penuh, pembuat roti akan tidur sampai pelanggan membeli kue dan kue != 50. Ini mengirimkan pesan kepada pembuat roti bangun(baker);
Dan jika kue Anda == 1, maka ia akan mengirimkan pesan kepada Pelanggan bahwa wakeup(customer);
Namun pengelolaan ini mempunyai beberapa permasalahan seperti:
Baker memproduksi kuenya dan pada saat yang sama pelanggan ingin mengambilnya. Pada saat yang sama; Pelanggan mengira kuenya sudah siap, sedangkan tukang roti mengira kuenya belum ada sehingga masih berproduksi. Jadi, orang dapat memahami bahwa hal itu menciptakan kekacauan!

Kini konsumen hanya melihat tidak ada kue, lalu hendak tidur. Sekarang, sebelum ia tertidur; bagaimana jika tukang roti menghasilkan kue? Dan setelah tukang roti baru saja membuat kue; toko roti mengirimkan pesan kepada pelanggan “Bangun!”. Namun karena pelanggan tersebut hendak tidur (karena dia mengetahui bahwa tidak ada kue), dan karena itu dia masih terjaga, maka panggilan “Bangun” dari pembuat roti menjadi sia-sia! Sebenarnya Panggilan Bangun itu untuk membangunkan Pelanggan 'Tidur'! Namun karena kurangnya Sinkronisasi, hal ini terjadi.

Sekarang, seperti yang terlihat sebelumnya; ketika pembuat roti memproduksi satu kue, pelanggan tidak muncul; Baker terus memproduksi kue hingga Oven penuh (50 kue)! Dan sesuai kondisi kami 4, pelanggan terbangun ketika kue==1; tapi di sini kuenya bertambah oleh Tukang Roti; jadi kue tidak akan pernah sama dengan satu dan Pelanggan tertidur tanpa batas. Kondisi ini tidak bisa diterima bukan?

Tepat. Ini adalah masalah Produsen-Konsumen. Pria jalanan juga bisa memahami hal sederhana ini, bukan? Namun solusi untuk ini jelas menarik.

![Tangkapan Layar 2024-05-05 pukul 12 27 28](https://github.com/zakwanaraffi/SysOP24-3123521030/assets/160553582/32b78a7b-805c-497a-90b2-a2d1626edb0e)

Formal Explanation:
Masalah produsen dan konsumen adalah masalah sinkronisasi. Ada buffer dengan ukuran tetap (here, OVEN_SIZE) dan produsen (tukang roti) memproduksi (kue) dan memasukkannya ke dalam buffer. Konsumen (]customer) menghapus item dari buffer dan mengkonsumsi (membeli) barang/item tersebut.

Seorang produsen tidak boleh memproduksi barang ke dalam buffer ketika konsumen sedang mengonsumsi suatu barang dari buffer dan sebaliknya. Jadi buffer hanya boleh diakses oleh produsen atau konsumen dalam satu waktu.

Untuk mengatasi hal tersebut, muncullah konsep Semaphores.

Semaphore adalah tipe data variabel atau abstrak yang digunakan untuk mengontrol akses ke sumber daya umum oleh beberapa proses dalam sistem bersamaan seperti sistem operasi multitasking. Semaphore hanyalah sebuah variabel. Variabel ini digunakan untuk memecahkan masalah “Bagian Kritis” dan untuk mencapai sinkronisasi proses dalam lingkungan multi pemrosesan.

Importan Semaphores:

Mutex Lock: Jika disetel '0', berarti terkunci oleh suatu proses dan telah masuk dalam Critical Region; sedangkan jika '1', proses apa pun dapat menguncinya ke '0' dan masuk ke Critikal Section.
Wait and Signal: Tunggu adalah untuk mengurangi semaphore jika memiliki nilai 'S' lebih besar dari sama dengan 0. Sinyal adalah untuk menambah.
tunggu
{
sementara(S<=0); // sibuk menunggu
S--;
}
sinyal
{
S++;
}
1 Produsen, 1 konsumen masalah:
// PART 1/4
Assumption: Buffer SIZE = 1
#include<stdio.h>
#include<pthread.h>
#include<semaphore.h>
#define SHARED 1
void *Producer(); // Make Declaration of Producer
void *Consumer(); // Make Declaration of Consumer
sem_t empty, full; //Declare semaphores to be used
int data; // data variable

Bahasa C sangat kuat. Ini memiliki perpustakaan yang bagus untuk Thread Programing. Seperti di sini dalam kasus kami; masalahnya adalah sinkronisasi proses, kita memerlukan beberapa proses yang berjalan secara bersamaan. Jadi kami menggunakan file header yang berbeda seperti pthread.h dan semaphore.h selain dari 'Studio.h'

//PART 2/4
int main()
{
pthread_t ptid, ctid; // Line 1
printf("\nMain Started");
sem_init(&empty, SHARED, 1); // Line 2
sem_init(&full, SHARED, 0); // Line 3
sem_init(&sm, SHARED, 1);// Line 4
pthread_create(&ptid,NULL,Producer,NULL); // Line 5
pthread_create(&ctid,NULL,Consumer,NULL); // Line 6
pthread_join(ptid,NULL); // Line 7
pthread_join(ctid,NULL); // Line 8
printf("\nMain done\n");
}

Penjelasan:
Baris-1: Buat instance ptid(ID proses induk) dan ctid(ID proses anak) dari pthread_t

Baris 2, 3 dan 4: Kita menginisialisasi semaphore yang dideklarasikan sebagai kosong = 1 dan penuh = 0. Artinya, awalnya buffer kosong (jadi kosong=1) dan tidak penuh (jadi penuh=0) dan kunci mutex sebagai sm diinisialisasi sebagai 1.

Baris 5 dan 6:

sistem memanggil pthread_create(&ptid, NULL,Produser,NULL); membuat thread ptid yang akan dieksekusi hingga berada dalam producer method.

Demikian pula system memanggil pthread_create(&ctid, NULL,Consumer, NULL); membuat thread ctid yang akan dieksekusi hingga berada dalam metode Konsumen.

Baris 7 dan 8:

Panggilan sistem pthread_join (ptid,NULL); memastikan bahwa thread berikutnya menyelesaikan eksekusinya hanya setelah selesainya thread ptid yang diberikan.
Panggilan sistem pthread_join (ctid,NULL); memastikan bahwa thread berikutnya
menyelesaikan eksekusinya hanya setelah selesainya thread ctid yang diberikan.

//PART 3/4
void *Producer()
{
//ITEM PRODUCED...
int produced;
printf("\nProducer created");
printf("\nProducer id is %ld\n",pthread_self()); //print thread id
for(produced=0;produced<100;produced++)
{
sem_wait(&empty);
// LOCK-starts
sem_wait(&sm);
//CRITICAL SECTION STARTS
data=produced;
//CRITICAL SECTION ENDS
sem_post(&sm);
//LOCK-ends
sem_post(&full);
printf("\nProducer: %d",data);
}
}

Penjelasan:
Fungsi Produser berfungsi sebagai berikut:

Setelah barang diproduksi, operasi tunggu dilakukan dalam keadaan kosong. Jika tidak kosong (kosong = 0), maka status sedang menunggu sibuk; sampai kosong=1.

Sekarang, ini menunjukkan bahwa ruang kosong di buffer berkurang 1. Kemudian operasi tunggu dilakukan pada 'sm' sehingga proses konsumen tidak dapat mengganggu karena proses apa pun dapat memasuki bagian kritis jika lock=1.

Namun karena fungsi wait diterapkan pada lock, maka fungsi tersebut berkurang menjadi nol sehingga tidak ada proses lain yang dapat masuk.

Setelah barang dimasukkan ke dalam buffer, operasi sinyal (sem_post) dilakukan pada 'sm' dan penuh. Yang pertama menunjukkan bahwa proses konsumen sekarang dapat bertindak dan yang terakhir menunjukkan bahwa buffer sudah penuh sebesar 1.

//PART 4/4
void *Consumer()
{
int consumed, total=0;
printf("\nConsumer created\n");
printf("\nConsumer id is %ld\n",pthread_self());
for(consumed=0;consumed<100;consumed++)
{
sem_wait(&full);
//LOCK-starts
sem_wait(&sm);
//CRITICAL SECTION STARTS
total=total+data;
//CRITICAL SECTION ENDS
sem_post(&sm);
//LOCK-ends
sem_post(&empty);
printf("\nConsumed: %d",data);
}
printf("\nThe total of 100 iterations is %d\n",total);
}

Penjelasan:
Operasi menunggu dilakukan secara penuh. Hal ini menandakan item yang ada di buffer berkurang 1. Kemudian operasi wait dilakukan pada mutex sehingga proses produser tidak dapat ikut campur.

Kemudian item tersebut dihapus dari buffer. Setelah itu, operasi sinyal dilakukan pada kunci 'sm', yang menunjukkan bahwa kunci dilepas saat pekerjaan selesai; dan sinyal 'kosong' menunjukkan bahwa ruang kosong di buffer bertambah 1.

in this way; seseorang dapat memahami bahwa meskipun beberapa proses berjalan pada waktu yang sama; karena penggunaan semaphore yang benar; 'Race Condition' dan 'Critical Setion Problem' dapat dihindari

1 Producer, 3 Consumenrs Problem :
Karena, sekarang kita sudah jelas dengan pemrograman thread dasar Masalah Produsen-Konsumen, mari kita selami lebih dalam beberapa Masalah Dunia Nyata. Dalam praktiknya, bisa saja ada konsumen ‘n’ untuk satu produsen seperti Toko Roti kita, atau belanja online, atau Reservasi Kereta Api atau yang lainnya. Semua masalah tersebut dapat diselesaikan dengan teknik pemrograman jenis ini.

kode di bawah ini menggambarkan Masalah 1 Produsen dan 3 Konsumen.
PART 1/4
Assumption: Buffer Size = 1
We manually define the 3 consumers the consume exactly one-third of the items produced by the Producer for ease of Understanding.

#include<stdio.h>
#include<pthread.h>
#include<semaphore.h>
#define SHARED 1
void *Producer();
void *Consumer();
sem_t empty, full,sm;
int data;

Penjelasan:
Ketika ada banyak konsumen, masalah sinkronisasi sebenarnya muncul. Untuk itu kita akan menulis logika kode kita dengan beberapa asumsi:

Ukuran Buffer sama dengan 1. (Anda dapat mengimplementasikan buffer berukuran 'n' dengan bantuan array. Namun dengan menjaga kode tetap rapi dan sederhana; kita dapat memahami masalah ini dengan lebih baik)

Kami secara eksplisit mendefinisikan bahwa ketiga konsumen tersebut akan mengambil tepat 1/3 bagian dari barang yang diproduksi (untuk konsumen 'n', 1/n bagian) untuk menghindari penggunaan beberapa semaphore.

int main()
{
pthread_t ptid, ctid1, ctid2, ctid3;
int x=1,y=2, z=3;
int a = &x;
int b = &y;
int c = &z;
sem_init(&empty, SHARED, 1);
sem_init(&full, SHARED, 0);
sem_init(&sm,SHARED,1);
pthread_create(&ptid,NULL,Producer,NULL);
pthread_create(&ctid1,NULL,Consumer,(void)a);
pthread_create(&ctid2,NULL,Consumer,(void)b);
pthread_create(&ctid3,NULL,Consumer,(void)c);
pthread_join(ptid,NULL);
pthread_join(ctid1,NULL);
pthread_join(ctid2,NULL);
pthread_join(ctid3,NULL);
printf("\nMain done\n");
}

Penjelasan:
Di sini, 4 thread berbeda dibuat yaitu Produser(ptid) dan Konsumen( dengan ctid1, ctid2, ctid3). Bersamaan dengan pembuatan, kami meneruskan nomor identifikasi unik sebagai variabel a,b, dan c ke masing-masing thread konsumen.

Setelah itu, dengan menggunakan pthread_join, semua thread dipanggil dan dieksekusi sesuai urutan yang ditentukan oleh 'Kebijakan Penjadwalan' OS.

Poin Penting yang Perlu Diperhatikan:

Thread apa pun yang 'dipanggil' dapat dieksekusi dalam urutan apa pun berdasarkan OS.

Jika kosong=0; dan Thread Produser dipanggil, lalu masuk ke status 'Sibuk Menunggu'; dan OS memanggil thread lain.

Jika penuh=0; dan salah satu Thread Konsumen dipanggil; kemudian masing-masing thread masuk ke Busy Waiting dan kontrol ditransfer ke thread lain.

Misalkan Producer Thread masuk ke Busy Waiting terlebih dahulu, kemudian Consumer Thread dieksekusi dan penambahan blank=1; jadi setelah dijalankan, Producer Thread keluar dari Busy Waiting State dan bisa berproduksi jika diberi charge. Demikian pula untuk thread lainnya.

Perulangan produser sebanyak 30 kali. Konsumen-1, Konsumen-2, Konsumen-3 akan berulang tepat 10 kali dan masing-masing akan mengonsumsi tepat 10 item.

Mutex Lock digunakan untuk setiap proses.

void *Producer()
{
int produced;
printf("\nProducer created");
printf("\nProducer id is %ld\n",pthread_self());
for(produced=0;produced<30;produced++)
{
sem_wait(&empty);
sem_wait(&sm);
data=produced;
sem_post(&sm);
sem_post(&full);
printf("\nProducer: %d",data);
}
}
void *Consumer(void *no)
{
int consumed, total=0;
int thread = (int)no;
printf("\nConsumer created, Thread number: %d\n", *thread);
printf("\nConsumer id is %ld\n",pthread_self());
for(consumed=0;consumed<10;consumed++)
{
sem_wait(&full);
sem_wait(&sm);
total=total+data;
printf("\nThread: %d, Consumed: %d", *thread, data);
sem_post(&sm);
sem_post(&empty);
}
printf("\nThe total of 10 iterations for thread %d is %d\n",*thread, total);
}

//Output tested on: https://www.onlinegdb.com/online_bash_shell
Consumer created, Thread number: 3
Consumer id is 140167270151936
Consumer created, Thread number: 1
Consumer id is 140167286937344
Producer created
Producer id is 140167295330048
Producer: 0
Thread: 3, Consumed: 0
Producer: 1
Thread: 1, Consumed: 1
Producer: 2
Thread: 3, Consumed: 2
Producer: 3
Thread: 1, Consumed: 3
Producer: 4
Thread: 3, Consumed: 4
Producer: 5
Thread: 1, Consumed: 5
Producer: 6
Thread: 3, Consumed: 6
Producer: 7
Thread: 1, Consumed: 7
Producer: 8
Thread: 3, Consumed: 8
Producer: 9
Thread: 1, Consumed: 9
Producer: 10
Thread: 3, Consumed: 10
Producer: 11
Thread: 1, Consumed: 11
Producer: 12
Thread: 3, Consumed: 12
Producer: 13
Thread: 1, Consumed: 13
Producer: 14
Thread: 3, Consumed: 14
Producer: 15
Thread: 1, Consumed: 15
Producer: 16
Thread: 3, Consumed: 16
Producer: 17
Thread: 1, Consumed: 17
Producer: 18
Thread: 3, Consumed: 18
The total of 10 iterations for thread 3 is 90
Producer: 19
Thread: 1, Consumed: 19
The total of 10 iterations for thread 1 is 100
Producer: 20
Consumer created, Thread number: 2
Consumer id is 140167278544640
Thread: 2, Consumed: 20
Producer: 21
Thread: 2, Consumed: 21
Producer: 22
Thread: 2, Consumed: 22
Producer: 23
Thread: 2, Consumed: 23
Producer: 24
Thread: 2, Consumed: 24
Producer: 25
Thread: 2, Consumed: 25
Producer: 26
Thread: 2, Consumed: 26
Producer: 27
Thread: 2, Consumed: 27
Producer: 28
Thread: 2, Consumed: 28
Producer: 29
Thread: 2, Consumed: 29
The total of 10 iterations for thread 2 is 245
Main done

“Implementasikan konsep yang baru kami pelajari untuk mengimprovisasi BAKERY kami untuk ‘n’ Konsumen dan 1 Produser. Pastikan itu tersinkronisasi dengan baik.”



