













# 
```

# Prompt: Build Complete Folder Management for Telegram Drive

Tujuan:
Bangun sistem Folder Management yang modern seperti Google Drive, MEGA, dan Dropbox. Semua file harus dapat dikelompokkan ke dalam folder. Sistem harus siap digunakan oleh file yang berasal dari Website maupun Telegram Downloader Bot.

## Folder List

Buat halaman Folder yang menampilkan:

- Folder Card/Grid
- Folder List View
- Nama Folder
- Jumlah File
- Total Ukuran
- Tanggal Dibuat
- Tanggal Update Terakhir
- Icon Folder

## Folder Actions

Saat menekan tombol (⋮) tampilkan:

- Open
- Rename
- Move
- Share
- Favorite
- Delete

## Create Folder

Tambahkan tombol:

+ New Folder

Saat ditekan tampilkan dialog:

- Nama Folder
- Tombol Cancel
- Tombol Create

Validasi:

- Nama tidak boleh kosong.
- Tidak boleh ada folder dengan nama yang sama pada lokasi yang sama.

## Rename Folder

Dialog Rename Folder.

## Delete Folder

Jika folder kosong:
- Hapus langsung setelah konfirmasi.

Jika folder berisi file:
Tampilkan pilihan:

- Pindahkan file ke folder lain
- Hapus seluruh isi folder
- Batal

## Move File

Saat memilih Move pada file:

Tampilkan Folder Picker.

User dapat memilih folder tujuan.

## Breadcrumb

Contoh:

Home
>
My Files
>
Photos
>
Vacation

Breadcrumb harus dapat ditekan.

## Search Folder

Search Folder secara realtime.

## Sort Folder

- Nama A-Z
- Nama Z-A
- Terbaru
- Terlama

## Favorite Folder

Folder dapat ditandai Favorite.

## Empty State

Jika belum ada folder:

Tampilkan ilustrasi.

Pesan:

"Belum ada folder."

"Tekan New Folder untuk membuat folder pertama."

## Loading

Gunakan Skeleton Loading.

## Error

Jika folder tidak ditemukan tampilkan Folder Not Found.

## Mobile

Gunakan Bottom Sheet.

## Desktop

Gunakan Context Menu.

## API

Semua folder menggunakan API.

Jangan menggunakan data dummy.

Gunakan service/repository yang sudah ada.

## Persiapan Telegram Downloader Bot

Saat integrasi selesai:

- File hasil Telegram Downloader Bot dapat langsung disimpan ke folder pilihan user.
- Upload Website juga dapat memilih folder.
- Upload Telegram Bot juga menggunakan struktur folder yang sama.

Folder menjadi struktur utama penyimpanan Telegram Drive.

## Target

Folder Management harus siap dipakai sebagai fondasi Telegram Drive sehingga seluruh file dari Website maupun Telegram Downloader Bot memiliki struktur penyimpanan yang rapi, modern, responsif, dan mudah dikelola.




```


# 
```

# Prompt: Build Professional File Details & Preview Page

Tujuan:
Buat halaman Detail File yang profesional seperti Google Drive, MEGA, atau Dropbox. Halaman ini akan menjadi pusat informasi setiap file yang dipilih dari halaman My Files dan harus siap digunakan oleh file yang berasal dari Website maupun Telegram Downloader Bot.

## Navigasi

- Saat user menekan file di My Files, buka halaman Detail File.
- Gunakan routing dinamis berdasarkan fileId.
- Jangan menggunakan data dummy.
- Ambil seluruh data melalui API/service yang sudah ada.

## Header

Tampilkan:
- Tombol Back.
- Nama file.
- Tombol More (⋮).

## Preview

Preview otomatis berdasarkan tipe file.

Image
- Preview penuh.
- Zoom.
- Fullscreen.

Video
- Video player.
- Play/Pause.
- Seek.
- Fullscreen.

Audio
- Audio player.
- Cover jika tersedia.
- Progress bar.

PDF
- Embedded PDF Viewer.

Dokumen lain
- Icon sesuai tipe file.
- Informasi file.

## Informasi File

Tampilkan:

- Nama File
- Ukuran
- MIME Type
- Folder
- Owner
- Upload Date
- Last Modified
- Download Count
- Telegram Message ID (hidden developer field)
- File Status

## Action Buttons

Primary

- Download

Secondary

- Share
- Copy Link
- Favorite / Unfavorite
- Rename
- Move
- Delete

## Share

Siapkan UI untuk:

- Copy Link
- Share Public
- Share Private
- Expired Link (coming soon)

## Preview Error

Jika preview gagal:

- tampilkan icon file
- tampilkan pesan
- tombol Download tetap tersedia

## Loading

Gunakan Skeleton Loading.

## Error

Jika file tidak ditemukan:

- tampilkan halaman File Not Found
- tombol Back
- tombol My Files

## Mobile

Gunakan Bottom Sheet untuk menu.

Desktop gunakan Right Information Panel.

## API

Gunakan service layer yang sudah ada.

Jangan hardcode data.

Semua data berasal dari API.

## Arsitektur

Pisahkan:

- UI
- Components
- Hooks
- API
- Types

## Persiapan Integrasi Telegram Downloader Bot

Halaman ini harus langsung kompatibel dengan file yang berasal dari:

- Upload Website
- Upload Telegram Bot
- Telegram Downloader Bot

Tanpa perlu perubahan UI ketika integrasi selesai.

## Target

Halaman Detail File menjadi halaman utama untuk melihat preview, informasi, dan mengelola setiap file di Telegram Drive dengan tampilan modern, cepat, responsif, dan siap terintegrasi penuh dengan Telegram Downloader Bot.




```


# Prompt AI A - Tahap Berikutnya Prompt: Sempurnakan Halaman My Files
```



# Prompt: Complete My Files Page

Tujuan:
Jadikan halaman My Files sebagai pusat pengelolaan file Telegram Drive. Halaman ini harus siap menerima file dari Website maupun Telegram Downloader Bot di masa depan.

Yang harus dikerjakan:

1. Layout
- Tampilan bersih seperti Google Drive / MEGA.
- Responsive desktop, tablet, dan mobile.
- Konsisten dengan tema Telegram Drive.

2. File List
Setiap file menampilkan:
- Thumbnail (jika gambar/video)
- Icon sesuai tipe file
- Nama file
- Ukuran file
- Tanggal upload
- Tombol menu (⋮)

3. Menu File (⋮)
- Download
- Share
- Rename
- Move
- Favorite / Unfavorite
- Delete
- Detail

4. Empty State
Jika belum ada file:
- Tampilkan ilustrasi sederhana.
- Pesan:
  "Belum ada file."
  "Upload file atau gunakan Telegram Downloader Bot untuk mulai menyimpan file."

5. Loading State
- Gunakan skeleton loading.
- Jangan tampilkan halaman kosong saat data dimuat.

6. Search
Tambahkan search bar di bagian atas halaman.

7. Sort
Tambahkan pilihan:
- Terbaru
- Terlama
- Nama A-Z
- Nama Z-A
- Ukuran terbesar
- Ukuran terkecil

8. View Mode
Tambahkan switch:
- Grid View
- List View

9. Selection Mode
Long press atau checkbox untuk memilih banyak file.
Saat aktif tampilkan:
- Select All
- Download ZIP
- Delete
- Move

10. Pagination / Infinite Scroll
Gunakan infinite scroll atau pagination agar performa tetap baik.

11. API Preparation
Pisahkan UI dari data.
Gunakan service/API layer sehingga nanti data dapat berasal dari:
- Upload Website
- Telegram Downloader Bot
- Upload Telegram Bot

Jangan gunakan data dummy yang tertanam di komponen. Semua komponen harus siap dihubungkan ke API.

Target akhir:
Halaman My Files menjadi pusat semua file pengguna dan siap menerima sinkronisasi dari Telegram Downloader Bot tanpa perlu perubahan struktur UI.


```

# Prompt: Rapikan Footer Halaman Home
```
Rapikan footer pada halaman Home Telegram Drive agar tampil lebih modern dan tidak seperti website biasa.

Perubahan yang harus dilakukan:

1. Hapus footer lama yang terdiri dari tiga baris:
   - Telegram Drive
   - Version 0.1.0
   - Copyright © 2026

2. Ganti menjadi footer minimalis satu baris:

────────────────────────
Telegram Drive • v0.1.0 • ©2026

3. Footer hanya berupa teks, tanpa:
   - Card
   - Background khusus
   - Shadow
   - Border tebal

4. Tambahkan hanya border-top tipis (1px) sebagai pemisah dari konten.

5. Style:
   - Font size: 13–14px
   - Warna teks: abu-abu (#6B7280)
   - Text align: center
   - Padding atas & bawah: 16px
   - Margin-top: 24px

6. Jika tinggi konten belum memenuhi layar, footer tetap berada di bagian bawah halaman (sticky footer menggunakan Flex Layout), tetapi tidak menutupi konten.

7. Jangan gunakan position: fixed karena akan menutupi konten saat halaman memiliki banyak isi.

8. Footer harus responsif di desktop, tablet, dan mobile.

Hasil akhir yang diinginkan:

────────────────────────
Telegram Drive • v0.1.0 • ©2026

Tujuan:
- Tampilan lebih modern seperti aplikasi Google Drive atau MEGA.
- Menghemat ruang.
- Tidak mengganggu fokus pengguna.
- Mudah diperbarui ketika versi aplikasi berubah.




```
# 
```

Ubah informasi aplikasi pada halaman Profil.

Jangan gunakan layout vertikal:

Telegram Drive
Version 0.1.0
Copyright ©2026

Ganti menjadi satu baris yang ringkas:

────────────────────────────

Telegram Drive • v0.1.0 • ©2026

Style:
- Border top tipis.
- Margin-top 24px.
- Padding-top 16px.
- Padding-bottom 16px.
- Font size 13–14px.
- Warna teks abu-abu (#6b7280).
- Center horizontal.
- Tidak menggunakan card.
- Tidak menggunakan shadow.
- Tidak menggunakan background khusus.
- Hanya tampil di halaman Profil/Akun.
- Jangan tampil di halaman lain.




```


# 
```

Continue the project following SPEC.md and ROADMAP.md.

Use TWO design references:

1. Homepage Digital Cell reference image.
2. Login & Register reference image I just uploaded.

These are the official design references for the project.

Your job is to reproduce this Authentication UI as accurately as possible while following the project's architecture.

Requirements

Build:

- Login Page
- Register Page

Follow the uploaded design almost pixel-perfect.

Implement:

LOGIN
- Logo
- Welcome text
- WhatsApp input
- Password input
- Show / Hide password
- Remember Me
- Forgot Password
- Login button
- Divider
- Google Login button
- Apple Login button
- Register link

REGISTER

- Logo
- Full Name
- WhatsApp
- Email (optional)
- Password
- Confirm Password
- Show / Hide Password
- Terms checkbox
- Register button
- Google Login
- Apple Login
- Login link

Animations

Use Framer Motion.

Match:

- spacing
- typography
- rounded corner
- shadows
- colors
- gradients
- icons
- transitions

Responsive:

- Mobile
- Tablet
- Desktop

Reuse existing UI components.

No backend.
No API.
Mock data only.

Rules

- No duplicated code
- No hardcoded colors
- No any
- Use design tokens
- Follow existing architecture

When finished

- Update ROADMAP.md
- Mark ONLY Login & Register tasks complete
- Update progress percentage
- Update CHANGELOG.md
- Commit changes




```

# 
```

Layout footer sekarang salah.

Jangan pindahkan footer ke tengah halaman.

Yang saya inginkan:

1. Footer tetap berada PALING BAWAH halaman.
2. Tetapi jarak antara konten terakhir dan footer cukup sekitar 24px.
3. Jangan ada area kosong ratusan pixel sebelum footer.
4. Jangan gunakan spacer kosong.
5. Jangan gunakan div kosong.
6. Jangan gunakan margin-top besar.
7. Jangan gunakan position:absolute ataupun fixed untuk footer.
8. Footer mengikuti tinggi konten (natural flow).

Susunan halaman harus seperti ini:

Header
↓

Konten Search
↓

(jarak sekitar 24px)

────────────────────

Telegram Drive
Version 0.1.0
Copyright © 2026

────────────────────

akhir halaman

Cari penyebab sebenarnya kenapa footer muncul di tengah halaman.
Kemungkinan parent layout memakai min-height:100vh, flex-1, justify-between, atau mt-auto.

Perbaiki layout parent, bukan hanya mengubah margin footer.

Jelaskan file yang diubah dan penyebab bug setelah selesai.




```

# 
```



Perubahan footer tidak ada efek sama sekali.

Saya sudah:
- Build ulang
- Restart PM2
- Hapus cache browser
- Hapus data aplikasi browser

Tampilan tetap sama.

Artinya file yang diubah bukan file/layout yang digunakan halaman Profil.

Lakukan investigasi.

1. Cari komponen footer yang sebenarnya dirender pada halaman Profil.
2. Cari layout parent yang membungkus halaman Profil.
3. Cari apakah ada:
   - min-height: 100vh
   - flex: 1
   - flex-grow
   - justify-between
   - justify-content: space-between
   - mt-auto
   - padding-bottom besar
   - spacer kosong
   - div kosong
   - container dengan tinggi penuh

Kemungkinan besar ruang kosong berasal dari parent layout, bukan dari footer.

Perbaiki agar:

[Konten Profil]
↓ jarak sekitar 20–24px
[Footer]
Telegram Drive
Version 0.1.0
Copyright © 2026

Footer harus langsung berada setelah konten, bukan terdorong ke bawah oleh layout.

Setelah selesai, sebutkan:
- file yang diubah
- class CSS yang diubah
- penyebab sebenarnya kenapa perubahan sebelumnya tidak berpengaruh.


```
# 
```

Rapikan footer halaman Profil dan seluruh website.

Masalah saat ini:
Footer "Telegram Drive - Version - Copyright" memiliki jarak kosong (margin/padding-top) yang terlalu besar dari konten di atasnya.

Perbaiki menjadi seperti aplikasi mobile modern.

Yang diinginkan:

- Kurangi margin-top footer menjadi sekitar 16–24px.
- Jangan ada ruang kosong yang sangat lebar sebelum footer.
- Footer tetap berada di bawah card terakhir dengan jarak yang proporsional.
- Gunakan padding vertikal yang lebih kecil.
- Footer tidak perlu memakan tinggi layar.

Contoh struktur:

-----------------------
[ Card Keluar ]
(jarak 20px)

-----------------------
Telegram Drive
Version 0.1.0
Copyright © 2026
-----------------------

Gunakan spacing yang konsisten di seluruh halaman (8px / 16px / 24px), jangan ada margin acak yang terlalu besar.

Periksa apakah jarak tersebut berasal dari:
- margin-top
- padding-top
- min-height
- flex-grow
- spacer kosong
- layout wrapper

Hapus spacer yang tidak diperlukan agar footer naik mendekati konten.




```

# Prompt untuk AI
```


Rapikan struktur drawer/menu Telegram Drive.

Drawer sekarang terlalu ramai.

Buat struktur baru seperti aplikasi cloud modern (Google Drive / MEGA / Dropbox).

==========================
DRAWER
==========================

🏠 Beranda

📁 File Saya
⬆️ Unggah
🔍 Cari

-------------------------

👤 Profil

-------------------------

ℹ️ Tentang
❓ Bantuan

-------------------------

🚪 Keluar

==========================

Pindahkan menu berikut ke halaman Profil:

⭐ Favorit
🕒 Recent
🤝 Shared with me
👥 Collaborate
⚙️ Pengaturan

==========================

Halaman Profil menjadi pusat akun.

Urutannya:

Avatar
Nama
Email
Username

-------------------------

🔑 Ganti Password

-------------------------

⭐ Favorit
🕒 Recent
🤝 Shared with me
👥 Collaborate

-------------------------

⚙️ Pengaturan

-------------------------

🚪 Keluar

==========================

Gunakan ikon konsisten (SVG/Lucide), jangan memakai emoji.

Drawer harus lebih pendek sehingga seluruh menu utama terlihat tanpa perlu scroll pada layar HP.



```
# 
```

Sekarang bug berubah.

Sebelumnya:
- Semua orang bisa membuka /my-files tanpa login.

Sekarang:
- Halaman sudah diproteksi.
- Tetapi setelah login berhasil, saya tetap kembali ke halaman /login.

Jangan melakukan perubahan secara acak.

Lakukan debugging terlebih dahulu.

Periksa dan tampilkan hasil berikut:

1. Setelah POST /api/auth/login
   - apakah response status 200?
   - apakah Set-Cookie dikirim?
   - nama cookie apa?
   - apakah cookie benar-benar tersimpan di browser?

2. Setelah redirect
   panggil /api/auth/me

Tampilkan hasilnya.

Harus diketahui apakah:
- 200 + user
atau
- 401

3. Middleware

Tambahkan log sementara:

- cookie diterima?
- token ditemukan?
- token valid?
- user ditemukan?

4. Pastikan nama cookie sama di semua tempat.

Misalnya:

SESSION_COOKIE=telegram_drive_session

Harus dipakai oleh:
- login
- logout
- auth/me
- middleware
- auth helper

Tidak boleh ada:
telegram_session
session
auth_token
telegram_drive_session

yang berbeda-beda.

5. Jika memakai JWT:
- cek verify()
- cek secret sama
- cek expire

6. Jika memakai Mongo:
- cek user ditemukan
- cek session ditemukan

Jangan ubah UI lagi.

Cari akar masalah kenapa setelah login middleware tetap menganggap user belum login.

Setelah menemukan penyebabnya, baru perbaiki.




```
# 
```


Masih ada bug autentikasi yang sangat serius.

Langkah reproduksi:

1. Hapus semua data browser (cookies, localStorage, sessionStorage).
2. Tutup browser.
3. Buka langsung:

/my-files

Hasil sekarang:
Halaman My Files tetap bisa diakses tanpa login.

Ini SALAH.

Yang benar:

Jika user BELUM login:

- /my-files
- /upload
- /shared-with-me
- /favorites
- /recent
- /profile
- /settings

WAJIB redirect ke:

/login

Tidak boleh menampilkan halaman My Files walaupun satu detik.

===================================

Periksa seluruh sistem autentikasi.

Cari penyebab sebenarnya.

Kemungkinan:
- middleware.ts tidak melindungi route
- layout tidak mengecek session
- page.tsx tidak memanggil auth()
- SessionProvider default menganggap login
- route /my-files menggunakan dummy user
- cookie tidak pernah divalidasi
- fallback memakai user "default"

===================================

Saya ingin proteksi dilakukan di SERVER.

Jangan hanya sembunyikan komponen React.

Gunakan middleware atau server component.

Pseudo:

if (!session) {
   redirect('/login');
}

bukan

if (!user) return null;

===================================

Periksa seluruh route yang membutuhkan login.

Pastikan semua route privat tidak dapat diakses tanpa session yang valid.

Jika ada dummy user, default user, bypass auth, development mode, atau fallback session, hapus semuanya.

Tidak boleh ada akses ke My Files tanpa login.

Cari akar masalahnya, bukan hanya memperbaiki tampilan.



```

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
