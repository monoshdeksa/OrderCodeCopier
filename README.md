# Salin Kode Pesanan (OrderCodeCopier)

Aplikasi utilitas Android (Kotlin + Google ML Kit Text Recognition) dengan **tombol melayang (Floating Bubble)** untuk menangkap tampilan layar pada aplikasi **ShopeeFood Driver**, membaca teks (OCR), mendeteksi baris **nomor pesanan penerima**, dan menyalinnya otomatis ke clipboard.

## Fitur Utama
- **Tombol Melayang 1-Ketuk**: Geser tombol ke posisi mana saja. Ketuk 1x untuk mengambil tangkapan layar, membaca teks dengan ML Kit OCR, dan menyalin kode yang cocok otomatis ke clipboard.
- **Deteksi Fleksibel (Label, Awalan, & Regex Kustom)**:
  - Mendukung label seperti `No. Pesanan Penerima`, `No. Pesanan`, `Order ID`, `Kode Pesanan` (baik kode di baris yang sama maupun tepat di baris bawahnya).
  - Mendukung awalan/prefix seperti `#` atau `SF`, serta opsi menghapus tanda `#` saat menyalin.
  - Mendukung Regex kustom jika format kode unik.
- **Mode Cadangan (Galeri & Share Screenshot)**:
  - Bisa menguji atau menyalin kode dari screenshot galeri maupun lewat fitur **Bagikan (Share)** gambar ke aplikasi ini.
  - Menampilkan semua baris hasil OCR agar bisa diketuk dan disalin manual jika aturan otomatis belum cocok.
- **Deteksi Layar Terproteksi (`FLAG_SECURE`)**: Jika aplikasi sumber memblokir tangkapan layar sehingga gambar menjadi hitam, aplikasi memberi peringatan yang jelas.

## Cara Build APK

### Opsi 1: GitHub Actions (Tanpa Install Android SDK di PC)
1. Publish/push folder `OrderCodeCopier` ini ke repository GitHub baru lewat **GitHub Desktop** atau `git push` (hindari drag-and-drop di browser karena folder tersembunyi `.github` sering tidak ikut ter-upload).
2. Workflow `.github/workflows/build-apk.yml` akan otomatis berjalan (atau jalankan manual lewat tab **Actions → Build Android APK → Run workflow**).
3. Setelah status build centang hijau (✓), unduh APK lewat salah satu cara berikut:
   - **Cara termudah di HP (Releases):** Buka halaman utama repository → ketuk **Releases** → unduh **`OrderCodeCopier-debug.apk`** langsung tanpa ekstrak ZIP. *(Pastikan di Settings → Actions → General → Workflow permissions terpilih "Read and write permissions" jika release belum muncul.)*
   - **Via Actions Artifacts:** **Login ke akun GitHub** di browser HP → buka tab **Actions** → buka run paling atas → scroll ke bawah ke bagian **Artifacts** → ketuk **`OrderCodeCopier-debug-apk`**, lalu ekstrak file `.zip` untuk memasang `app-debug.apk`.

### Opsi 2: Android Studio (Lokal)
1. Buka folder `OrderCodeCopier` di **Android Studio** (dengan JDK 17 & Android SDK Platform 35).
2. Tunggu proses Gradle Sync selesai (Android Studio akan mengunduh Gradle 8.9 otomatis sesuai `gradle-wrapper.properties`).
3. Pilih **Build → Build Bundle(s) / APK(s) → Build APK(s)**.

## Cara Menggunakan di HP Android
1. Buka aplikasi **Salin Kode Pesanan**.
2. Tekan **Aktifkan Tombol Melayang**.
3. Izinkan **Tampil di atas aplikasi lain** (*Display over other apps*), notifikasi (Android 13+), dan konfirmasi **Mulai merekam / tangkap layar**.
4. Buka **ShopeeFood Driver** pada halaman detail pesanan.
5. Ketuk tombol melayang oranye 1x → muncul notifikasi singkat `"Tersalin: ..."` dan nomor pesanan sudah siap di-paste (`Tempel`).
6. Jika hasil belum pas, tekan lama tombol melayang untuk membuka aplikasi dan sesuaikan **Label** atau **Awalan** pada pengaturan pola (atau uji dulu memakai screenshot di menu **Uji / Salin dari Screenshot Galeri**).
