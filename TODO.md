# TODO: Hosting Website Jurnal Harian

File utama: `index.html` (satu file, tanpa build). Cukup diunggah ke hosting statis.

## 1. Sebelum hosting

- [ ] Unduh `index.html` dan simpan dalam satu folder, misalnya `jurnal-harian/`
- [ ] Buka file di **HP** dan **PC**, cek tampilan terang dan gelap
- [ ] Uji alur lengkap: Daftar, Masuk, Keluar, lalu Masuk lagi
- [ ] Uji tiap tab: Makanan, Aktivitas (tidur, olahraga, skripsi), Curhat, Laporan harian dan bulanan, Hadiah
- [ ] Cek aturan poin: makanan pedas atau manis −50, makanan sehat +1 sampai +5, olahraga dan skripsi +1 sampai +5, tidur lewat jam 12 malam −10 sampai −20
- [ ] Putuskan soal **riset gizi otomatis** (lihat bagian 4). Di luar claude.ai, fitur ini jatuh ke mode offline dengan data gizi bawaan (sekitar 25 makanan umum)
- [ ] Putuskan soal **akun**: sekarang login hanya lokal per browser (lihat bagian 4)
- [ ] Siapkan teks kebijakan privasi singkat (data apa yang disimpan, di mana, cara menghapus)

## 2. Hosting gratis dengan GitHub Pages (disarankan)

- [ ] Buat repository baru, misalnya `jurnal-harian` (Public)
- [ ] Unggah `index.html` ke root repository
- [ ] Buka **Settings → Pages → Build and deployment**
- [ ] Pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, lalu Save
- [ ] Tunggu 1–3 menit sampai alamat muncul, formatnya `https://<username>.github.io/jurnal-harian/`
- [ ] Buka alamatnya di HP dan PC, pastikan memakai **https** (login butuh https agar password bisa diamankan)

### Alternatif yang sama mudahnya

- [ ] **Netlify Drop**: seret folder ke app.netlify.com/drop, alamat langsung jadi
- [ ] **Cloudflare Pages**: hubungkan repository, tanpa perintah build, folder output `/`
- [ ] **Vercel**: impor repository, framework "Other"

## 3. Setelah online

- [ ] Uji ulang daftar, masuk, dan simpan catatan di alamat publik
- [ ] Uji "Tambahkan ke layar utama" di HP supaya terasa seperti aplikasi
- [ ] Ganti judul tab dan deskripsi di `<head>` kalau mau memakai nama brand klien
- [ ] (Opsional) pasang domain sendiri: beli domain, arahkan DNS ke hosting, aktifkan HTTPS
- [ ] (Opsional) pasang analitik ringan, misalnya Cloudflare Web Analytics
- [ ] Bagikan tautan ke klien dan kumpulkan masukan

## 4. Keputusan dan pengembangan lanjutan

### Riset gizi otomatis
- [ ] Pilih satu: tetap pakai mode offline, atau buat layanan perantara (misalnya Cloudflare Worker) yang memanggil API Claude
- [ ] Kalau memakai API: simpan API key **hanya di server**, jangan pernah di dalam `index.html`
- [ ] Perluas daftar makanan offline dengan makanan khas yang sering dimakan klien

### Akun dan data
- [ ] Sekarang: akun dan data hanya ada di browser perangkat itu, tidak sinkron, dan password lupa tidak bisa dipulihkan
- [ ] Kalau butuh login lintas perangkat: pakai Firebase Authentication + Firestore atau Supabase
- [ ] Tambahkan tombol ekspor atau cadangan data supaya klien tidak kehilangan catatan

### Pengingat ke Gmail
- [ ] Buat Gmail khusus pengirim, misalnya `jurnalharian.official@gmail.com`
- [ ] Buat Google Sheet untuk daftar email, lalu pasang Google Apps Script dengan pemicu harian (misalnya jam 20.00)
- [ ] Tambahkan kolom email opsional di form daftar, persetujuan pengguna, dan cara berhenti berlangganan
- [ ] Ingat batas kirim Gmail biasa sekitar 100 email per hari

## 5. Perawatan

- [ ] Simpan salinan `index.html` di tempat aman (Drive atau repository)
- [ ] Catat setiap perubahan aturan poin supaya klien tidak bingung
- [ ] Cek tampilan sesekali di browser baru (Chrome, Safari, Firefox)
