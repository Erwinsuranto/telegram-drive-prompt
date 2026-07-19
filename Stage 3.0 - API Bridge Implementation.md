


















# 
```
# Stage 3.7 — Integrasi Telegram Media Downloader ↔ Telegram Drive

Repository: telegram-drive
AI: AI A

Tujuan:

Menghubungkan seluruh API Telegram Drive yang sudah selesai dengan Telegram Media Downloader melalui API Bridge Stage 2.x.

API yang sudah tersedia:

- Files
- Folder
- Share
- Trash
- Favorite
- Recent
- Collaboration

JANGAN:

- Jangan mengubah repository telegram-media-downloader.
- Jangan mengubah kontrak API Bridge Stage 2.x.
- Jangan mengubah endpoint yang sudah ada.
- Jangan mengubah request/response API.
- Jangan mengubah authentication.
- Jangan mengubah upload pipeline downloader.

Implementasi:

Bangun layer integrasi internal pada telegram-drive agar seluruh endpoint siap menerima request dari downloader.

Pastikan:

- seluruh endpoint memakai API Bridge yang sama
- validasi API Key
- Idempotency-Key
- retry policy
- standard response
- standard error
- logger
- metrics
- health check
- capability detection
- service registration

Lakukan verifikasi bahwa:

- Files API bekerja bersama Folder API
- Share API bekerja bersama Files API
- Trash API bekerja bersama Files API
- Favorite API bekerja bersama Files API
- Recent API otomatis ter-update saat file diakses
- Collaboration API menggunakan permission yang benar
- seluruh service memakai repository yang sama
- seluruh endpoint siap dipanggil downloader

Belum mengubah repository telegram-media-downloader.

Verifikasi:

npm run typecheck
npm run lint
npm test
npm run build

Output:

1. Ringkasan implementasi.
2. Diagram alur integrasi.
3. Hasil seluruh test.
4. Daftar file yang diubah.
5. Bagian yang tidak diubah.

WAJIB:

- Repository telegram-media-downloader tidak boleh diubah.
- Tahap ini hanya menyiapkan telegram-drive agar siap dihubungkan pada repository downloader pada tahap berikutnya.
```



# 
```
# Stage 3.6 — Collaboration API

Repository: telegram-drive
AI: AI A

Tujuan:
Membangun Collaboration API pada repository telegram-drive. Tahap ini hanya membangun REST API dan business logic agar siap dipanggil oleh Telegram Media Downloader pada tahap integrasi. Belum melakukan integrasi antar repository.

JANGAN:
- Jangan mengubah repository telegram-media-downloader.
- Jangan mengubah API Bridge Stage 2.x.
- Jangan mengubah Folder API Stage 3.1.
- Jangan mengubah Share API Stage 3.2.
- Jangan mengubah Trash API Stage 3.3.
- Jangan mengubah Favorite API Stage 3.4.
- Jangan mengubah Recent API Stage 3.5.
- Jangan mengubah upload pipeline.
- Jangan mengubah metadata sync.
- Jangan mengubah endpoint yang sudah ada.

Implementasi endpoint:

POST   /api/v1/collaborations
GET    /api/v1/collaborations
GET    /api/v1/collaborations/:id
PATCH  /api/v1/collaborations/:id
DELETE /api/v1/collaborations/:id

Fitur:

- Invite Collaborator
- Accept Collaboration
- Reject Collaboration
- Remove Collaborator
- Permission Management
- Read Only
- Read Write
- Owner Validation
- Duplicate Validation
- Status Pending / Accepted / Rejected

Model:

DriveCollaboration

Field minimal:

- id
- ownerId
- collaboratorId
- fileId
- permission
- status
- invitedAt
- acceptedAt
- createdAt
- updatedAt

Buat:

- Model
- Repository
- Service
- Route
- Validation
- Error Handling
- Logger
- Unit Test
- Integration Test
- README

Gunakan standar Stage 2.x:

- API Bridge v1
- X-API-Key
- Idempotency-Key
- Standard Success Response
- Standard Error Response

Validasi:

- hanya owner dapat mengundang collaborator
- collaborator tidak boleh ganda
- owner tidak dapat mengundang dirinya sendiri
- status hanya Pending, Accepted, Rejected
- permission hanya ReadOnly atau ReadWrite
- duplicate request menggunakan Idempotency-Key
- retry mengikuti kontrak Stage 2.x

Verifikasi:

npm run typecheck
npm run lint
npm test
npm run build

Output:

1. Ringkasan implementasi.
2. Daftar endpoint.
3. Struktur request/response.
4. Hasil unit test.
5. Hasil integration test.
6. Hasil build.
7. Daftar file yang dibuat/diubah.
8. Bagian yang TIDAK diubah.

WAJIB:
- Tidak menyentuh repository telegram-media-downloader.
- Tidak membuat integrasi antar repository.
- Tidak menghubungkan Downloader ke Collaboration API.
- Fokus hanya membangun Collaboration API pada repository telegram-drive agar siap dipanggil pada tahap integrasi berikutnya.
```


# 
```
# Stage 3.5 — Recent API

Repository: telegram-drive
AI: AI A

Tujuan:
Membangun Recent API pada repository telegram-drive. Tahap ini hanya membangun REST API dan business logic agar siap dipanggil oleh Telegram Media Downloader pada tahap integrasi. Belum melakukan integrasi antar repository.

JANGAN:
- Jangan mengubah repository telegram-media-downloader.
- Jangan mengubah API Bridge Stage 2.x.
- Jangan mengubah Folder API Stage 3.1.
- Jangan mengubah Share API Stage 3.2.
- Jangan mengubah Trash API Stage 3.3.
- Jangan mengubah Favorite API Stage 3.4.
- Jangan mengubah upload pipeline.
- Jangan mengubah metadata sync.
- Jangan mengubah endpoint yang sudah ada.

Implementasi endpoint:

POST   /api/v1/recents
GET    /api/v1/recents
DELETE /api/v1/recents

Fitur:

- Record Recent Activity
- List Recent Files
- Auto Update Last Access
- Auto Remove Duplicate
- Auto Cleanup (configurable)
- Sort by Latest Access
- Owner Validation

Model:

DriveRecent

Field minimal:

- id
- ownerId
- fileId
- lastAccessAt
- accessCount
- createdAt
- updatedAt

Buat:

- Model
- Repository
- Service
- Route
- Validation
- Error Handling
- Logger
- Unit Test
- Integration Test
- README

Gunakan standar Stage 2.x:

- API Bridge v1
- X-API-Key
- Idempotency-Key
- Standard Success Response
- Standard Error Response

Validasi:

- hanya owner dapat melihat recent miliknya
- akses file memperbarui lastAccessAt
- tidak boleh duplicate recent untuk file yang sama
- auto cleanup sesuai konfigurasi
- duplicate request menggunakan Idempotency-Key
- retry mengikuti kontrak Stage 2.x

Verifikasi:

npm run typecheck
npm run lint
npm test
npm run build

Output:

1. Ringkasan implementasi.
2. Daftar endpoint.
3. Struktur request/response.
4. Hasil unit test.
5. Hasil integration test.
6. Hasil build.
7. Daftar file yang dibuat/diubah.
8. Bagian yang TIDAK diubah.

WAJIB:
- Tidak menyentuh repository telegram-media-downloader.
- Tidak membuat integrasi antar repository.
- Tidak menghubungkan Downloader ke Recent API.
- Fokus hanya membangun Recent API pada repository telegram-drive agar siap dipanggil pada tahap integrasi berikutnya.
```

# 
```
# Stage 3.4 — Favorite API

Repository: telegram-drive
AI: AI A

Tujuan:
Membangun Favorite API pada repository telegram-drive. Tahap ini hanya membangun REST API dan business logic agar siap dipanggil oleh Telegram Media Downloader pada tahap integrasi. Belum melakukan integrasi antar repository.

JANGAN:
- Jangan mengubah repository telegram-media-downloader.
- Jangan mengubah API Bridge Stage 2.x.
- Jangan mengubah Folder API.
- Jangan mengubah Share API.
- Jangan mengubah Trash API.
- Jangan mengubah upload pipeline.
- Jangan mengubah metadata sync.
- Jangan mengubah endpoint yang sudah ada.

Implementasi endpoint:

POST   /api/v1/favorites
DELETE /api/v1/favorites/:fileId
GET    /api/v1/favorites

Fitur:

- Add Favorite
- Remove Favorite
- List Favorites
- Owner Validation
- Duplicate Validation
- Favorite Count
- Sort by Latest

Model:

DriveFavorite

Field minimal:

- id
- ownerId
- fileId
- createdAt
- updatedAt

Buat:

- Model
- Repository
- Service
- Route
- Validation
- Error Handling
- Logger
- Unit Test
- Integration Test
- README

Gunakan standar Stage 2.x:

- API Bridge v1
- X-API-Key
- Idempotency-Key
- Standard Success Response
- Standard Error Response

Validasi:

- hanya owner dapat menambah/menghapus favorite
- tidak boleh favorite ganda
- duplicate request menggunakan Idempotency-Key
- retry mengikuti kontrak Stage 2.x

Verifikasi:

npm run typecheck
npm run lint
npm test
npm run build

Output:

1. Ringkasan implementasi.
2. Daftar endpoint.
3. Struktur request/response.
4. Hasil unit test.
5. Hasil integration test.
6. Hasil build.
7. Daftar file yang dibuat/diubah.
8. Bagian yang TIDAK diubah.

WAJIB:
- Tidak menyentuh repository telegram-media-downloader.
- Tidak membuat integrasi antar repository.
- Tidak menghubungkan Downloader ke Favorite API.
- Fokus hanya membangun Favorite API pada repository telegram-drive agar siap dipanggil pada tahap integrasi berikutnya.
```

# Stage 3.3 (Trash API).
```
# Stage 3.3 — Trash API

Repository: telegram-drive
AI: AI A

Tujuan:
Membangun Trash API pada repository telegram-drive. Tahap ini hanya membangun REST API dan business logic agar siap dipanggil oleh Telegram Media Downloader pada tahap integrasi. Belum melakukan integrasi antar repository.

JANGAN:
- Jangan mengubah repository telegram-media-downloader.
- Jangan mengubah API Bridge Stage 2.x.
- Jangan mengubah Downloader.
- Jangan mengubah upload pipeline.
- Jangan mengubah metadata sync.
- Jangan mengubah Folder API Stage 3.1.
- Jangan mengubah Share API Stage 3.2.
- Jangan mengubah endpoint yang sudah ada.

Implementasi endpoint:

POST   /api/v1/files/:id/trash
POST   /api/v1/files/:id/restore
DELETE /api/v1/files/:id
GET    /api/v1/trash

Fitur:

- Move to Trash
- Restore
- Permanent Delete
- Soft Delete
- Owner Validation
- Restore Validation
- Permanent Delete Validation
- Trash Listing
- Deleted Time
- Restore Time

Model:

DriveTrash

Field minimal:

- id
- fileId
- ownerId
- deletedAt
- deletedBy
- restoredAt
- permanentlyDeleted
- createdAt
- updatedAt

Buat:

- Model
- Repository
- Service
- Route
- Validation
- Error Handling
- Logger
- Unit Test
- Integration Test
- README

Gunakan standar Stage 2.x:

- API Bridge v1
- X-API-Key
- Idempotency-Key
- Standard Success Response
- Standard Error Response

Validasi:

- hanya owner dapat menghapus
- restore hanya jika masih berada di Trash
- permanent delete tidak dapat di-restore
- duplicate request menggunakan Idempotency-Key
- retry mengikuti kontrak Stage 2.x

Verifikasi:

npm run typecheck
npm run lint
npm test
npm run build

Output:

1. Ringkasan implementasi.
2. Daftar endpoint.
3. Struktur request/response.
4. Hasil unit test.
5. Hasil integration test.
6. Hasil build.
7. Daftar file yang dibuat/diubah.
8. Bagian yang TIDAK diubah.

WAJIB:
- Tidak menyentuh repository telegram-media-downloader.
- Tidak membuat integrasi antar repository.
- Tidak menghubungkan Downloader ke Trash API.
- Fokus hanya membangun Trash API pada repository telegram-drive agar siap dipanggil pada tahap integrasi berikutnya.
```



# Prompt Stage 3.2 — Share API
```
# Stage 3.2 — Share API

Repository: telegram-drive
AI: AI A

Tujuan:
Membangun Share API pada repository telegram-drive. Tahap ini hanya membangun API dan business logic agar nantinya dapat dipanggil oleh Telegram Media Downloader. Belum melakukan integrasi antar repository.

JANGAN:
- Jangan mengubah repository telegram-media-downloader.
- Jangan mengubah API Bridge Stage 2.x.
- Jangan mengubah Downloader.
- Jangan mengubah upload pipeline.
- Jangan mengubah metadata sync.
- Jangan mengubah Folder API Stage 3.1.
- Jangan mengubah endpoint yang sudah ada.

Implementasi:

Endpoint:

POST   /api/v1/shares
GET    /api/v1/shares
GET    /api/v1/shares/:id
PATCH  /api/v1/shares/:id
DELETE /api/v1/shares/:id

Fitur:

- Public Share
- Private Share
- Password Protected
- Expired Link
- Unlimited Link
- Download Counter
- Owner Validation
- Permission Validation
- Share Token Generator
- Duplicate Validation

Model:

DriveShare

Field minimal:

- id
- ownerId
- fileId
- shareToken
- passwordHash
- permission
- expiresAt
- downloadCount
- createdAt
- updatedAt

Buat layer lengkap:

- Model
- Repository
- Service
- Controller/Route
- Validation
- Error Handling
- Logger
- Unit Test
- Integration Test
- README

Gunakan standar Stage 2.x:

- API Bridge v1
- X-API-Key
- Idempotency-Key
- Standard Success Response
- Standard Error Response

Validasi:

- owner hanya dapat mengubah share miliknya
- password di-hash
- token unik
- expired otomatis ditolak
- permission readonly
- duplicate request menggunakan Idempotency-Key
- retry mengikuti kontrak Stage 2.x

Verifikasi:

npm run typecheck
npm run lint
npm test
npm run build

Output yang diharapkan:

1. Ringkasan implementasi.
2. Daftar endpoint.
3. Struktur request/response.
4. Hasil unit test.
5. Hasil integration test.
6. Hasil build.
7. Daftar file yang dibuat/diubah.
8. Bagian yang TIDAK diubah.

WAJIB:
- Tidak menyentuh repository telegram-media-downloader.
- Tidak membuat integrasi antar repository.
- Tidak menghubungkan Downloader ke Share API.
- Fokus hanya membangun Share API di repository telegram-drive agar siap dipanggil pada tahap integrasi berikutnya.
```


# Stage 3.2 — Folder API Implementation
```
Repository:
telegram-drive

AI:
AI A

Stage:
3.2 - Folder API Implementation

Repository yang dikerjakan HANYA:
telegram-drive

Jangan mengubah repository telegram-media-downloader.

Tujuan tahap ini adalah mengimplementasikan Folder API yang nantinya dipanggil oleh Telegram Media Downloader melalui API Bridge.

Implementasikan:

1. Folder Model
- id
- ownerId
- parentFolderId
- name
- createdAt
- updatedAt

2. Folder Repository

3. Folder Service

4. Endpoint:

POST /api/v1/folders

GET /api/v1/folders

PATCH /api/v1/folders/:id

DELETE /api/v1/folders/:id

5. Validasi:
- nama folder
- parent folder
- owner
- duplicate folder pada parent yang sama

6. Mendukung struktur folder bertingkat.

7. Tambahkan Unit Test.

8. Tambahkan Integration Test.

9. Update README.

Jangan mengimplementasikan:

- Share
- Trash
- Favorite
- Recent
- Collaboration

Belum menghubungkan Downloader secara langsung.
Tahap ini hanya membangun Folder API agar siap dipanggil pada tahap integrasi berikutnya.

Pastikan:

npm run typecheck
npm run lint
npm test
npm run build

berhasil tanpa error.
```

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
