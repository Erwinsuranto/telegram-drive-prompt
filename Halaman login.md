









# 
```


Masih ada bug pada autentikasi.

Gejalanya:
- Saya sudah berhasil login.
- Halaman My Files sudah bisa diakses.
- Tetapi drawer/menu masih menampilkan menu Guest:
  - Masuk
  - Buat Akun

Ini berarti status login yang dipakai drawer berbeda dengan status login aplikasi.

Perbaiki dengan benar.

Yang harus dilakukan:

1. Gunakan SATU sumber status autentikasi.
   Misalnya:
   - cookie telegram_drive_session
   - JWT
   - auth context
   - server session

2. Drawer TIDAK BOLEH memakai state lokal sendiri.

3. Saat halaman dibuka:
   - cek session dari server (/api/auth/me atau endpoint yang digunakan)
   - jika user login tampilkan menu user
   - jika belum login tampilkan menu guest

4. Setelah login berhasil:
   - update auth context
   - refresh status user
   - drawer langsung berubah tanpa reload.

5. Setelah logout:
   - hapus session
   - drawer kembali ke mode guest.

Menu Guest hanya:

🏠 Beranda
ℹ️ Tentang
❓ Bantuan

----------------

🔐 Masuk
📝 Buat Akun

Menu User:

🏠 Beranda
📁 File Saya
⬆️ Unggah
🔍 Cari
🤝 Shared with me
🤝 Collaborate
⭐ Favorit
👤 Profil
⚙️ Pengaturan
ℹ️ Tentang
❓ Bantuan

----------------

🚪 Keluar

Jangan sembunyikan dengan CSS.

Perbaiki penyebab utamanya.

Cari sendiri kenapa drawer masih menganggap user sebagai guest walaupun login berhasil.



```
# 
```



Menu drawer masih salah.

Saya ingin menu berubah berdasarkan status login.

== SAAT BELUM LOGIN ==
Hanya tampilkan:

🏠 Beranda
ℹ️ Tentang
❓ Bantuan

----------------

🔐 Masuk
📝 Buat Akun

JANGAN tampilkan:
- File Saya
- Unggah
- Cari
- Shared with me
- Collaborate
- Profil
- Favorit
- Recent
- Pengaturan
- Logout

==================================================

== SETELAH LOGIN ==

Tampilkan:

🏠 Beranda
📁 File Saya
⬆️ Unggah
🔍 Cari
👤 Profil
⭐ Favorit
🕒 Recent
🤝 Shared with me
🤝 Collaborate
⚙️ Pengaturan
ℹ️ Tentang
❓ Bantuan

----------------

🚪 Keluar

JANGAN tampilkan lagi:
- Masuk
- Buat Akun

==================================================

Gunakan status autentikasi (session/cookie/token) sebagai satu-satunya penentu.

Semua menu harus dirender secara conditional, bukan disembunyikan dengan CSS.

Setelah login atau logout, drawer harus otomatis berubah tanpa refresh halaman.

Cari penyebab bug apabila menu guest masih muncul setelah login.


```

# 
```

Masalah:

Login sudah berhasil dan user sudah berada di halaman My Files, tetapi drawer masih menampilkan menu Guest:
- 🔒 Masuk
- ✍️ Buat Akun

Ini adalah bug.

Perbaiki dengan aturan berikut:

1. Setelah login berhasil, cek session/cookie/token autentikasi saat render drawer.

2. Jika user sudah login:
   Hapus menu:
   - Masuk
   - Buat Akun

3. Ganti dengan menu user:

👤 Profil
⭐ Favorit
🕒 Terbaru
📤 Dibagikan
⚙️ Pengaturan
🚪 Keluar

4. Menu Guest hanya boleh muncul jika user BELUM login.

5. Pastikan status login diperiksa saat:
   - halaman pertama dimuat,
   - refresh browser,
   - membuka drawer,
   - pindah halaman.

6. Jika session berubah (login/logout), drawer harus otomatis melakukan re-render tanpa perlu refresh manual.

7. Cari penyebab bug. Kemungkinan:
   - Drawer menggunakan state login lama.
   - Session hanya dicek saat aplikasi pertama dibuka.
   - Cookie sudah dibuat tetapi drawer tidak membaca ulang status autentikasi.
   - Context/AuthProvider tidak mengirim update ke Drawer.

8. Jangan gunakan CSS untuk menyembunyikan menu. Perbaiki logika render berdasarkan status autentikasi.

Hasil akhir:

Belum login:
- Beranda
- File Saya
- Unggah
- Cari
- Tentang
- Bantuan
- Masuk
- Buat Akun

Sudah login:
- Beranda
- File Saya
- Unggah
- Cari
- Tentang
- Bantuan
- Profil
- Favorit
- Terbaru
- Dibagikan
- Pengaturan
- Keluar

Menu "Masuk" dan "Buat Akun" tidak boleh muncul setelah login berhasil.




```


# Prompt: Perbaiki autentikasi Telegram Drive
```


Masalah:

Setelah login berhasil, di drawer/menu masih muncul DUA tombol "Masuk" yang identik.

Ini bukan karena menu guest dan user tampil bersamaan, tetapi karena komponen tombol "Masuk" dirender dua kali.

Perbaiki sebagai berikut:

1. Cari semua komponen yang merender tombol "Masuk".
2. Pastikan hanya ada SATU tombol "Masuk" pada kondisi user belum login.
3. Jangan pernah merender tombol "Masuk" dua kali, baik di mobile maupun desktop.
4. Periksa apakah:
   - DrawerMenu dan MobileDrawer sama-sama merender tombol login.
   - Ada komponen LoginButton yang dipanggil dua kali.
   - Ada array menu yang berisi item "Masuk" lebih dari satu.
5. Setelah login berhasil:
   - Semua tombol "Masuk" harus hilang.
   - Semua tombol "Buat Akun" harus hilang.
6. Setelah logout:
   - Hanya muncul SATU tombol "Masuk".
   - Hanya muncul SATU tombol "Buat Akun".
7. Jangan menggunakan CSS display:none untuk menyembunyikan tombol duplikat. Hapus penyebab render ganda pada source code.
8. Audit seluruh komponen drawer/menu agar tidak ada item yang didaftarkan dua kali.

Hasil akhir:
- Guest: hanya 1 tombol Masuk dan 1 tombol Buat Akun.
- Login: tidak ada tombol Masuk maupun Buat Akun.



```
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
