# **Rencana Sprint & Iterasi: Gsports v1.0**


| **Status Dokumen** | Draft                                        |
| ------------------ | -------------------------------------------- |
| **Versi Dokumen**  | 1.0                                          |
| **Tanggal**        | 5 November 2025                              |
| **Penyusun**       | Ahmad Rois (221240001239)<br>M. Gilang M.W. Sabd
---
*   **Nama Proyek:** Gsports v1.0
*   **Tujuan:** Dokumen ini memecah lingkup pengembangan Gsports v2.0 menjadi beberapa sprint yang terkelola, dengan daftar tugas (task checklist) yang konkret untuk setiap iterasi. Tujuannya adalah memberikan visibilitas progres dan panduan kerja harian bagi tim pengembangan.

## **Metodologi & Asumsi**

*   **Durasi Sprint:** Setiap sprint akan berlangsung selama **2 minggu**.
*   **Peran:**
    *   **Product Owner:** Bertanggung jawab atas prioritas backlog dan menerima hasil sprint.
    *   **Scrum Master/Project Manager:** Memfasilitasi proses dan menghilangkan hambatan.
    *   **Development Team:** Tim lintas fungsional (Frontend, Backend) yang mengerjakan tugas.
*   **Tools:** Dokumen ini berfungsi sebagai panduan awal. Tugas-tugas ini harus dipindahkan ke alat manajemen proyek (misal: Trello, Jira) untuk pelacakan harian.

## **Cara Menggunakan Dokumen Ini**

Setiap item di bawah ini adalah sebuah tugas yang dapat dilacak. Saat tugas dikerjakan, centang kotaknya.
*   `[ ]` - **To Do:** Tugas belum dimulai.
*   `[x]` - **Done:** Tugas telah selesai dan lolos pengujian unit.

---

## **Sprint 0: Persiapan & Fondasi Proyek (Durasi: ~3-5 Hari)**

*Tujuan: Menyiapkan semua alat, lingkungan, dan struktur dasar agar tim dapat mulai bekerja pada fitur di Sprint 1 tanpa hambatan.*

### **Checklist Tugas Sprint 0**
*   **[ ] Setup Proyek:**
    *   **[ ]** Buat repositori Git baru untuk Gsports v2.0.
    *   **[ ]** Inisialisasi proyek Flutter v2.0 dengan struktur direktori yang disetujui (feature-first).
    *   **[ ]** Instal semua dependensi dasar (Riverpod, go_router, Dio/Http, etc.).
*   **[ ] Setup Backend (Appwrite):**
    *   **[ ]** Siapkan proyek Appwrite baru (Cloud atau self-hosted).
    *   **[ ]** Buat semua koleksi (Collections) sesuai dokumen ERD.md (`users`, `bookings`, `match_history`, dll.).
    *   **[ ]** Definisikan semua atribut dan indeks untuk setiap koleksi.
    *   **[ ]** Simpan kredensial Appwrite (endpoint, project ID) sebagai *environment variables* di proyek Flutter.
*   **[ ] CI/CD & Workflow:**
    *   **[ ]** Konfigurasi alur kerja dasar CI/CD (misal: GitHub Actions) untuk menjalankan *analyzer* dan *tests* pada setiap *push*.
*   **[ ] Dokumentasi Awal:**
    *   **[ ]** Pastikan semua anggota tim memiliki akses ke dokumen SRS, PRD, SDD, dan ERD.

---

## **Sprint 1: Mode Tamu & Alur Login Kontekstual**

*Tujuan: Merombak pengalaman pengguna awal agar lebih ramah dengan mengizinkan penjelajahan tanpa akun. Ini adalah perubahan fundamental pada alur aplikasi.*

### **Checklist Tugas Sprint 1**
*   **[ ] Backend:**
    *   **[ ]** Sesuaikan *Permissions* pada koleksi `sport_centers` & `fields` untuk memberikan akses baca ke `role:all`.
*   **[ ] Frontend:**
    *   **[ ]** Refactor state management otentikasi (Riverpod) untuk menangani tiga status: `loading`, `guest`, `authenticated`.
    *   **[ ]** Buat UI untuk dialog/layar "Masuk untuk Melanjutkan".
    *   **[ ]** Implementasikan *navigation guards* menggunakan `go_router` pada rute yang dilindungi (misal: `/booking`, `/profile`).
    *   **[ ]** Modifikasi UI `AppBar` dan `BottomNavBar` untuk menampilkan opsi "Masuk/Daftar" saat dalam mode tamu.
*   **[ ] Pengujian:**
    *   **[ ]** Verifikasi bahwa pengguna tamu dapat mencari dan melihat detail lapangan.
    *   **[ ]** Verifikasi bahwa menekan tombol "Pesan" atau mengakses halaman profil memicu alur login.
    *   **[ ]** Verifikasi bahwa setelah login, pengguna diarahkan kembali ke alur yang benar.

---

## **Sprint 2: Monetisasi Inti (Biaya Layanan) & Booking via Functions**

*Tujuan: Mengimplementasikan aliran pendapatan pertama dan membangun pola arsitektur Functions-centric yang akan digunakan di seluruh aplikasi.*

### **Checklist Tugas Sprint 2**
*   **[ ] Backend:**
    *   **[ ]** Buat Appwrite Function pertama: `createBooking`.
    *   **[ ]** Implementasikan logika kalkulasi `base_price`, `admin_fee`, dan `final_price` di dalam fungsi.
    *   **[ ]** Konfigurasi *environment variable* di Appwrite untuk persentase `ADMIN_FEE_PERCENTAGE`.
    *   **[ ]** Atur *execute access* fungsi `createBooking` hanya untuk `role:member` (pengguna terotentikasi).
*   **[ ] Frontend:**
    *   **[ ]** Modifikasi UI halaman ringkasan pemesanan untuk menampilkan rincian biaya secara transparan.
    *   **[ ]** Refactor `BookingService` di Flutter untuk memanggil fungsi `createBooking` alih-alih `databases.createDocument` secara langsung.
    *   **[ ]** Tangani respons sukses dan error dari Appwrite Function.
*   **[ ] Pengujian:**
    *   **[ ]** Pastikan perhitungan biaya layanan selalu akurat.
    *   **[ ]** Pastikan dokumen `bookings` yang dibuat berisi semua field harga yang benar.
    *   **[ ]** Pastikan pengguna yang tidak login tidak dapat memanggil fungsi ini.

---

## **Sprint 3: Integrasi Papan Skor "SEKOR" (Fungsionalitas Inti)**

*Tujuan: Membangun fitur engagement utama yang memberikan nilai tambah signifikan bagi pengguna, bahkan di luar alur pemesanan.*

### **Checklist Tugas Sprint 3**
*   **[ ] Frontend:**
    *   **[ ]** Buat layar "Setup Pertandingan" (input nama tim/pemain, pilih olahraga).
    *   **[ ]** Buat UI Papan Skor Interaktif sesuai desain UI/UX.md (area sentuh besar, tombol kontrol).
    *   **[ ]** Implementasikan logika state management lokal untuk skor, timer, dan set.
    *   **[ ]** Buat UI untuk layar "Riwayat Pertandingan".
    *   **[ ]** Implementasikan alur "Simpan Hasil Pertandingan" yang menyimpan data ke koleksi `match_history` (untuk pengguna yang login).
    *   **[ ]** Tambahkan navigasi ke Papan Skor dari `BottomNavBar`.
*   **[ ] Pengujian:**
    *   **[ ]** Uji semua interaksi UI di papan skor (tambah/kurang skor, jeda/lanjut).
    *   **[ ]** Verifikasi bahwa hanya pengguna yang login yang dapat menyimpan hasil.
    *   **[ ]** Verifikasi bahwa data yang disimpan di `match_history` akurat.

---

## **Sprint 4: Monetisasi Papan Skor (Model Freemium & Kuota)**

*Tujuan: Mengimplementasikan model bisnis Freemium untuk fitur papan skor, mendorong pengguna gratis untuk melakukan konversi ke premium.*

### **Checklist Tugas Sprint 4**
*   **[ ] Backend:**
    *   **[ ]** Buat Appwrite Function `onUserCreate` (Trigger) untuk menginisialisasi kuota pengguna baru.
    *   **[ ]** Buat Appwrite Function `startMatch` untuk validasi kuota/status premium.
    *   **[ ]** Implementasikan logika pengurangan kuota di dalam fungsi `startMatch`.
*   **[ ] Frontend:**
    *   **[ ]** Panggil fungsi `startMatch` sebelum membuka UI Papan Skor Interaktif.
    *   **[ ]** Tangani respons sukses/error dari `startMatch`.
    *   **[ ]** Buat UI untuk dialog "Kuota Habis. Upgrade ke Premium!".
    *   **[ ]** Buat halaman informasi statis yang menjelaskan keuntungan Premium.
    *   **[ ]** Tampilkan sisa kuota di suatu tempat yang relevan (misal: halaman profil).
*   **[ ] Pengujian:**
    *   **[ ]** Verifikasi pengguna baru mendapatkan 5 kuota.
    *   **[ ]** Verifikasi kuota berkurang setelah pertandingan disimpan.
    *   **[ ]** Verifikasi pengguna diblokir saat kuota habis dan dialog upgrade muncul.
    *   **[ ]** Verifikasi pengguna premium (di-set manual di DB untuk tes) memiliki akses tak terbatas.

---

## **Sprint 5: Fitur Sosial (Pemesanan Patungan)**

*Tujuan: Mengimplementasikan fitur sosial yang paling kompleks untuk menyederhanakan koordinasi permainan grup.*

### **Checklist Tugas Sprint 5**
*   **[ ] Backend:**
    *   **[ ]** Modifikasi fungsi `createBooking` untuk menangani flag `is_patungan` dan membuat entri `host` di `booking_participants`.
    *   **[ ]** Buat Appwrite Function `joinBooking`.
*   **[ ] Frontend:**
    *   **[ ]** Tambahkan *checkbox* "Ajak Teman" di alur pemesanan.
    *   **[ ]** Konfigurasi `go_router` untuk menangani *deep link* (`gsports://booking/{booking_id}`).
    *   **[ ]** Buat UI di halaman detail booking untuk menampilkan daftar peserta dan tombol "Undang".
    *   **[ ]** Implementasikan logika untuk men-generate dan membagikan tautan undangan.
    *   **[ ]** Buat UI untuk Halaman Undangan yang terbuka dari *deep link*.
*   **[ ] Pengujian:**
    *   **[ ]** Uji alur pembuatan booking patungan.
    *   **[ ]** Uji *deep link* saat aplikasi tertutup, berjalan di latar belakang, dan sudah terbuka.
    *   **[ ]** Verifikasi bahwa daftar peserta diperbarui secara *real-time* (jika memungkinkan dengan Appwrite Realtime).

---

## **Sprint 6: Stabilisasi, Pengujian Akhir, & Persiapan Rilis**

*Tujuan: Memastikan produk berkualitas tinggi, bebas dari bug kritis, dan siap untuk diluncurkan ke pengguna.*

### **Checklist Tugas Sprint 6**
*   **[ ] Bug Fixing:**
    *   **[ ]** Alokasikan waktu untuk memperbaiki semua bug prioritas tinggi dan menengah yang ditemukan selama pengembangan.
*   **[ ] Pengujian Akhir:**
    *   **[ ]** Lakukan pengujian regresi penuh di seluruh aplikasi.
    *   **[ ]** Lakukan User Acceptance Testing (UAT) dengan sekelompok pengguna internal/beta.
    *   **[ ]** Uji performa aplikasi (waktu startup, kelancaran animasi).
*   **[ ] Persiapan Rilis:**
    *   **[ ]** Lakukan finalisasi pada teks dan terjemahan di dalam aplikasi.
    *   **[ ]** Siapkan aset untuk Google Play Store & Apple App Store (screenshot, deskripsi, ikon).
    *   **[ ]** Lakukan *build* aplikasi dalam mode rilis (`release mode`).
    *   **[ ]** Kirim aplikasi untuk ditinjau oleh platform.