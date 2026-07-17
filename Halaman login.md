










# Prompt: Perbaiki autentikasi Telegram Drive
```

Masalah ditemukan.

Database MongoDB telegram_drive sudah memiliki collection users, tetapi collection tersebut kosong.

Hasil pemeriksaan:
- db.users.countDocuments() = 0
- Login selalu gagal karena belum ada akun.

Tugas:

1. Periksa implementasi register (/register).
   - Pastikan ketika pengguna membuat akun, data benar-benar tersimpan ke collection users.
   - Password wajib di-hash menggunakan algoritma yang sama dengan login (bcrypt/argon2 sesuai proyek).

2. Jika collection users masih kosong saat aplikasi pertama dijalankan:
   - Buat seed otomatis.
   - Tambahkan akun administrator default.

Username: admin
Email: admin@telegramdrive.local
Password: admin123
Role: admin

Seed hanya dijalankan jika collection users kosong, sehingga tidak membuat akun ganda.

3. Periksa endpoint login.
   - Pastikan login mencari berdasarkan username ATAU email.
   - Verifikasi password menggunakan hash yang benar.
   - Jika berhasil, buat session/cookie lalu redirect ke /my-files.

4. Setelah login berhasil, admin dapat mengganti password dari halaman Pengaturan.

5. Jangan mengubah struktur collection lain (files, folders, uploadhistories, downloadhistories, dsb).




```


# Prompt 1 — Halaman Login
```


Buat halaman Login yang benar, menggantikan placeholder saat ini.

Persyaratan:

1. Hapus placeholder "Autentikasi belum dibuat".

2. Buat halaman Login modern dengan desain yang konsisten dengan Telegram Drive.

Komponen:

- Logo Telegram Drive
- Judul "Masuk"
- Deskripsi singkat

Field:
- Email atau Username
- Password
- Tombol Show/Hide Password

Tombol:
- Masuk
- Lupa Password
- Buat Akun

3. Validasi:
- Email wajib valid.
- Password tidak boleh kosong.
- Tampilkan pesan error yang jelas.

4. Loading:
Saat login tampilkan spinner dan nonaktifkan tombol.

5. Jika login berhasil:
- Simpan session/JWT.
- Redirect ke halaman My Files.
- Tampilkan nama pengguna dan avatar pada menu.

6. Jika gagal:
- Tampilkan pesan error dari backend.

7. Responsive untuk desktop dan mobile.

Jangan gunakan placeholder lagi.



```
