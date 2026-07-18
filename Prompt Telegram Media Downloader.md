









# 
```
# Stage 2.0 - Design Telegram Drive Integration Bridge

Jangan mengimplementasikan sinkronisasi file terlebih dahulu.

Tujuan tahap ini adalah membangun fondasi komunikasi antara Telegram Media Downloader dan Telegram Drive.

Analisis dan rancang:

1. API yang harus dimiliki Telegram Drive.
2. Endpoint yang diperlukan.
3. Authentication antar aplikasi.
4. Request/Response schema.
5. Error code.
6. Retry strategy.
7. Versioning API.
8. Security.
9. Rate limit.
10. Idempotency.

Output yang diinginkan:

- Daftar endpoint yang diperlukan.
- Struktur JSON request/response.
- Header authentication.
- Flow diagram.
- Urutan implementasi.

Jangan mengubah downloader.

Jangan mengubah website.

Jangan membuat integrasi.

Hanya desain Integration Bridge.
```
# Phase 2.1 — Sinkronisasi File
```
# Stage 2.1 - Telegram Drive Integration (Metadata Sync)

Tujuan:
Integrasikan Telegram Media Downloader dengan Telegram Drive secara bertahap.

Pada tahap ini HANYA mengimplementasikan sinkronisasi metadata file.

Jangan mengimplementasikan:

- Folder Sync
- Share Sync
- Trash
- Favorite
- Recent
- Collaboration

Semuanya akan dikerjakan pada tahap berikutnya.

--------------------------------------------------

Setelah downloader berhasil:

Download
↓

Upload ke Telegram

↓

Storage Facade selesai

↓

Bangun metadata lengkap

↓

POST ke Telegram Drive API

↓

Telegram Drive menyimpan metadata

↓

File langsung muncul di My Files

--------------------------------------------------

Gunakan Storage Facade yang sudah ada.

Jangan mengubah downloader.

Jangan mengubah pipeline upload.

Jangan mengubah command bot.

--------------------------------------------------

Metadata minimal:

telegram_file_unique_id
telegram_file_id
message_id
chat_id
title
filename
mimeType
size
duration
thumbnail
source_url
provider
createdAt
owner_id
status

--------------------------------------------------

Buat DriveSyncService.

Semua komunikasi dengan Telegram Drive harus melalui service ini.

Downloader tidak boleh mengetahui detail API website.

--------------------------------------------------

Tambahkan konfigurasi:

DRIVE_API_URL
DRIVE_API_KEY
DRIVE_TIMEOUT

Validasi saat startup.

--------------------------------------------------

Retry jika website gagal.

Gunakan exponential backoff.

--------------------------------------------------

Jika website offline:

Downloader tetap selesai.

Metadata masuk retry queue.

--------------------------------------------------

Logging:

SYNC_START

SYNC_SUCCESS

SYNC_FAILED

SYNC_RETRY

--------------------------------------------------

Output

Berikan laporan:

- File yang dibuat
- File yang diubah
- Diagram alur sinkronisasi
- Endpoint yang digunakan
- Cara rollback jika sinkronisasi dimatikan

Jangan mengimplementasikan folder, share, trash, favorite ataupun collaboration pada tahap ini.
```

# Stage 1: Hardening
```
# Prompt: Stage 1 - Hardening Telegram Media Downloader

Tujuan:
Perkuat fondasi Telegram Media Downloader berdasarkan hasil audit. Fokus pada keamanan, konsistensi data, dan kesiapan integrasi dengan Telegram Drive. Jangan mengubah alur downloader yang sudah berjalan.

## Rules

- Jangan mengubah command bot.
- Jangan mengubah UX pengguna.
- Jangan mengubah alur download.
- Jangan mengubah provider downloader.
- Jangan mengubah format database yang sudah dipakai kecuali penambahan field yang kompatibel.
- Semua perubahan harus backward compatible.

--------------------------------------------------
1. Permanent File Identity
--------------------------------------------------

Gunakan file_unique_id sebagai identitas permanen.

Jika belum ada, simpan:

- telegram_file_id
- telegram_file_unique_id

Gunakan file_unique_id sebagai referensi utama.

--------------------------------------------------
2. Soft Delete
--------------------------------------------------

Jangan langsung menghapus record.

Tambahkan field:

deletedAt
deletedBy
isDeleted

Semua query aktif harus mengabaikan record yang sudah di-soft-delete.

--------------------------------------------------
3. Thumbnail Isolation
--------------------------------------------------

Pisahkan penyimpanan thumbnail dari media utama.

Thumbnail tidak boleh bercampur dengan channel media.

Jika sudah memakai channel yang sama, buat abstraction agar nanti mudah dipindahkan tanpa mengubah kode lain.

--------------------------------------------------
4. Search Performance
--------------------------------------------------

Tambahkan index untuk:

- title
- original_url
- telegram_file_unique_id

Gunakan strategi pencarian yang efisien sesuai database yang digunakan.

--------------------------------------------------
5. Storage Layer
--------------------------------------------------

Pastikan seluruh operasi upload/download hanya melalui Storage Facade.

Tidak boleh ada akses langsung ke Telegram API di luar Storage Layer.

--------------------------------------------------
6. Metadata Validation
--------------------------------------------------

Pastikan metadata selalu lengkap:

- title
- mimeType
- size
- source
- uploader
- createdAt
- telegram_file_id
- telegram_file_unique_id

Tambahkan validasi.

--------------------------------------------------
7. Logging
--------------------------------------------------

Tambahkan logging terstruktur untuk:

- upload
- download
- storage
- error
- retry

Jangan menampilkan token/API key.

--------------------------------------------------
8. Retry
--------------------------------------------------

Jika upload Telegram gagal:

Retry otomatis dengan exponential backoff.

--------------------------------------------------
9. Queue Safety
--------------------------------------------------

Pastikan job download dan upload aman terhadap race condition.

Jangan mengubah queue yang sudah ada.

--------------------------------------------------
10. Configuration Validation
--------------------------------------------------

Validasi seluruh ENV saat startup.

Jika ada konfigurasi wajib yang hilang:

Stop aplikasi dengan pesan yang jelas.

--------------------------------------------------
11. Documentation
--------------------------------------------------

Perbarui README:

- Storage Layer
- Metadata
- Soft Delete
- File Identity
- Index
- Logging

--------------------------------------------------
12. Verification
--------------------------------------------------

Pastikan:

npm run lint

npm run typecheck

npm run build

Semua berhasil tanpa error.

--------------------------------------------------
Output
--------------------------------------------------

Berikan laporan:

- File yang diubah
- Perubahan yang dilakukan
- Risiko yang berhasil dikurangi
- Apakah proyek siap masuk Stage 2 (Integrasi Telegram Drive)

Jangan mengerjakan integrasi Telegram Drive pada tahap ini.
```

# 
```
# Prompt: Audit Repository Telegram Media Downloader

Jangan mengubah kode apa pun terlebih dahulu.

Lakukan audit menyeluruh terhadap repository Telegram Media Downloader agar memahami arsitektur proyek sebelum melakukan integrasi dengan Telegram Drive.

## Yang harus dianalisis

1. Struktur folder dan file.

2. Framework, library, dan teknologi yang digunakan.

3. Entry point aplikasi.

4. Cara bot menerima command dan message.

5. Alur download dari semua provider.

6. Cara upload hasil download ke Telegram.

7. Lokasi penyimpanan metadata.

8. Sistem database (jika ada).

9. Konfigurasi environment (.env).

10. Struktur service, handler, middleware, helper, util, dan model.

11. Sistem logging.

12. Error handling.

13. Queue atau concurrency.

14. Rate limiting.

15. Retry mechanism.

16. Cara bot menangani file besar.

17. Struktur command.

18. API internal (jika ada).

19. Potensi titik integrasi dengan Telegram Drive.

20. Risiko yang harus diperhatikan sebelum integrasi.

## Output yang diinginkan

Jangan melakukan perubahan kode.

Buat laporan audit berisi:

- Ringkasan arsitektur proyek.
- Diagram alur kerja bot.
- Daftar module utama beserta fungsinya.
- Daftar endpoint/API yang sudah ada (jika ada).
- Daftar model/database yang digunakan.
- Titik terbaik untuk integrasi dengan Telegram Drive.
- Bagian mana yang dapat digunakan kembali.
- Bagian mana yang perlu ditambah tanpa merusak fitur downloader yang sudah ada.
- Daftar rekomendasi implementasi integrasi secara bertahap.

Jangan membuat commit, jangan mengubah file, jangan melakukan refactor. Hanya lakukan analisis dan berikan laporan lengkap.
```
