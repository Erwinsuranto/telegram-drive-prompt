# Judul: Fix Server Crash After npm start
```
Project Telegram Drive.

Problem:
The application starts, connects to MongoDB, initializes the Telegram bot, then exits before Express begins listening.

Evidence:
- curl http://localhost:3000/health -> connection refused
- ss -tulpn | grep 3000 -> no process listening
- npm start exits unexpectedly after initialization.

Task:
1. Find the exact reason Node exits.
2. Check for process.exit(), uncaught exception, rejected promise, or server.close().
3. Add complete startup logging.
4. Ensure app.listen() is reached and keeps the process alive.
5. Do not refactor unrelated code.
6. Only modify the files required to keep the HTTP server running.

Output:
- Explain the root cause.
- Show changed files.
- Keep the fix minimal.


```


# Prompt: Hapus Duplikasi Gambar Upload
```
Project: Telegram Drive

Masalah:

Saat user mengupload foto, bot mengirim foto dua kali.

Yang diinginkan:

- Hanya kirim SATU foto.
- Semua informasi (nama file, ukuran, jenis, link download, waktu upload) menjadi caption pada foto tersebut.
- Jangan kirim foto kedua.
- Jangan kirim pesan teks terpisah.

Audit seluruh alur upload dan pastikan hanya ada satu pemanggilan sendPhoto() untuk balasan ke user.

Jika foto juga harus dikirim ke Channel Database, lakukan secara terpisah tanpa mengirim ulang foto ke chat user.

Hasil akhir:
- User menerima 1 foto + caption.
- Channel Database menerima 1 foto.
- Tidak ada duplikasi di chat user.

```

# Prompt: Perbaiki CSS Landing Page

```

Project: Telegram Drive

Masalah:

Landing page masih tampil sebagai HTML polos.
Semua CSS tidak diterapkan walaupun file /css/styles.css bisa diakses langsung.

Tugas:

1. Audit mengapa CSS tidak diterapkan pada halaman index.html.
2. Pastikan <link rel="stylesheet" href="/css/styles.css"> benar-benar dimuat oleh browser.
3. Periksa apakah Express static middleware mengarah ke folder public.
4. Periksa Content-Type, CSP, path relatif, dan middleware yang mungkin mengganggu.
5. Pastikan setelah server dijalankan, halaman utama tampil dengan desain modern (bukan HTML polos).

Jangan mengubah desain website.
Jangan membuat CSS baru.
Fokus hanya memperbaiki penyebab CSS tidak diterapkan.

```




# Prompt: Gabungkan Detail Upload Menjadi Caption Foto

```
Project: Telegram Drive

Ubah tampilan hasil upload.

Saat user mengirim foto:
- Jangan kirim foto lalu kirim pesan teks terpisah.
- Kirim SATU pesan saja berupa foto dengan caption.

Format caption:

✅ Upload Berhasil

📷 Photo
👤 Pengguna : digitalcel
📦 Ukuran : 112.22 KB
🆔 ID : 6a4f510...
🕒 Upload : 09 Jul 2026 • 14:43 WIB

━━━━━━━━━━━━━━

🔗 Download
https://domain.com/download/xxxxxxxx

✨ File berhasil disimpan di Telegram Drive.

Aturan:
- Foto harus menjadi preview utama.
- Semua informasi berada di caption.
- Jangan tampilkan nama file acak Telegram.
- Gunakan caption maksimal ±15 baris agar tidak terlalu panjang.
- Berlaku juga untuk Video (caption pada video), Document (caption pada dokumen), Audio (caption pada audio), dan Voice.
- Jangan mengubah proses upload atau penyimpanan database, hanya ubah cara bot mengirim hasil upload.


```



# Prompt: Perbaiki Upload ke Channel Database

```
Project: Telegram Drive

Masalah saat ini:

- User mengirim file ke bot.
- Bot menerima file.
- Metadata tersimpan ke database.
- Tetapi file tidak pernah masuk ke Telegram Channel Database.

Tugas:

1. Audit alur upload file.
2. Pastikan setiap file yang diterima bot dikirim ke CHANNEL_DATABASE menggunakan bot.sendDocument(), bot.sendPhoto(), bot.sendVideo(), bot.sendAudio(), atau bot.sendVoice() sesuai jenis file.
3. Simpan message_id dan file_id dari channel ke database.
4. Jika gagal upload ke channel, tampilkan error yang jelas di log.
5. Jangan mengubah fitur lain.

Cari penyebab mengapa file berhenti sebelum dikirim ke channel dan perbaiki sampai file benar-benar muncul di channel database.


```



# Prompt: Tambahkan Tombol Start Telegram Bot
```
Project: Telegram Drive

Tambahkan persistent menu (Telegram Bot Commands/Menu Button).

Menu yang diinginkan:

🚀 Mulai Telegram Drive
Command:
/start

📂 File Saya
Command:
/myfiles

📤 Upload File
Command:
/upload

🔍 Cari File
Command:
/search

⭐ Favorit
Command:
/favorites

🗑️ Sampah
Command:
/trash

👤 Profil Saya
Command:
/profile

❓ Bantuan
Command:
/help

Aturan:
- Gunakan Telegram Bot API setMyCommands agar menu muncul di ikon Menu Telegram.
- Saat pengguna menekan "🚀 Mulai Telegram Drive", jalankan command /start.
- Jangan mengubah fungsi command yang sudah ada.
- Jika command belum dibuat, cukup tampilkan pesan "Fitur sedang dikembangkan."
- Pastikan menu otomatis diperbarui setiap bot dijalankan.


```
# Prompt: Perbaiki Tampilan Pesan Upload Telegram Bot
```
Project: Telegram Drive

Perbaiki tampilan pesan setelah upload berhasil.

Gunakan format yang rapi, modern, dan penuh emoji. Jangan tampilkan nama file acak Telegram seperti photo-AQADxxxx.

Format yang diinginkan:

✅ Upload Berhasil!

📄 Nama File :
<nama file asli atau "Photo" jika foto Telegram>

📦 Ukuran :
72.32 KB

🗂 Jenis :
Photo / Video / Document / Audio / Voice

🆔 ID File :
12345

🔗 Download :
https://domain.com/download/xxxxxxxx

⏰ Upload :
09 Jul 2026 • 14:15 WIB

━━━━━━━━━━━━━━
✨ File berhasil disimpan di Telegram Drive.

Aturan:
- Gunakan emoji yang konsisten.
- Jangan tampilkan nama file Telegram yang panjang.
- Gunakan nama "Photo", "Video", "Document", "Audio", atau "Voice" jika tidak ada nama asli.
- Link tetap bisa diklik.
- Gunakan timezone Asia/Jakarta.
- Jangan ubah proses upload, hanya tampilan pesan.


```

```

Project: Telegram Drive

Saat ini upload berhasil, tetapi bot masih mengirim download link seperti:

http://localhost:3000/download/{downloadToken}

Hal ini tidak bisa digunakan oleh user.

Tugas:

1. Audit seluruh project yang membuat download URL.
2. Jangan hardcode localhost.
3. Gunakan BASE_URL dari environment (.env).
4. Jika BASE_URL tidak ada, tambahkan.
5. Semua link yang dikirim bot harus menggunakan BASE_URL.
6. Jangan mengubah route download yang sudah ada.
7. Jangan mengubah token download.
8. Jangan mengubah UI.

Contoh:

.env
BASE_URL=http://159.198.39.160:3000

Output bot:

http://159.198.39.160:3000/download/{downloadToken}

Jika nanti menggunakan domain, cukup mengganti BASE_URL tanpa mengubah kode.

Berikan daftar file yang diubah.

```
