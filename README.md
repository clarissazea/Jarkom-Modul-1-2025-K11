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

<img width="822" height="315" alt="image" src="https://github.com/user-attachments/assets/7ceeb8a8-bfc1-4759-93ac-57d3587395b2" />

b.) Nama file pertama yang mengandung malware/mencurigakan: `d0p2nc6ka3f_fixhohlycj4ovqfcy_smchzo_ub83urjpphrwahjwhv_o5c0fvf6.exe`
<img width="1103" height="126" alt="image" src="https://github.com/user-attachments/assets/b8e855cd-5ba5-4c4c-ae2f-7c9bbd13b685" />

c.) Nama file kedua yang mengandung malware/mencurigakan: `oiku9bu68cxqenfmcsos2aek6t07_guuisgxhllixv8dx2eemqddnhyh46l8n_di.exe`
<img width="1158" height="113" alt="image" src="https://github.com/user-attachments/assets/51aa51e8-685c-4706-a3b6-0cf7f03c4e2b" />

d.) Hash dari file pertama:

`59896ae5f3edcb999243c7bfdc0b17eb7fe28f3a66259d797386ea470c010040`
<img width="1898" height="481" alt="image" src="https://github.com/user-attachments/assets/29df5cd9-5a6e-4f36-8d2b-801c0e0985e7" />

e.) Hash dari file kedua:

`cf99990bee6c378cbf56239b3cc88276eec348d82740f84e9d5c343751f82560`
<img width="1893" height="286" alt="image" src="https://github.com/user-attachments/assets/d312fa62-195c-4450-8ab8-55d2c6cdf399" />

Hasil pertanyaan diatas menghasilkan sebuah flag seperti gambar dibawah:

<img width="1463" height="848" alt="image" src="https://github.com/user-attachments/assets/64f08cde-f73b-4603-a518-a938c34fad01" />


19.) Manwe mengirimkan email berisi surat cinta kepada Varda melalui koneksi yang tidak terenkripsi. Melihat hal itu Melkor sipaling jahat langsung melancarkan aksinya yaitu meneror Varda dengan email yang disamarkan. Analisis file capture jaringan dan gagalkan lagi rencana busuk Melkor.
	(link file) nc 10.15.43.32 3406

a.) Siapa yang mengirimkan pesan ancaman?
`Your Life`

Step pertama mencari paket dengan protocol `TCP`.

<img width="1919" height="632" alt="image" src="https://github.com/user-attachments/assets/271571e7-8f45-4631-b0a5-2a06b152b5dc" />

Ketika difollow, muncul identitas pengirim dan isi pesan yang dikirimkan. 
```
MAIL FROM: <YourLife36@7162.com>
RCPT TO: <ikwlngpoh@yahoo.com>
```

<img width="1357" height="738" alt="image" src="https://github.com/user-attachments/assets/9b16f72a-cce2-4f40-ac41-2a6051dd8df4" />

Isi pesan yang dikirimkan oleh user `Your Life` mengandung ancaman. Pesan menyebutkan bahwa pengirim telah menginstal malware/RAT di perangkat korban. Disebutkan pula bahwa pengirim mengakses password, webcam, data pribadi, dan video korban. Ada ancaman eksplisit pula, jika korban tidak membayar (biasanya dengan Bitcoin), maka data pribadi dan video akan dipublikasikan ke kontak dan media sosial.

<img width="1919" height="1043" alt="image" src="https://github.com/user-attachments/assets/50828117-4921-4092-9472-450f80e4bcc4" />

b.) Berapa banyak uang tebusan yang diminta attacker?
`1600$`
<img width="1117" height="131" alt="image" src="https://github.com/user-attachments/assets/97330beb-6e39-48b0-b519-2432d277c82a" />

User `Your Life` menuliskan sendiri cara menghentikan serangan/ancaman dengan memberi uang tebusan (bitcoin) sebanyak 1600 dalam waktu 4 hari saja.

c.) Dompet bitcoin milik attacker?
`1CWHmuF8dHt7HBGx5RKKLgg9QA2GmE3UyL`
<img width="756" height="277" alt="image" src="https://github.com/user-attachments/assets/d15a563b-69b5-4c0e-9ac7-a822695cd447" />

User `Your Life` juga mencantumkan dompet bitcoin miliknya untuk pembayaran.

Hasil pertanyaan diatas menghasilkan sebuah flag seperti gambar dibawah:
<img width="1270" height="472" alt="image" src="https://github.com/user-attachments/assets/9a9ebdcd-6379-448d-bed9-9aaba6e99e6c" />


20.) Untuk yang terakhir kalinya, rencana besar Melkor yaitu menanamkan sebuah file berbahaya kemudian menyembunyikannya agar tidak terlihat oleh Eru. Tetapi Manwe yang sudah merasakan adanya niat jahat dari Melkor, ia menyisipkan bantuan untuk mengungkapkan rencana Melkor. Analisis file capture dan identifikasi kegunaan bantuan yang diberikan oleh Manwe untuk menggagalkan rencana jahat Melkor selamanya.
(link file) nc 10.15.43.32 3407

a.) Metode enkripsi apa yang digunakan? 

Jawaban: `TLS`
Trafik di dalam `MelkorPlan5` tidak berjalan sebagai teks biasa (cleartext) seperti `SMTP/HTTP` sebelumnya, tetapi melalui protokol terenkripsi (bukan MAIL FROM/DATA atau HTTP/1.1 GET yang bisa dibaca). Dari pola port yang digunakan dan payload yang tidak dapat dibaca langsung, dapat dipastikan bahwa metode enkripsi yang dipakai adalah:
<img width="603" height="333" alt="image" src="https://github.com/user-attachments/assets/b375a170-25d6-439c-a542-8d2941bd632c" />


b.) Apa nama file berbahaya yang ditempatkan oleh penyerang?: ` invest_20.dll`

Step pertama, buka `File` lalu export object untuk `HTTP`
<img width="1539" height="979" alt="image" src="https://github.com/user-attachments/assets/649ef7aa-7136-411b-b85d-76d5cb285e55" />

<img width="1234" height="888" alt="image" src="https://github.com/user-attachments/assets/76240094-4e80-4797-b7df-d22b99ff2a0f" />

Hasil yang ditampilkan kosong, artinya protokol TLS harus memasukkan password terlebih dahulu. (TLS adalah protokol yang menyediakan confidentiality (enkripsi), integrity dan authentication.)

Sehingga, kita bisa memasukkan file `keyslogfile` yang berada dalam folder `MelkorPlan5`. Dengan cara tekan menu `Edit` ---> `Preferences` ---> Pilih `protocol` lalu `TLS`.

<img width="427" height="579" alt="image" src="https://github.com/user-attachments/assets/272871f0-8bbd-4b34-a0c1-59611fb149fd" />

Masukkan file `keyslogfile` lalu `OK`

<img width="1137" height="623" alt="image" src="https://github.com/user-attachments/assets/f99ec0a6-3864-44c6-8296-3cb8e4567b6d" />

Kemudian, kembali ke export object `HTTP` dan mencari file berbahaya tersebut
<img width="1919" height="595" alt="image" src="https://github.com/user-attachments/assets/d5d7ce01-ab1b-4c9b-b894-66833528db5c" />

Terdapat beberapa file dan setelah beberapa percobaan, file yang berbahaya (mengandung malware) adalah file ` invest_20.dll`
<img width="1919" height="451" alt="image" src="https://github.com/user-attachments/assets/13eef271-c785-4e04-9e84-48f9c8e058c2" />


c.) Hash dari file yang mengandung malware (` invest_20.dll`) menggunakan `sha256`

<img width="1696" height="460" alt="image" src="https://github.com/user-attachments/assets/77122a12-edfe-4f7f-b162-af8b331869e9" />

Hasil pertanyaan diatas menghasilkan sebuah flag seperti gambar dibawah:

<img width="1919" height="924" alt="image" src="https://github.com/user-attachments/assets/004f7085-84f2-4862-800c-6e4d2da36722" />


