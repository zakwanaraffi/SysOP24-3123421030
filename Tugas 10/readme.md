## Chapter

Threads

Practice Exercises

*4.1 Provide three programming examples in which multithreading provides better performance than a single-threaded solution.*

Answer:
a. A Web server that services each request in a separate thread.
b. A parallelized application such as matrix multiplication where different parts of the matrix may be worked on in parallel.
c. An interactive GUI program such as a debugger where a thread is used to monitor user input, another thread represents the running application, and a third thread monitors performance.

4.2 What are two differences between user-level threads and kernel-level threads? Under what circumstances is one type better than the other?

Answer:
a. User-level threads are unknown by the kernel, whereas the kernel is aware of kernel threads.
b. On systems using either M:1 or M:N mapping, user threads are scheduled by the thread library and the kernel schedules kernel threads.
c. Kernel threads need not be associated with a process whereas every user thread belongs to a process. Kernel threads are generally more expensive to maintain than user threads as they must be represented with a kernel data structure.

4.3 Describe the actions taken by a kernel to context-switch between kernel-level threads.

Answer:
Context switching between kernel threads typically requires saving the value of the CPU registers from the thread being switched out and restoring the CPU registers of the new thread being scheduled.

4.4 What resources are used when a thread is created? How do they differ from those used when a process is created?

Answer:
Because a thread is smaller than a process, thread creation typically uses fewer resources than process creation. Creating a process requires allocating a process control block (PCB), a rather large data structure. The PCB includes a memory map, list of open files, and environment variables. Allocating and managing the memory map is typically the most time-consuming activity. Creating either a user or kernel thread involves allocating a small data structure to hold a register set, stack, and priority.

4.5 Assume that an operating system maps user-level threads to the kernel using the many-to-many model and that the mapping is done through LWPs. Furthermore, the system allows developers to create real-time threads for use in real-time systems. Is it necessary to bind a real-time thread to an LWP? Explain.

Answer:
Yes. Timing is crucial to real-time applications. If a thread is marked as real-time but is not bound to an LWP, the thread may have to wait to be attached to an LWP before running. Consider if a real-time thread is running (is attached to an LWP) and then proceeds to block (i.e. must perform I/O, has been preempted by a higher-priority real-time thread, is waiting for a mutual exclusion lock, etc.) While the real-time thread is blocked, the LWP it was attached to has been assigned to another thread. When the real-time thread has been scheduled to run again, it must first wait to be attached to an LWP. By binding an LWP to a real-time thread you are ensuring the thread will be able to run with minimal delay once it is scheduled.

## Translate 

Latihan

4.1 Berikan tiga contoh pemrograman di mana multithreading memberikan kinerja yang lebih baik daripada solusi single-threaded.

Menjawab:
a. Server Web yang melayani setiap permintaan dalam thread terpisah.
b. Aplikasi yang diparalelkan seperti perkalian matriks di mana bagian-bagian matriks yang berbeda dapat dikerjakan secara paralel.
c. Sebuah program GUI interaktif seperti debugger dimana thread digunakan untuk memonitor input pengguna, thread lain mewakili aplikasi yang sedang berjalan, dan thread ketiga memonitor kinerja.

4.2 Apa dua perbedaan antara thread tingkat pengguna dan thread tingkat kernel? Dalam kondisi apa satu jenis lebih baik dibandingkan jenis lainnya?

Menjawab:
a. Thread tingkat pengguna tidak diketahui oleh kernel, sedangkan kernel mengetahui thread kernel.
b. Pada sistem yang menggunakan pemetaan M:1 atau M:N, thread pengguna dijadwalkan oleh pustaka thread dan kernel menjadwalkan thread kernel.
c. Kernelthread tidak perlu dikaitkan dengan suatu proses, sedangkan setiap thread pengguna termasuk dalam suatu proses. Pemeliharaan thread kernel umumnya lebih mahal daripada thread pengguna karena harus direpresentasikan dengan struktur data kernel.

4.3 Jelaskan tindakan yang diambil oleh kernel untuk beralih konteks antar thread tingkat kernel.

Menjawab:
Peralihan konteks antar thread kernel biasanya memerlukan penyimpanan nilai register CPU dari thread yang dialihkan dan memulihkan register CPU dari thread baru yang dijadwalkan.

4.4 Sumber daya apa yang digunakan saat thread dibuat? Apa perbedaannya dengan yang digunakan saat proses dibuat?

Menjawab:
Karena thread lebih kecil dari proses, pembuatan thread biasanya menggunakan lebih sedikit sumber daya dibandingkan pembuatan proses. Membuat suatu proses memerlukan alokasi blok kontrol proses (PCB), sebuah struktur data yang agak besar. PCB mencakup peta memori, daftar file yang terbuka, dan variabel lingkungan. Mengalokasikan dan mengelola peta memori biasanya merupakan aktivitas yang paling memakan waktu. Membuat thread pengguna atau kernel melibatkan pengalokasian struktur data kecil untuk menampung set register, tumpukan, dan prioritas.

4.5 Asumsikan bahwa sistem operasi memetakan thread tingkat pengguna ke kernel menggunakan model banyak ke banyak dan pemetaan dilakukan melalui LWP. Selain itu, sistem ini memungkinkan pengembang membuat thread real-time untuk digunakan dalam sistem real-time. Apakah perlu untuk mengikat thread real-time ke LWP? Menjelaskan.

Menjawab:
Ya. Pengaturan waktu sangat penting untuk aplikasi real-time. Jika thread ditandai sebagai real-time namun tidak terikat ke LWP, thread mungkin harus menunggu untuk dipasang ke LWP sebelum dijalankan. Pertimbangkan apakah thread real-time sedang berjalan (terpasang ke LWP) dan kemudian melanjutkan ke pemblokiran (yaitu harus melakukan I/O, telah didahului oleh thread real-time dengan prioritas lebih tinggi, sedang menunggu kunci pengecualian bersama, dll.) Saat thread real-time diblokir, LWP yang dilampirkannya telah ditetapkan ke thread lain. Ketika thread real-time telah dijadwalkan untuk dijalankan kembali, thread tersebut harus menunggu terlebih dahulu untuk dilampirkan ke LWP. Dengan mengikat LWP ke thread real-time, Anda memastikan thread akan dapat berjalan dengan penundaan minimal setelah dijadwalkan.
