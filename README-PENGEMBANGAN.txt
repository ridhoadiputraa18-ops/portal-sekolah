PORTAL SEKOLAH — PORTAL AKADEMIK
=================================

File utama:
- portal-sekolah.html: website profil sekolah.
- portal-akademik.html: login guru, dashboard, input nilai, ranking, rapor PDF.
- server.py: backend Python dengan login sesi dan API nilai.
- portal_sekolah.db: dibuat otomatis saat server pertama dijalankan.
- img/: aset gambar sekolah.

JALANKAN DI TERMUX
1. Ekstrak ZIP.
2. Masuk ke folder hasil ekstrak yang berisi server.py.
3. Jalankan: python server.py (port default 8080; bisa diubah dengan PORT=8081 python server.py)
4. Buka Chrome: http://127.0.0.1:8080/portal-sekolah.html
5. Login awal: guru / guru123
6. Ubah password awal sebelum pemakaian sungguhan; lihat catatan keamanan di bawah.

ALUR NILAI
- Guru mengisi Tugas, UTS, UAS.
- Tekan Submit Nilai.
- Server memvalidasi rentang 0–100 dan menyimpan ke SQLite.
- Dashboard menghitung nilai akhir: Tugas 25% + UTS 30% + UAS 45%.
- Ranking dan rapor memakai data yang sudah disubmit.
- PDF dibuat melalui dialog cetak browser (pilih Save as PDF).

CATATAN
- Akun awal disediakan agar sistem bisa langsung diuji secara lokal.
- Login memakai hash PBKDF2 dan sesi cookie HttpOnly; server hanya bind ke localhost.
- Ini backend lokal satu perangkat, belum hosting publik/multi-user lintas jaringan.
- Sebelum deployment publik, buat pengelolaan akun guru, ubah kredensial awal, tambah HTTPS,
  proteksi CSRF/rate-limit, audit log, backup database, serta kebijakan akses per guru.
- Bobot dan KKM masih nilai awal contoh (25/30/45 dan KKM 75), sesuaikan dengan kebijakan sekolah.
