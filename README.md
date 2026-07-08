```

# Telegram Drive - Tahap 1 (Fondasi Project)

Buat project baru dari nol bernama **Telegram Drive**.

Jangan menggunakan kode dari project lama. Semua struktur harus baru, rapi, scalable, mudah dikembangkan, dan mengikuti best practice.

## Tujuan Tahap 1

Tahap ini hanya membuat pondasi project.

Belum membuat fitur upload, download, search, preview, ataupun website download.

Fokus pada struktur project, backend, frontend, admin panel, database, dan koneksi bot Telegram.

---

# Teknologi

Backend
- Node.js
- Express.js
- MongoDB (Mongoose)
- Telegraf
- JWT
- dotenv
- cors
- helmet
- morgan
- compression
- cookie-parser

Frontend
- React
- Vite
- Tailwind CSS
- React Router

Deployment
- Ubuntu VPS
- PM2
- Nginx

---

# Struktur Project

telegram-drive/

backend/

frontend/

admin/

docs/

README.md

.gitignore

---

Backend harus dipisahkan menjadi

src/

config/

controllers/

middleware/

models/

routes/

services/

bot/

utils/

public/

app.js

server.js

---

Frontend menggunakan React + Vite.

Admin panel juga React + Vite.

Frontend dan admin benar-benar terpisah.

---

# Database MongoDB

Siapkan collection

users

admins

files

folders

downloads

settings

logs

Belum perlu diisi data.

---

# Authentication

Siapkan sistem login admin menggunakan JWT.

Belum perlu halaman login yang lengkap.

Cukup endpoint login dan middleware auth.

---

# REST API

Buat struktur route

/api/auth

/api/files

/api/folders

/api/users

/api/admin

/api/settings

Semua route masih boleh mengembalikan response JSON sederhana.

---

# Telegram Bot

Gunakan Telegraf.

Bot harus dapat dijalankan bersamaan dengan backend.

Ketika backend berjalan:

Bot otomatis aktif.

Ketika user mengetik

/start

Bot membalas

"Telegram Drive sedang dalam tahap pengembangan."

Belum perlu fitur upload.

---

# Environment

Gunakan file .env

Contoh isi

PORT=

MONGO_URI=

BOT_TOKEN=

JWT_SECRET=

ADMIN_USERNAME=

ADMIN_PASSWORD=

DOMAIN=

---

# Error Handler

Buat middleware

404 handler

Global Error Handler

---

# Logging

Gunakan morgan.

Semua request tercatat.

---

# Security

Gunakan

Helmet

CORS

Compression

Rate Limit

---

# Folder Docs

Buat folder docs.

Isi dengan dokumentasi singkat project.

---

# README

Buat README lengkap berisi

Cara install

Cara menjalankan

Cara build

Cara deploy VPS

Cara menjalankan PM2

Cara konfigurasi Nginx

Cara mengisi .env

Struktur folder

Penjelasan setiap folder

Roadmap project

---

# Coding Style

Gunakan ES Modules.

Gunakan async/await.

Tidak boleh ada callback lama.

Semua file diberi komentar singkat.

Semua fungsi dipisahkan ke folder masing-masing.

---

# Output

Hasil akhir harus berupa project yang langsung bisa dijalankan menggunakan

npm install

npm run dev

tanpa error.

Belum membuat fitur upload.

Belum membuat website download.

Belum membuat search.

Belum membuat preview.

Belum membuat admin dashboard.

Fokus hanya membuat pondasi project yang bersih, modern, dan siap dikembangkan ke Tahap 2.


```
