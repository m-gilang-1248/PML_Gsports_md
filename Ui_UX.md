Tentu, mari kita lanjutkan dengan membuat dokumen UI/UX.

Dokumen ini akan berfungsi sebagai jembatan antara PRD (apa yang kita bangun) dan tim desain/pengembangan (bagaimana tampilannya dan rasanya). Ini akan menguraikan prinsip-prinsip desain, panduan visual, dan wireframe konseptual untuk setiap alur pengguna baru.

---

# **UI/UX Design Guidelines: Gsports v2.0**

| **Status Dokumen** | Draft                                        |
| ------------------ | -------------------------------------------- |
| **Versi Dokumen**  | 1.0                                          |
| **Tanggal**        | 5 November 2025                              |
| **Penyusun**       | Ahmad Rois (221240001239)<br>M. Gilang M.W. Sabdokafi (221240001248)
---
*   **Nama Produk:** Gsports
*   **Tanggal:** 5 November 2025
*   **Tujuan:** Dokumen ini memberikan panduan dan spesifikasi desain antarmuka (UI) dan pengalaman pengguna (UX) untuk pengembangan Gsports v2.0. Tujuannya adalah memastikan konsistensi, kemudahan penggunaan, dan pengalaman yang menyenangkan di seluruh fitur baru.



## **1. Filosofi & Prinsip Desain**

Desain Gsports v2.0 harus berpegang pada empat prinsip utama:

1.  **Kecepatan & Efisiensi (Speed & Efficiency):** Pengguna harus dapat menyelesaikan tugas utama (menemukan lapangan, memesan, mencatat skor) dengan jumlah langkah dan waktu sesingkat mungkin. Alur harus terasa cepat dan responsif.
2.  **Kejelasan & Intuitif (Clarity & Intuitive Design):** Antarmuka harus bersih, tidak berantakan, dan mudah dipahami tanpa memerlukan instruksi. Setiap elemen harus memiliki tujuan yang jelas. Gunakan bahasa yang lugas dan ikon yang familiar.
3.  **Memberdayakan, Bukan Memaksa (Empower, Don't Force):** Pengguna harus merasa memegang kendali. Mode Tamu memungkinkan eksplorasi tanpa paksaan. Fitur premium ditawarkan sebagai nilai tambah, bukan sebagai penghalang yang membuat frustrasi.
4.  **Konsistensi Visual (Visual Consistency):** Elemen desain (warna, font, tombol, kartu) harus konsisten di seluruh aplikasi untuk membangun keakraban dan mengurangi beban kognitif pengguna.

## **2. Panduan Gaya Visual (Visual Style Guide) - Konsep**

*   **Palet Warna:**
    *   **Primary (Utama):** Biru Energetik (`#007BFF`) - Digunakan untuk tombol utama (CTA), header aktif, dan elemen interaktif penting. Melambangkan kepercayaan dan sportivitas.
    *   **Secondary (Pendukung):** Abu-abu Gelap (`#343A40`) - Digunakan untuk teks utama dan judul.
    *   **Background (Latar):** Putih (`#FFFFFF`) atau Abu-abu Sangat Terang (`#F8F9FA`) - Untuk memberikan kesan bersih dan lapang.
    *   **Aksen Sukses:** Hijau (`#28A745`) - Digunakan untuk pesan sukses, status "Confirmed", dan status "Available".
    *   **Aksen Peringatan/Error:** Merah (`#DC3545`) - Digunakan untuk pesan error, status "Cancelled", dan notifikasi penting.
*   **Tipografi:**
    *   **Judul (Headings):** `Poppins` (Bold, Semi-Bold) - Memberikan kesan modern, ramah, dan mudah dibaca.
    *   **Teks Isi (Body):** `Roboto` (Regular) - Sangat terbaca di berbagai ukuran layar, standar untuk Android, dan bekerja dengan baik di iOS.
*   **Ikonografi:**
    *   Gunakan set ikon yang konsisten, direkomendasikan **Material Design Icons**. Ikon harus solid, jelas, dan mudah dikenali.
*   **Komponen UI Utama:**
    *   **Tombol (Buttons):** Tombol utama memiliki sudut membulat, bayangan halus (subtle shadow), dan warna solid (Primary). Tombol sekunder memiliki border (outline) atau tanpa latar belakang (text-only).
    *   **Kartu (Cards):** Digunakan untuk menampilkan item list (SC, lapangan, riwayat). Memiliki sudut membulat, border tipis, dan bayangan halus untuk memberikan elevasi.
    *   **Input Fields:** Desain bersih dengan label yang jelas di atasnya. Saat aktif, border akan menggunakan warna Primary.

## **3. Peta Alur & Desain per Layar (Screen Wireframes)**

### **3.1. Alur Pengguna Baru & Mode Tamu**

**Layar 1: Layar Utama (Mode Tamu)**
*   **Header:** Judul "Gsports", Ikon Lonceng (Notifikasi), Ikon "Masuk/Daftar".
*   **Body:**
    *   Search Bar: "Cari kota atau nama sport center".
    *   Grid/List Ikon Olahraga (Futsal, Badminton, dll.).
    *   Section: "Rekomendasi Terdekat" (jika izin lokasi diberikan).
    *   Section: "Promosi" (jika ada).
*   **Navigasi Bawah:**
    *   `Beranda` (Aktif)
    *   `Papan Skor`
    *   `Pemesanan Saya` (Akan mengarahkan ke login jika diklik)
    *   `Profil` (Akan mengarahkan ke login jika diklik)

**Layar 2: Detail Lapangan & Jadwal (Mode Tamu)**
*   **Layout:** Sama seperti v1.1.
*   **CTA Utama:** Tombol "Pesan Sekarang" yang menonjol di bagian bawah.
*   **Interaksi:** Menekan "Pesan Sekarang" akan memunculkan **Dialog/Bottom Sheet "Masuk untuk Melanjutkan"** dengan opsi "Masuk" dan "Daftar Sekarang".

---
### **3.2. Alur Pemesanan Patungan**

**Layar 3: Ringkasan Pemesanan**
*   **Header:** "Konfirmasi Pemesanan".
*   **Body:**
    *   Detail Lapangan (Nama, Alamat, Tanggal, Waktu).
    *   **Checkbox:** `[ ] Ajak Teman (Booking Patungan)`.
    *   **Section Rincian Biaya (Sangat Penting):**
        *   `Harga Sewa Lapangan`: `Rp 150.000`
        *   `Biaya Layanan`: `Rp 7.500` (terdapat ikon `?` di sebelahnya yang menjelaskan fungsi biaya ini saat ditekan).
        *   `-------------------------` (Garis pemisah)
        *   **`Total Pembayaran`**: **`Rp 157.500`**
*   **CTA Bawah:** Tombol "Lanjutkan Pembayaran".

**Layar 4: Detail Pemesanan (Setelah Bayar - Booking Patungan)**
*   **Header:** "Detail Pemesanan".
*   **Body:**
    *   Informasi booking seperti biasa (status `Confirmed`, kode booking, dll).
    *   **Section Baru: "Peserta"**
        *   List nama-nama peserta. Awalnya hanya berisi nama Host.
        *   Contoh: `1. Rian (Host)`, `2. (Slot Kosong)`, `3. (Slot Kosong)`, dst.
    *   **Tombol Utama:** `[+] Undang Peserta`.
*   **Interaksi:** Menekan "Undang Peserta" memunculkan **Dialog "Bagikan Undangan"** dengan teks penjelasan singkat dan tombol "Salin Tautan".
*   **Feedback:** Setelah menekan "Salin Tautan", muncul toast/snackbar "Tautan berhasil disalin ke clipboard!".

**Layar 5: Halaman Undangan (Dibuka dari Deep Link)**
*   **Header:** "Anda Diundang!"
*   **Body:**
    *   Kartu besar berisi detail permainan:
        *   `Olahraga`: Badminton
        *   `Lokasi`: GOR Cempaka
        *   `Waktu`: Minggu, 10 Nov 2025, 19:00
        *   `Diundang oleh`: Rian
    *   List avatar/nama peserta yang sudah bergabung.
*   **CTA Utama:** Tombol besar "Ya, Saya Bergabung!".

---
### **3.3. Alur Papan Skor "SEKOR"**

**Layar 6: Papan Skor Interaktif**
*   **Desain:** Mengutamakan area sentuh yang besar.
*   **Layout:**
    *   Bagian Kiri: Area besar untuk Tim/Pemain A. Berisi Nama Tim, Angka Skor (font sangat besar), dan tombol `+` / `-`.
    *   Bagian Tengah: Informasi Pertandingan (Skor Set, Timer, Indikator Babak). Tombol `Jeda`/`Lanjut` dan `Selesai`.
    *   Bagian Kanan: Area besar untuk Tim/Pemain B. Sama seperti bagian kiri.
*   **CTA Bawah (hanya untuk user login):** Tombol "Simpan Hasil Pertandingan".

**Layar 7: Riwayat Pertandingan**
*   **Header:** "Riwayat Pertandingan".
*   **Body:** List vertikal berisi kartu-kartu pertandingan.
    *   **Setiap Kartu Berisi:**
        *   Ikon Olahraga.
        *   `Tim A` **vs** `Tim B`.
        *   Skor Akhir: `21 - 18`.
        *   Tanggal Pertandingan.

---
### **3.4. Alur Monetisasi & Upgrade**

**Interaksi 1: Dialog Kuota Habis**
*   **Pemicu:** Pengguna gratis menekan "Simpan Hasil Pertandingan" saat kuota = 0.
*   **Tipe:** Modal Dialog (menutupi layar, fokus pada pesan).
*   **Judul:** "Kuota Gratis Anda Habis!"
*   **Isi Pesan:** "Anda telah menggunakan 5 dari 5 kuota gratis untuk menyimpan pertandingan. Upgrade ke Premium untuk menyimpan hasil tanpa batas!"
*   **Tombol Aksi:**
    *   **Primer:** "Upgrade ke Premium" (Warna Primary).
    *   **Sekunder:** "Tutup" (Text-only).

**Layar 8: Halaman Informasi Premium**
*   **Desain:** Halaman statis yang menarik secara visual (sales page).
*   **Header:** "Jadilah Anggota Gsports Premium!"
*   **Body:**
    *   Grafis/ilustrasi yang menarik.
    *   **Section Keuntungan (menggunakan ikon checklist):**
        *   `✅ Simpan Skor Tanpa Batas`
        *   `✅ Akses Fitur Eksklusif Mendatang`
        *   `✅ Pengalaman Bebas Iklan (Segera Hadir)`
        *   `✅ Mendukung Pengembangan Gsports`
*   **CTA Utama (Sticky di Bawah):** Tombol "Berlangganan Sekarang - Rp 10.000/bulan" (Harga hanya contoh).

## **4. Interaksi Mikro & Umpan Balik**

*   **Loading States:** Gunakan *skeleton loaders* (kerangka abu-abu yang berkedip) saat memuat daftar SC atau riwayat untuk UX yang lebih baik daripada spinner di tengah layar.
*   **Feedback Aksi:** Setiap aksi penting (booking, bergabung, menyalin tautan, menyimpan hasil) harus memberikan umpan balik visual instan (toast, snackbar, atau perubahan state tombol).
*   **Transisi Halus:** Gunakan animasi transisi yang halus (fade in/out, slide up) antar layar untuk membuat aplikasi terasa lebih profesional dan tidak "patah-patah".

*   **Gestur:** Pertimbangkan gestur "tarik untuk refresh" (pull-to-refresh) pada daftar yang dinamis seperti jadwal atau riwayat.
