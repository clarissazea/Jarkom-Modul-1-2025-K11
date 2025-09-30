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

- user: n1enna
- password: y4v4nn4_k3m3nt4r1

<img width="1919" height="549" alt="image" src="https://github.com/user-attachments/assets/b652f46c-f447-4d4f-b01a-0f1618ae1add" />

c.) Username dan password tersebut muncul pada stream 41824 (berada di pojok kanan bawah)

<img width="1263" height="815" alt="image" src="https://github.com/user-attachments/assets/745960a9-1f44-46b7-8b0b-1543ebfd76c2" />

d.) Tools yang digunakan untuk brute force adalah `Fuzz Faster U Fool v2.1.0-dev`

`ffuf` dipakai untuk menemukan direktori tersembunyi, file, parameter, atau melakukan brute-force nilai (mis. username/password) dengan mengirim banyak request HTTP paralel menggunakan wordlist/payloads.

<img width="627" height="221" alt="image" src="https://github.com/user-attachments/assets/26d2e8b1-0885-4b00-9647-48be261a244e" />

Hasil pertanyaan diatas menghasilkan sebuah flag seperti gambar dibawah:

<img width="1359" height="706" alt="image" src="https://github.com/user-attachments/assets/838e0357-f75d-48c2-a746-31e3d309bba4" />



15. Melkor menyusup ke ruang server dan memasang keyboard USB berbahaya pada node Manwe. Buka file capture dan identifikasi pesan atau ketikan (keystrokes) yang berhasil dicuri oleh Melkor untuk menemukan password rahasia.
    
(link file) nc 10.15.43.32 3402

16. Melkor semakin murka ia meletakkan file berbahaya di server milik Manwe. Dari file capture yang ada, identifikasi file apa yang diletakkan oleh Melkor.
	(link file) nc 10.15.43.32 3403

a.) Credential yang attacker pakai untuk login adalah 

- USER ind@psg420.com
- PASS {6r_6e#TfT1p
  
<img width="1919" height="594" alt="image" src="https://github.com/user-attachments/assets/04f2a13a-f3cd-4f26-a079-9ad58caf588a" />

- RST (Reset) = sinyal TCP untuk memutus koneksi secara paksa.
- ACK (Acknowledgement) = penanda bahwa sampai titik tertentu data sudah diterima.
Bisa karena attacker atau server menutup koneksi dengan cara tidak normal (misalnya setelah brute force atau upload file berbahaya, langsung putus).

<img width="802" height="514" alt="image" src="https://github.com/user-attachments/assets/6c09ab2b-d14f-4e3e-a411-fb37c935063c" />

b.) File yang ter-suspected untuk berisi malware adalah sebanyak 5 file (q, w, e, r, t)

<img width="724" height="611" alt="image" src="https://github.com/user-attachments/assets/38a6a58c-093e-4bbd-956e-cfb4cd54978a" />

<img width="830" height="660" alt="image" src="https://github.com/user-attachments/assets/9c4334b8-ecb1-493c-9abe-b28ff2c95a82" />

<img width="842" height="329" alt="image" src="https://github.com/user-attachments/assets/8488f651-cbe0-462f-8ae8-c75a622add4b" />

c.) Hash dari file pertama (q.exe) adalah `ca34b0926cdc3242bbfad1c4a0b42cc2750d90db9a272d92cfb6cb7034d2a3bd`

Pertama, kita harus melihat paket dengan protocol FTP-Data dengan size q.exe

<img width="1919" height="642" alt="image" src="https://github.com/user-attachments/assets/6ad8d12e-840a-48af-9d3a-442ce4341647" />

Ketika difollow, akan muncul kode ASCII seperti gambar dibawah

<img width="1283" height="1138" alt="image" src="https://github.com/user-attachments/assets/744488e6-c5e2-4edc-9ee6-13ae689d5ae2" />

Lalu ubah menjadi `Raw` dan simpan di folder `MelkorPlan1`

<img width="1319" height="1121" alt="image" src="https://github.com/user-attachments/assets/2acc331b-ec67-44b5-9371-21dc1ae03568" />

Di terminal, jalankan `sha256sum namafile.txt` untuk menghitung nilai hash SHA‑256 dari sebuah file.

<img width="1537" height="450" alt="image" src="https://github.com/user-attachments/assets/5bf5a18b-63c3-4256-bcb1-d8bb38a34a14" />

d.) w: `08eb941447078ef2c6ad8d91bb2f52256c09657ecd3d5344023edccf7291e9fc` 

<img width="1919" height="627" alt="image" src="https://github.com/user-attachments/assets/5f75fdee-2721-48c1-9124-339ec62cc7d7" />

<img width="1113" height="132" alt="image" src="https://github.com/user-attachments/assets/f8eede30-9cf3-49ab-9726-571bea7ddbd1" />



e.) e: `32e1b3732cd779af1bf7730d0ec8a7a87a084319f6a0870dc7362a15ddbd3199`
<img width="1919" height="784" alt="image" src="https://github.com/user-attachments/assets/11915904-e17b-4306-b973-b9c29075a9e1" />
<img width="1189" height="126" alt="image" src="https://github.com/user-attachments/assets/8281a417-c084-46b0-912c-b6493b26adf2" />



f.) r: `4ebd58007ee933a0a8348aee2922904a7110b7fb6a316b1c7fb2c6677e613884`
<img width="1915" height="747" alt="image" src="https://github.com/user-attachments/assets/bf498645-ea66-4d2f-aa8b-23dd42294385" />

<img width="1135" height="228" alt="image" src="https://github.com/user-attachments/assets/28c4c7af-b78b-4cb2-8ace-b3cddd750ebf" />


g.) t: `10ce4b79180a2ddd924fdc95951d968191af2ee3b7dfc96dd6a5714dbeae613a`
<img width="1919" height="742" alt="image" src="https://github.com/user-attachments/assets/fd17495b-0bea-4bb1-b8f8-0e398e0a60a6" />

<img width="1180" height="120" alt="image" src="https://github.com/user-attachments/assets/4393fc81-3b37-4315-8002-24225c7fbf72" />

Hasil pertanyaan (hasil hash) diatas menghasilkan sebuah flag seperti gambar dibawah:

<img width="1508" height="933" alt="image" src="https://github.com/user-attachments/assets/4cf9aeed-7db1-45c1-8c80-ec38226c2e4a" />

17.)  Manwe membuat halaman web di node-nya yang menampilkan gambar cincin agung. Melkor yang melihat web tersebut merasa iri sehingga ia meletakkan file berbahaya agar web tersebut dapat dianggap menyebarkan malware oleh Eru. Analisis file capture untuk menggagalkan rencana Melkor dan menyelamatkan web Manwe.
(link file) nc 10.15.43.32 3404

a.) Nama file mencurigakan pertama 

Lihat pada file `MelkorPlan2`, dan di bagian export object pilih `HTTP`

<img width="1918" height="821" alt="image" src="https://github.com/user-attachments/assets/035b5d00-46d5-4025-b8bc-6ebbce073587" />

Nama file berada antara 3 file dibawah

<img width="1150" height="269" alt="image" src="https://github.com/user-attachments/assets/6c179e7d-146c-4b55-b628-f9f27371febd" />

<img width="770" height="534" alt="image" src="https://github.com/user-attachments/assets/53d49852-50b3-49c2-b4b0-6cb2cc1a5d12" />

b.) Nama file mencurigarakan kedua

<img width="800" height="109" alt="image" src="https://github.com/user-attachments/assets/2c07cfd7-67bc-4970-a535-f3d4c9f2e887" />


c.) Hash dari `knr.exe` 

`749e161661290e8a2d190b1a66469744127bc25bf46e5d0c6f2e835f4b92db18`
<img width="1896" height="539" alt="image" src="https://github.com/user-attachments/assets/f51dded4-98fb-4ecb-8cd1-424dde78603b" />


Hasil pertanyaan diatas menghasilkan sebuah flag seperti gambar dibawah:

<img width="1509" height="783" alt="image" src="https://github.com/user-attachments/assets/08eb98b6-1458-4fe0-82dc-d120bca75f6d" />







18.) Karena rencana Melkor yang terus gagal, ia akhirnya berhenti sejenak untuk berpikir. Pada saat berpikir ia akhirnya memutuskan untuk membuat rencana jahat lainnya dengan meletakkan file berbahaya lagi tetapi dengan metode yang berbeda. Gagalkan lagi rencana Melkor dengan mengidentifikasi file capture yang disediakan agar dunia tetap aman.
(link file) nc 10.15.43.32 3405

a.) Berapa banyak file yang mengandung malware? `2`

Lihat pada file `MelkorPlan3`, dan di bagian export object pilih `SMB`

<img width="1919" height="852" alt="image" src="https://github.com/user-attachments/assets/99383e7e-e74b-43dd-b456-c206d67f5b92" />

Setelah dibuka, muncul 7 file SMB dan ada beberapa file yang mengandung malware.

<img width="1919" height="550" alt="image" src="https://github.com/user-attachments/assets/a773340b-1c36-4448-be11-2f446168a621" />

`\\WINDOWS\d0p2nc6ka3f.fixh0lhyg4voyfcy_smc2ho_u083urjpphnwlahjwhv_o5c0vf6.exe` : suspicious .exe (nama acak, panjang, indikasi obfuscation).

`\\WINDOWS\oiku9bu68cxqenfmcso2aek6t07_guuisqxlnliv8dx2eemqdnhvhyl46l8n.di.exe` : suspicious .exe (juga nama acak, panjang, tidak wajar).


File .exe dengan nama acak (sangat mencurigakan), karena:
- Lokasi di \WINDOWS\ tapi nama tidak sesuai pola file sistem normal.
- Nama panjang tetapi random string (ciri khas file hasil dropper atau malware)
- Ekstensi .exe → executable, berpotensi berbahaya.


19.) Manwe mengirimkan email berisi surat cinta kepada Varda melalui koneksi yang tidak terenkripsi. Melihat hal itu Melkor sipaling jahat langsung melancarkan aksinya yaitu meneror Varda dengan email yang disamarkan. Analisis file capture jaringan dan gagalkan lagi rencana busuk Melkor.
	(link file) nc 10.15.43.32 3406

20.) Untuk yang terakhir kalinya, rencana besar Melkor yaitu menanamkan sebuah file berbahaya kemudian menyembunyikannya agar tidak terlihat oleh Eru. Tetapi Manwe yang sudah merasakan adanya niat jahat dari Melkor, ia menyisipkan bantuan untuk mengungkapkan rencana Melkor. Analisis file capture dan identifikasi kegunaan bantuan yang diberikan oleh Manwe untuk menggagalkan rencana jahat Melkor selamanya.
(link file) nc 10.15.43.32 3407
