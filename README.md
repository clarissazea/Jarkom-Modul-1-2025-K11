# Jarkom-Modul-1-2025-K11

14. Setelah gagal mengakses FTP, Melkor melancarkan serangan brute force terhadap  Manwe. Analisis file capture yang disediakan dan identifikasi upaya brute force Melkor.
    
(link file) nc 10.15.43.32 3401

a.) Jumlah seluruh paket dalam shortbf adalah 500358
<img width="1919" height="1130" alt="image" src="https://github.com/user-attachments/assets/90f89427-1805-4ca8-ad4c-e8f7afcc6c3e" />

b.) User yang login dengan sukses bisa kita cari dengan memfilter paket `http`. Kemudian kita membaca paket dengan metode `POST /login` satu-persatu yang memiliki info login success. 
<img width="1919" height="500" alt="image" src="https://github.com/user-attachments/assets/ebf54794-46ad-4e2d-b074-121075a78faa" />

Setelah kita lihat (follow http stream), paket login selalu `Invalid credentials` atau gagal, seperti gambar dibawah:

<img width="1041" height="572" alt="image" src="https://github.com/user-attachments/assets/b94a3bfd-1d6d-43f0-b82f-1fbac6c47d49" />


Sehingga, untuk mencari user yang bisa login dengan sukses (diantara 500358 paket), bisa kita identifikasi percobaan login yang benar berada di bawah (akhir paket) setelah banyak upaya gagal diatasnya. 

<img width="982" height="544" alt="image" src="https://github.com/user-attachments/assets/b13d26cb-a12d-4841-b0ff-24d9affcd8fa" />
Sehingga ketemu,
user: n1enna
password: y4v4nn4_k3m3nt4r1

<img width="1919" height="549" alt="image" src="https://github.com/user-attachments/assets/b652f46c-f447-4d4f-b01a-0f1618ae1add" />



16. Melkor menyusup ke ruang server dan memasang keyboard USB berbahaya pada node Manwe. Buka file capture dan identifikasi pesan atau ketikan (keystrokes) yang berhasil dicuri oleh Melkor untuk menemukan password rahasia.
(link file) nc 10.15.43.32 3402

17. Melkor semakin murka ia meletakkan file berbahaya di server milik Manwe. Dari file capture yang ada, identifikasi file apa yang diletakkan oleh Melkor.
	(link file) nc 10.15.43.32 3403

18. Manwe membuat halaman web di node-nya yang menampilkan gambar cincin agung. Melkor yang melihat web tersebut merasa iri sehingga ia meletakkan file berbahaya agar web tersebut dapat dianggap menyebarkan malware oleh Eru. Analisis file capture untuk menggagalkan rencana Melkor dan menyelamatkan web Manwe.
(link file) nc 10.15.43.32 3404

19. Karena rencana Melkor yang terus gagal, ia akhirnya berhenti sejenak untuk berpikir. Pada saat berpikir ia akhirnya memutuskan untuk membuat rencana jahat lainnya dengan meletakkan file berbahaya lagi tetapi dengan metode yang berbeda. Gagalkan lagi rencana Melkor dengan mengidentifikasi file capture yang disediakan agar dunia tetap aman.
(link file) nc 10.15.43.32 3405

20. Manwe mengirimkan email berisi surat cinta kepada Varda melalui koneksi yang tidak terenkripsi. Melihat hal itu Melkor sipaling jahat langsung melancarkan aksinya yaitu meneror Varda dengan email yang disamarkan. Analisis file capture jaringan dan gagalkan lagi rencana busuk Melkor.
	(link file) nc 10.15.43.32 3406

21. Untuk yang terakhir kalinya, rencana besar Melkor yaitu menanamkan sebuah file berbahaya kemudian menyembunyikannya agar tidak terlihat oleh Eru. Tetapi Manwe yang sudah merasakan adanya niat jahat dari Melkor, ia menyisipkan bantuan untuk mengungkapkan rencana Melkor. Analisis file capture dan identifikasi kegunaan bantuan yang diberikan oleh Manwe untuk menggagalkan rencana jahat Melkor selamanya.
(link file) nc 10.15.43.32 3407
