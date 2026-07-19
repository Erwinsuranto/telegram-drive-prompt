






# Stage 3.1 — Metadata Sync Receiver
```
Repository:
telegram-drive

AI:
AI A

Stage:
3.1 - Metadata Sync Receiver

Repository yang dikerjakan HANYA:
telegram-drive

Jangan mengubah repository telegram-media-downloader.

Tujuan tahap ini adalah membuat endpoint POST /api/v1/integration/files benar-benar menyimpan metadata file ke database.

Implementasikan:

1. Validasi payload lengkap.
2. Simpan metadata file ke MongoDB/FileModel.
3. Gunakan file_unique_id sebagai identitas permanen.
4. Idempotency:
   - Request yang sama tidak membuat data duplikat.
5. Jika file sudah ada:
   - update metadata yang diperbolehkan.
6. Simpan:
   - file_id
   - file_unique_id
   - ownerId
   - fileName
   - mimeType
   - size
   - thumbnail
   - uploadDate
   - source
   - provider
   - metadata tambahan bila ada.
7. Tambahkan service layer terpisah.
8. Tambahkan repository layer.
9. Tambahkan validation layer.
10. Tambahkan unit test.

Jangan mengimplementasikan:

- Folder
- Share
- Trash
- Favorite
- Recent
- Collaboration

Tahap ini hanya Metadata Receiver.

Pastikan:

npm run typecheck
npm run lint
npm run build

berhasil tanpa error.
``

# Stage 3.0 - API Bridge Implementation (Part 1)
```

Stage:
3.0 - API Bridge Implementation (Part 1)

Jangan mengubah repository Telegram Media Downloader.

Pada tahap ini implementasikan server API Telegram Drive berdasarkan desain Stage 2.0.

Implementasikan hanya:

1. Middleware API Authentication menggunakan X-API-Key.

2. Middleware Idempotency-Key.

3. Endpoint:

GET /api/v1/integration/health

Response:
{
  "success": true,
  "apiKeyConfigured": true,
  "version": "v1"
}

4. Endpoint hanya skeleton:

POST /api/v1/integration/files

Belum menyimpan ke database.
Hanya:

- validasi API Key
- validasi request
- validasi idempotency
- return JSON sukses

5. Endpoint:

GET /api/v1/integration/version

6. Standard response JSON.

7. Standard error JSON.

8. Logger.

- jangan pernah log API Key
- redact header sensitif

9. Environment:

DRIVE_API_KEY

10. Dokumentasikan endpoint di README.

Yang TIDAK boleh dibuat:

- Folder
- Share
- Trash
- Favorite
- Recent
- Collaboration
- Metadata Sync
- Sinkronisasi dengan Downloader

Tahap ini hanya membangun pondasi API server.

Pastikan:

- npm run typecheck
- npm run lint
- npm run build

harus berhasil tanpa error.
``
