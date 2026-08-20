# Longdaycat.Co (Point of Sale & Inventory System)

Selamat datang di repositori **Longdaycat.Co**. Aplikasi ini adalah sistem **Point of Sale (POS)** dan **Manajemen Stok/Inventaris** berbasis web modern. Aplikasi ini dirancang untuk memudahkan proses transaksi kasir, pelacakan stok barang, hingga pembuatan laporan penjualan.

## 🚀 Fitur Utama

- **Point of Sale (POS)**: Antarmuka kasir yang interaktif untuk memproses transaksi dengan cepat.
- **Manajemen Produk & Kategori**: Mengelola data barang, harga, dan kategori produk.
- **Manajemen Stok (Inventory)**: Pelacakan keluar masuknya barang dan ketersediaan stok.
- **Rekomendasi Restok**: Sistem cerdas yang secara otomatis memberikan notifikasi dan saran pengisian ulang ketika stok barang sudah menipis.
- **Pemindai Barcode/QR Code**: Terintegrasi dengan fitur scan barcode & QR code (menggunakan kamera/scanner) untuk pencarian barang.
- **Laporan Penjualan (Reports)**: Laporan transaksi yang dilengkapi dengan grafik visual (Chart.js) dan bisa di-export ke dokumen (Word/DOCX).
- **Manajemen Pengguna (Users)**: Hak akses untuk pengguna/karyawan.
- **PWA (Progressive Web App)**: Aplikasi dapat diinstal di perangkat (Mobile/Desktop) dan bekerja lebih optimal layaknya aplikasi native.

## 🛠️ Teknologi yang Digunakan

Aplikasi ini menggunakan stack teknologi terkini (TALL/VILT stack variant):

- **Backend**: Laravel 11 (PHP)
- **Frontend**: Vue.js 3 + Inertia.js
- **Styling**: Tailwind CSS
- **Bundler**: Vite
- **Integrasi PWA**: `vite-plugin-pwa`
- **Lain-lain**: 
  - `chart.js` & `vue-chartjs` (Untuk grafik analitik)
  - `html5-qrcode` & `jsbarcode` (Pemindai dan pembuat barcode)
  - `docx` & `file-saver` (Export laporan ke dokumen)

## 🗄️ Struktur Data (Database)

Sistem ini menggunakan beberapa tabel relasional utama untuk mendukung operasional Point of Sale dan Inventaris, di antaranya:

- **`users`**: Data pengguna, kasir, pengelola, beserta peran/hak aksesnya.
- **`kategoris`**: Kategori untuk pengelompokan produk.
- **`produks`**: Data master barang, harga jual/beli, stok, dan barcode/QR code.
- **`transaksis` & `detail_transaksis`**: Mencatat informasi struk pesanan dan rincian barang yang terjual.
- **`pembayarans`**: Data informasi dan metode pembayaran pelanggan.
- **`manajemen_stoks`**: Melacak riwayat pergerakan stok (barang masuk/keluar/retur).
- **`rekomendasi_stoks`**: Data rekomendasi cerdas dari sistem untuk pengisian ulang stok yang mulai menipis.
- **`log_transaksis` & `activity_logs`**: Merekam jejak audit serta log aktivitas pengguna secara real-time.
- **`settings`**: Pengaturan konfigurasi aplikasi dan profil toko.
- **`notifications` & `push_subscriptions`**: Data pengelolaan push notification untuk aplikasi PWA.

## 📈 Implementasi Single Moving Average (SMA)

Sistem rekomendasi restok (pengisian ulang stok barang) pada aplikasi ini ditenagai oleh metode **Single Moving Average (SMA)**. Algoritma peramalan (*forecasting*) ini memprediksi kebutuhan stok di periode mendatang dengan cara menghitung nilai rata-rata penjualan dari beberapa periode waktu sebelumnya (historis). 

- Proses kalkulasi algoritma SMA ini dilakukan secara dinamis melalui `StockRecommendationController`.
- **Tujuan**: Mencegah terjadinya *Overstock* (kelebihan stok) atau *Stockout* (kehabisan stok), sehingga manajemen inventaris menjadi lebih efisien berdasarkan tren penjualan aktual.

## 📂 Struktur Folder Utama

Aplikasi ini mengadaptasi arsitektur monolith modern dengan integrasi Laravel dan Inertia.js. Berikut adalah direktori utama proyek:

- `app/` : Berisi logika utama *backend* PHP (Models, Controllers, Middleware, dll).
  - `app/Http/Controllers/` : Tempat berjalannya logika bisnis aplikasi (seperti POS, Inventaris, dan kalkulasi SMA).
- `database/` : Berisi *database migrations* dan *seeder*.
- `resources/` :
  - `resources/js/` : Kumpulan kode *frontend* Vue.js 3 dan komponen antarmuka.
  - `resources/js/Pages/` : *View* halaman (seperti Dashboard, POS, Products, Reports, Settings).
- `public/` : Aset statis yang dapat diakses publik, *manifest* PWA, dan file hasil *build* dari Vite.
- `routes/` : Pengaturan rute URL (berkas utama: `web.php`).

## ⚙️ Panduan Instalasi (Development)

Berikut adalah langkah-langkah untuk menjalankan Longdaycat.Co di perangkat lokal Anda:

1. **Clone repositori ini**:
   ```bash
   git clone https://github.com/TRPL-JBI/TA2026-362155401070-Aidika-Akbar-Assufa.git
   cd TA2026-362155401070-Aidika-Akbar-Assufa
   ```

2. **Instalasi Dependensi PHP (Composer)**:
   ```bash
   composer install
   ```

3. **Instalasi Dependensi Node.js**:
   ```bash
   npm install
   ```

4. **Konfigurasi Environment**:
   Salin file `.env.example` ke `.env`, kemudian sesuaikan pengaturan koneksi database Anda:
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

5. **Jalankan Migrasi Database & Seeder**:
   ```bash
   php artisan migrate --seed
   ```

6. **Jalankan Server Lokal**:
   Jalankan perintah ini menggunakan 2 terminal yang berbeda (atau gunakan command yang sudah disatukan jika tersedia):
   ```bash
   php artisan serve
   ```
   dan
   ```bash
   npm run dev
   ```

Aplikasi sekarang dapat diakses melalui `http://localhost:8000`.

## 👥 Kontributor
- **Aidika Akbar Assufa** (362155401070)

## 📄 Lisensi
Proyek ini bersifat *Open Source* dan dilisensikan di bawah [MIT License](https://opensource.org/licenses/MIT).
