#  WashOps — Aplikasi Manajemen Pemesanan & Operasional Jasa Laundry

WashOps merupakan sistem mandiri (self-contained product) yang dikembangkan untuk menggantikan pencatatan manual pada UMKM *laundry*. WashOps memisahkan tampilan dan logika antarmuka di sisi perangkat Andorid menggunakan **Kotlin Jetpack Compose** serta pola **MVVM** dan menghubungkan melalui REST API ke **Backend** serta **cloud database Supabase (PostgreSQL)** untuk menyimpan dan mengolah data operasional. System ini juga terhubung secara fungsional dengan aplikasi Whatsapp melalui mekanisme **Android Intent** untuk mendukung pengiriman struk digital serta notifikasi selesai dan  layanan antar.


## Progres Proyek

- [x] **Bab 1 — Introduction**
       *1.1 : Menetapkan tujuan dokumen SRS sebagai acuan pengembangan sistem kasir dan operasional UMKM laundry WashOps*
       *1.2 : Menentukan standar penulisan kebutuhan fungsional, kebutuhan kinerja, serta Penekanan istilah teknis dalam dokumen*
       *1.3 : Menganalisa target pembaca dokumentasi beserta uturan pembacaan dokumentasi tiap bab*
       *1.4 : Mengidentifikasi batasan ruang lingkup WashOps sebagai aplikasi Android self-contained untuk pencatatan pesanan, perhitungan biaya otomatis, pelacakan status cucian, rekap pembayaran, dan pengiriman nota/notifikasi via WhatsApp*
       *1.5 : Mencantumkan referensi standar penyusunan SRS serta dokumentasi teknis pendukung (Android Jetpack Compose, Supabase, dan Android Intent)*
- [x] **Bab 2 — Overall Description** 
       *2.1 : Menjelaskan arsitektur yang menghubungkan aplikasi mobile Android (MVVM) dengan REST API Backend dan cloud database Supabase (PostgreSQL)*
       *2.2 : Merangkum enam fungsi utama sistem (Autentikasi Kasir, Katalog Layanan, Data Pelanggan, Pencatatan & Pelacakan Pesanan, Pembayaran & Rekapitulasi, serta Struk Digital & Automasi WhatsApp)*
       *2.3 : Menetapkan model pengguna tunggal yaitu **Staf Kasir / Admin**, beserta karakteristik kebutuhan operasionalnya di meja kasir*
       *2.4 : Menentukan spesifikasi lingkungan operasi perangkat lunak dan perangkat keras (perangkat Android minimal Android 8.0, koneksi internet aktif, dan aplikasi WhatsApp terpasang)*
       *2.5 : Mengidentifikasi batasan teknis sistem, antara lain tidak menggunakan WhatsApp Business API berbayar (Android Intent) dan tidak menyimpan database lokal (Room DB)*
       *2.6 : Merencanakan dokumentasi pendukung penggunaan aplikasi seperti panduan operasional kasir dan `README.md` repositori*
       *2.7 : Menjelaskan ketergantungan eksternal, seperti ketersediaan jaringan internet saat transaksi, layanan Supabase aktif, serta izin penyimpanan internal untuk pembuatan berkas struk*
- [x] **Bab 3 — System Features**
      *Spesifikasi Kebutuhan Fungsional (`FR-01` – `FR-32`):** Menjabarkan *stimulus/response sequences* dan kebutuhan fungsional lengkap untuk 6 fitur utama
      (Autentikasi Kasir, Manajemen Katalog Layanan, Manajemen Data Pelanggan, Pencatatan & Pelacakan Pesanan, Pembayaran & Rekapitulasi Keuangan, serta Struk
      Digital & Automasi WhatsApp).
      *Pemodelan Alur Proses: Menyusun Activity Diagram (dengan swimlane `Kasir`, `Aplikasi WashOps`, `Supabase`) serta Flowchart untuk setiap fitur*
      *Perancangan Basis Data: Merancang Entity Relationship Diagram (ERD) dan skema tabel relasional (RAT) pada PostgreSQL Supabase*

- [x] **Bab 4 — External Interface Requirements**
      *4.1 : Merancang spesifikasi antarmuka pengguna mobile berbasis Kotlin Jetpack Compose (halaman Login/Registrasi, Beranda, Katalog Layanan, Data Pelanggan, Form & Detail Pesanan, serta Rekapitulasi Keuangan)*
      *4.2 : Menentukan kebutuhan antarmuka perangkat keras smartphone Android (layar sentuh, koneksi jaringan internet, dan media penyimpanan internal untuk berkas struk)*
      *4.3 : Mendefinisikan integrasi perangkat lunak dengan REST API Backend (Node.js/Express), Supabase (Auth JWT & PostgreSQL), serta aplikasi WhatsApp via *Android Intent* (`wa.me` dan `FileProvider`)*
      *4.4 : Menetapkan protokol komunikasi HTTP/HTTPS dengan pertukaran data format JSON serta otorisasi *Bearer Token* (JWT)*
- [ ] **Bab 5 — Other Nonfunctional Requirements**

- [ ] **Bab 6 — Other Requirements**

## Fitur Utama

1. **Autentikasi Staf Kasir**
   Registrasi akun, login dengan token JWT dari Supabase Auth, serta manajemen sesi logout.
2. **Manajemen Katalog Layanan**
   Tambah, ubah, cari, dan hapus jenis layanan laundry beserta tarif dan satuan hitung (per kilogram).
3. **Manajemen Data Pelanggan**
   Simpan, cari, dan perbarui data pelanggan (nama, nomor WhatsApp, dan alamat) untuk transaksi berikutnya.
4. **Pencatatan & Pelacakan Pesanan**
   Pembuatan nomor nota otomatis, hitung total biaya (`harga/kg × berat`), pilihan ambil sendiri atau layanan antar, serta pembaruan status cucian (*Antre → Diproses → Sedang Diantar → Selesai*).
5. **Pembayaran & Rekapitulasi Keuangan**
   Pencatatan status pelunasan beserta waktu bayar, dan tampilan rekapitulasi total pendapatan.
6. **Struk Digital & Automasi WhatsApp**
   Pembuatan berkas struk ke penyimpanan internal perangkat serta pengiriman pesan status dan lampiran struk ke WhatsApp pelanggan via *Android Intent* dan `FileProvider`.
