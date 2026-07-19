



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
