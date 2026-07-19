









# Stage 2.8 - Production Readiness & Queue Reliability
```
Repository:
telegram-media-downloader

AI:
AI B

Stage:
2.8 - Production Readiness & Queue Reliability

Jangan mengubah repository telegram-drive.

Kontrak API Bridge Stage 2.0-2.7 sudah final. Jangan mengubah endpoint, payload, authentication, ataupun response.

Fokus tahap ini adalah membuat Telegram Media Downloader lebih stabil untuk penggunaan produksi.

Implementasikan:

1. Queue Recovery
- Saat bot restart, queue yang masih Pending harus dilanjutkan.
- Queue Processing kembali otomatis.
- Queue Dead tetap tersimpan.

2. Startup Health Check
- Cek koneksi Database.
- Cek Telegram Bot.
- Cek Telegram API.
- Cek Drive API Health (/api/v1/integration/health).
- Tampilkan status startup.

3. Background Worker
- Worker Queue terpisah.
- Retry Queue.
- Dead Queue.
- Graceful Shutdown.

4. Monitoring
- Queue Length.
- Success Count.
- Failed Count.
- Retry Count.
- Processing Time.
- Last Sync Time.

5. Structured Logging
- Request ID.
- Queue ID.
- File Unique ID.
- Owner ID.
- Processing Duration.
- Tidak boleh log API Key maupun token.

6. Performance
- Hindari duplicate sync.
- Optimalkan memory.
- Hindari blocking upload.

7. Error Handling
- Semua error memiliki kategori.
- Retryable.
- Permanent.
- Validation.
- Network.
- Telegram.
- Database.
- API.

8. Dokumentasi
- Tambahkan README untuk Production Deployment.
- Tambahkan Recovery Guide.
- Tambahkan Queue Architecture.

Jangan mengimplementasikan:
- Folder baru.
- Share baru.
- Trash baru.
- Favorite baru.
- Recent baru.
- Collaboration baru.
- Perubahan API Bridge.

Pastikan:

npm run typecheck
npm run lint
npm run build

berhasil tanpa error.

Output harus kompatibel dengan Telegram Drive Stage 3 tanpa mengubah kontrak API.
``

# Stage 2.7 — Collaboration Sync
```
# Stage 2.7 - Collaboration Sync (Telegram Media Downloader)

Tujuan:

Implementasikan sinkronisasi Collaboration antara Telegram Media Downloader dan Telegram Drive melalui API Bridge.

Tahap ini merupakan tahap terakhir integrasi Downloader.

Jangan mengubah:

- Downloader
- Upload Telegram
- Metadata Sync
- Folder Sync
- Share Sync
- Trash Sync
- Favorite Sync
- Recent Sync
- Storage Facade
- API Bridge Contract

--------------------------------------------------

Flow

Downloader

↓

Metadata Sync

↓

Folder Sync

↓

Share Sync

↓

Trash Sync

↓

Favorite Sync

↓

Recent Sync

↓

Collaboration Sync

--------------------------------------------------

Seluruh komunikasi wajib melalui DriveSyncService.

Downloader tidak boleh mengakses endpoint API secara langsung.

--------------------------------------------------

Implementasikan:

- Create Collaboration
- Update Collaboration
- Remove Collaboration
- List Collaboration
- Collaboration Cache
- Collaboration Retry Queue

--------------------------------------------------

Permission

Implementasikan dukungan:

- View
- Download
- Upload
- Edit
- Delete

Permission mengikuti kontrak API Bridge.

--------------------------------------------------

Retry

401 / 403 / 422

Tidak retry.

429

Retry.

5xx

Retry.

Timeout

Retry.

Network Error

Retry.

--------------------------------------------------

Queue

Jika Telegram Drive offline:

Collaboration Sync masuk retry queue.

Downloader tetap dianggap berhasil.

--------------------------------------------------

Logging

Tambahkan:

COLLAB_SYNC_START

COLLAB_SYNC_SUCCESS

COLLAB_SYNC_FAILED

COLLAB_SYNC_RETRY

COLLAB_SYNC_QUEUE

API Key tidak boleh pernah tercetak pada log.

--------------------------------------------------

Backward Compatibility

Semua fitur lama harus tetap berjalan.

Tidak boleh mengubah schema lama.

Tidak boleh mengubah command bot.

Tidak boleh mengubah Storage Facade.

--------------------------------------------------

Verification

Pastikan:

npm run lint

npm run typecheck

npm run build

berhasil tanpa error.

--------------------------------------------------

Output

Berikan laporan:

- File yang dibuat.
- File yang diubah.
- Diagram Collaboration Sync.
- Retry Flow.
- Error Handling.
- Langkah pengujian.

Tahap ini menutup seluruh implementasi integrasi Telegram Media Downloader dengan Telegram Drive.
```


# 
```
# Stage 2.6 - Favorite & Recent Sync (Telegram Media Downloader)

Tujuan:

Implementasikan sinkronisasi Favorite dan Recent antara Telegram Media Downloader dan Telegram Drive melalui API Bridge.

Tahap ini hanya mengimplementasikan:

- Favorite Sync
- Recent Sync

Jangan mengimplementasikan:

- Collaboration
- Permission Management
- Multi-user Editing

--------------------------------------------------

Flow

Downloader

↓

Metadata Sync

↓

Folder Sync

↓

Share Sync

↓

Trash Sync

↓

Favorite Sync

↓

Recent Sync

--------------------------------------------------

Seluruh komunikasi wajib melalui DriveSyncService.

Downloader tidak boleh memanggil endpoint API secara langsung.

--------------------------------------------------

Implementasikan:

Favorite

- Add Favorite
- Remove Favorite
- List Favorite
- Favorite Cache

Recent

- Record Recent Access
- Update Recent Access
- Recent Cache
- Recent Cleanup

--------------------------------------------------

Retry

401 / 403 / 422

Tidak retry.

429

Retry.

5xx

Retry.

Timeout

Retry.

Network Error

Retry.

--------------------------------------------------

Queue

Jika website offline:

Favorite dan Recent masuk retry queue.

Downloader tetap dianggap berhasil.

--------------------------------------------------

Logging

Tambahkan:

FAVORITE_SYNC_START
FAVORITE_SYNC_SUCCESS
FAVORITE_SYNC_FAILED
RECENT_SYNC_START
RECENT_SYNC_SUCCESS
RECENT_SYNC_FAILED

Jangan pernah mencetak API Key.

--------------------------------------------------

Backward Compatibility

Jangan mengubah:

- Downloader
- Upload Telegram
- Metadata Sync
- Folder Sync
- Share Sync
- Trash Sync
- Storage Facade
- API Bridge

Semua fitur lama harus tetap berjalan.

--------------------------------------------------

Verification

Pastikan:

npm run lint

npm run typecheck

npm run build

berhasil tanpa error.

--------------------------------------------------

Output

Berikan laporan:

- File yang dibuat.
- File yang diubah.
- Diagram Favorite & Recent Sync.
- Retry Flow.
- Error Handling.
- Langkah pengujian.

Jangan mengimplementasikan Collaboration pada tahap ini.
```


# # Stage 2.5 - Trash Sync (Telegram Media
```
# Stage 2.5 - Trash Sync (Telegram Media Downloader)

Tujuan:

Implementasikan sinkronisasi Trash antara Telegram Media Downloader dan Telegram Drive menggunakan API Bridge.

Tahap ini hanya mengimplementasikan Trash Sync.

Jangan mengimplementasikan:

- Favorite
- Recent
- Collaboration

--------------------------------------------------

Flow

Downloader

↓

Metadata Sync

↓

Folder Sync

↓

Share Sync

↓

Trash Sync

--------------------------------------------------

Gunakan DriveSyncService.

Downloader tidak boleh mengakses endpoint API secara langsung.

--------------------------------------------------

Implementasikan:

- Move to Trash
- Restore from Trash
- Permanent Delete (jika didukung API)
- Trash Status
- Trash Cache
- Trash Retry Queue

--------------------------------------------------

Jika Trash Sync gagal:

Downloader tetap dianggap berhasil.

Masukkan operasi ke retry queue.

--------------------------------------------------

Retry Policy

401 / 403 / 422

Tidak retry.

429

Retry.

5xx

Retry.

Timeout

Retry.

Network Error

Retry.

--------------------------------------------------

Logging

Tambahkan:

TRASH_SYNC_START

TRASH_SYNC_SUCCESS

TRASH_SYNC_FAILED

TRASH_SYNC_RETRY

TRASH_SYNC_QUEUE

Jangan pernah mencetak API Key.

--------------------------------------------------

Backward Compatibility

Jangan mengubah:

- Downloader
- Upload Telegram
- Metadata Sync
- Folder Sync
- Share Sync
- Storage Facade
- API Bridge

Semua fitur lama harus tetap berjalan.

--------------------------------------------------

Verification

Pastikan:

npm run lint

npm run typecheck

npm run build

berhasil tanpa error.

--------------------------------------------------

Output

Berikan laporan:

- File yang dibuat.
- File yang diubah.
- Diagram Trash Sync.
- Retry Flow.
- Error Handling.
- Langkah pengujian.

Jangan mengimplementasikan Favorite, Recent, ataupun Collaboration pada tahap ini.
```


# Lanjut berikutnya: Stage 2.4 — Share Sync
```
# Stage 2.4 - Share Sync (Telegram Media Downloader)

Tujuan:

Implementasikan sinkronisasi Share antara Telegram Media Downloader dan Telegram Drive menggunakan API Bridge yang sudah tersedia.

Tahap ini hanya mengimplementasikan Share Sync.

Jangan mengimplementasikan:

- Trash Sync
- Favorite Sync
- Recent Sync
- Collaboration

--------------------------------------------------

Flow

Downloader

↓

Download Media

↓

Upload Telegram

↓

Metadata Sync

↓

Folder Sync

↓

Share Sync (opsional)

↓

Telegram Drive membuat Share Link

--------------------------------------------------

Gunakan DriveSyncService.

Downloader tidak boleh mengakses endpoint API secara langsung.

Seluruh komunikasi dilakukan melalui DriveSyncService.

--------------------------------------------------

Implementasikan:

- Create Share
- Update Share
- Revoke Share
- Share Permission
- Share Expiration
- Share Password (jika didukung API)
- Public / Private Share
- Share Cache

--------------------------------------------------

Jika Share gagal:

Jangan menggagalkan downloader.

Masukkan ke retry queue.

--------------------------------------------------

Retry Policy

401/403/422

Tidak retry.

429

Retry.

5xx

Retry.

Timeout

Retry.

Network Error

Retry.

--------------------------------------------------

Logging

Tambahkan:

SHARE_SYNC_START

SHARE_SYNC_SUCCESS

SHARE_SYNC_FAILED

SHARE_SYNC_RETRY

SHARE_SYNC_QUEUE

--------------------------------------------------

Backward Compatibility

Jangan mengubah:

- Downloader
- Upload Telegram
- Metadata Sync
- Folder Sync
- Storage Facade
- API Bridge

Semua fitur lama tetap berjalan.

--------------------------------------------------

Verification

Pastikan:

npm run lint

npm run typecheck

npm run build

berhasil.

--------------------------------------------------

Output

Berikan laporan:

- File yang dibuat.
- File yang diubah.
- Diagram Share Sync.
- Retry Flow.
- Error Handling.
- Langkah pengujian.
```
# AI B (repo Telegram Media Downloader).
```
# Stage 2.3 - Folder Sync (Telegram Media Downloader)

Tujuan:

Implementasikan sinkronisasi Folder antara Telegram Media Downloader dan Telegram Drive menggunakan API Bridge yang sudah tersedia.

Jangan mengimplementasikan:

- Share
- Trash
- Favorite
- Recent
- Collaboration

--------------------------------------------------

Flow

User memilih folder aktif

↓

Downloader memproses media

↓

Upload ke Telegram

↓

Metadata Sync

↓

Folder Sync

↓

Website menempatkan file ke folder yang sesuai

--------------------------------------------------

Gunakan endpoint Folder API yang sudah disediakan oleh Telegram Drive.

Seluruh komunikasi dilakukan melalui DriveSyncService.

Jangan memanggil endpoint langsung dari downloader.

--------------------------------------------------

Implementasikan:

- Folder ID
- Folder Path
- Root Folder
- Default Folder
- Folder Validation
- Folder Mapping
- Folder Cache

--------------------------------------------------

Jika Folder tidak ditemukan:

Gunakan Default Folder.

Jangan menghentikan proses download.

--------------------------------------------------

Retry

Gunakan retry policy yang sama seperti Metadata Sync.

401/403/422

Tidak retry.

5xx

Timeout

Network Error

Retry dengan exponential backoff.

--------------------------------------------------

Queue

Jika website offline:

Folder Sync masuk retry queue.

Downloader tetap sukses.

--------------------------------------------------

Logging

Tambahkan:

FOLDER_SYNC_START

FOLDER_SYNC_SUCCESS

FOLDER_SYNC_FAILED

FOLDER_SYNC_RETRY

FOLDER_SYNC_QUEUE

--------------------------------------------------

Backward Compatibility

Jangan mengubah:

- Command Bot
- Download Pipeline
- Upload Telegram
- Metadata Sync
- Storage Facade
- API Bridge
- Schema Lama

--------------------------------------------------

Verification

Pastikan:

npm run lint

npm run typecheck

npm run build

Semua berhasil.

--------------------------------------------------

Output

Berikan laporan:

- File yang dibuat.
- File yang diubah.
- Diagram Folder Sync.
- Retry Flow.
- Error Handling.
- Cara konfigurasi Folder Sync.
- Langkah pengujian.

Jangan mengimplementasikan Share, Trash, Favorite, Recent ataupun Collaboration pada tahap ini.
```
# 
```
# Stage 2.2 - Metadata Sync (Telegram Media Downloader)

Tujuan:
Hubungkan Telegram Media Downloader dengan Telegram Drive API Bridge yang sudah tersedia.

Tahap ini HANYA mengimplementasikan sinkronisasi metadata file setelah upload Telegram berhasil.

Jangan mengimplementasikan:

- Folder Sync
- Share Sync
- Trash Sync
- Favorite Sync
- Recent Sync
- Collaboration

Semua akan dikerjakan pada tahap berikutnya.

--------------------------------------------------
Flow
--------------------------------------------------

Downloader
↓

Download media

↓

Upload ke Telegram

↓

Storage Facade selesai

↓

Bangun metadata

↓

POST ke Telegram Drive API

↓

Selesai

--------------------------------------------------

Gunakan endpoint API Bridge yang sudah tersedia pada Telegram Drive.

Seluruh komunikasi dilakukan melalui DriveSyncService.

Jangan mengakses endpoint secara langsung dari downloader.

--------------------------------------------------

Metadata minimal

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

provider

source_url

createdAt

ownerId (opsional)

--------------------------------------------------

Authentication

Gunakan:

X-API-Key

Idempotency-Key

sesuai kontrak API Bridge.

--------------------------------------------------

Retry

Jika request gagal karena:

timeout

5xx

network error

gunakan exponential backoff.

Jika gagal karena:

401

403

422

jangan retry.

--------------------------------------------------

Queue

Jika Telegram Drive sedang offline:

masukkan metadata ke retry queue.

Downloader tetap dianggap berhasil.

--------------------------------------------------

Logging

Tambahkan log:

SYNC_START

SYNC_SUCCESS

SYNC_FAILED

SYNC_RETRY

SYNC_QUEUE

Jangan pernah mencetak API Key.

--------------------------------------------------

Backward Compatibility

Jangan mengubah:

- command bot
- pipeline downloader
- upload Telegram
- Storage Facade
- schema lama

Semua fitur lama harus tetap berjalan.

--------------------------------------------------

Verification

Pastikan:

npm run lint

npm run typecheck

npm run build

berhasil tanpa error.

--------------------------------------------------

Output

Berikan laporan:

- file yang dibuat
- file yang diubah
- alur sinkronisasi
- cara konfigurasi DRIVE_API_URL
- cara konfigurasi DRIVE_API_KEY
- cara mengaktifkan atau menonaktifkan sinkronisasi
- langkah pengujian untuk memastikan metadata berhasil dikirim ke Telegram Drive

Jangan mengimplementasikan Folder, Share, Trash, Favorite, ataupun Collaboration pada tahap ini.
```
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
