# Deskripsi Umum: Sistem Kontrol & Monitoring Material BSPS

## Apa Itu Aplikasi Ini?

Ini adalah **sistem digital untuk mengawasi penyaluran bantuan rumah** dalam program **BSPS (Bantuan Stimulan Perumahan Swadaya)** — program pemerintah Indonesia yang memberi bantuan material bangunan kepada masyarakat untuk membangun/memperbaiki rumah secara mandiri (bukan dibangun kontraktor, tapi swadaya/gotong royong sendiri).

Aplikasi ini dipakai oleh **TIM 22 MINAHASA** untuk mengawasi penyaluran bantuan di 4 desa: Simbel, Totolan, Tolok, dan Tolok Satu.

**Analogi sederhana:** Bayangkan ini seperti sistem pelacakan paket (seperti aplikasi kurir), tapi untuk material bangunan rumah — siapa menerima apa, berapa banyak, dari toko mana, sudah sampai mana progresnya, dan apakah ada masalah di lapangan.

---

## Siapa yang Memakai Aplikasi Ini?

| Peran | Tugasnya |
|---|---|
| **TFL** (Tenaga Fasilitator Lapangan) | Petugas di lapangan — input data penerima, catat penyaluran material, foto kondisi rumah, lapor temuan/masalah |
| **Korkab** (Koordinator Kabupaten) | Mengawasi semua TFL dan progres seluruh desa dalam wilayahnya |
| **Admin** | Akses penuh — kelola data master, user, dan sistem |
| **Warga/Penerima Bantuan** | Bisa cek status bantuannya sendiri tanpa perlu login, lewat scan QR Code |

---

## Apa yang Bisa Dilakukan Aplikasi Ini?

**1. Mencatat Data Penerima Bantuan**
Nama, NIK, KK, alamat, desa, kelompok, toko penyedia material — semua tersimpan rapi per orang.

**2. Melacak Penyaluran Material**
Setiap kali material dikirim ke penerima, dicatat: jenis material, jumlah, foto sebelum/saat/sesudah, video bukti, dan lokasi GPS pengiriman.

**3. Verifikasi Otomatis Lewat GPS**
Sistem otomatis mengecek apakah lokasi pengiriman material benar-benar dekat dengan rumah penerima. Kalau jaraknya lebih dari 500 meter, sistem otomatis membuat "temuan" (warning) — supaya tidak ada laporan palsu bahwa material sudah terkirim padahal sebenarnya tidak.

**4. Status Otomatis per Penerima**
Setiap penerima otomatis berstatus salah satu dari: belum mulai, sedang proses, selesai, atau ada temuan/masalah — dihitung otomatis dari data distribusi dan temuan, bukan input manual.

**5. Verifikasi Lewat QR Code**
Setiap penerima punya QR Code unik. Siapa pun yang scan bisa lihat status bantuannya secara terbuka — transparansi tanpa harus login.

**6. Bantuan AI (Google Gemini)**
- Membuat ringkasan harian otomatis dalam Bahasa Indonesia
- Chat tanya-jawab seputar data program
- Mendeteksi keanehan/anomali data secara otomatis
- Membaca teks dari foto dokumen (OCR)

**7. Pemetaan**
Lokasi semua penerima bantuan ditampilkan di peta, dengan mode ringan khusus untuk koneksi internet lambat di lapangan.

**8. Pelaporan**
Bisa export data ke Excel dan PDF untuk laporan ke atasan/dinas.

**9. Jejak Audit**
Setiap perubahan data (siapa, kapan, apa yang diubah) tercatat permanen — penting untuk akuntabilitas program bantuan pemerintah.

---

## Bagaimana Aplikasi Ini Dibangun? (Singkat)

- **Tampilan (Frontend):** React + TypeScript — dijalankan di browser HP/laptop TFL
- **Otak Pemrosesan (Backend):** Express.js (Node.js) — menangani semua logika dan validasi data
- **Penyimpanan Data:** File JSON datar (`database.json`) sebagai database utama, dengan Firebase sebagian terhubung untuk fitur sinkronisasi real-time
- **AI:** Google Gemini untuk fitur cerdas (ringkasan, chat, OCR)

---

## Tahap Pengembangan Saat Ini

Berdasarkan audit kode terbaru: struktur dan fitur utamanya **sudah solid dan berfungsi**, tapi masih dalam proses **penyempurnaan** di beberapa area — terutama integrasi penuh dengan Firebase untuk sinkronisasi data real-time antar perangkat, dan beberapa perbaikan keamanan/bug yang sudah kita identifikasi dan perbaiki bersama di percakapan sebelumnya (seperti celah login dan validasi data).
