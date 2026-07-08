```

# Telegram Drive - Tahap 1 (Project Foundation)

Buat project baru dari nol dengan nama **Telegram Drive**.

Jangan menggunakan kode dari project lama.

## Tujuan

Tahap ini hanya membangun pondasi project.

Belum membuat fitur upload, download, search, preview, ataupun dashboard.

Fokus hanya membuat struktur project yang bersih, modern, scalable, dan mudah dikembangkan.

---

## Teknologi

Backend
- Node.js
- Express.js
- MongoDB (Mongoose)
- dotenv
- cors
- helmet
- compression
- morgan
- express-rate-limit
- cookie-parser
- bcrypt
- jsonwebtoken

Frontend
- React
- Vite
- Tailwind CSS
- React Router

Deployment
- Ubuntu
- PM2
- Nginx / 9router

---

## Struktur Project

telegram-drive/

backend/

frontend/

admin/

docs/

scripts/

README.md

.gitignore

docker-compose.yml

---

## Backend

Buat struktur berikut

src/

config/

controllers/

middleware/

models/

routes/

services/

utils/

bot/

public/

app.js

server.js

---

## Frontend

Gunakan React + Vite.

Belum membuat halaman.

Cukup siapkan struktur project.

---

## Admin

Gunakan React + Vite.

Belum membuat dashboard.

---

## Database

Siapkan koneksi MongoDB.

Belum membuat collection.

---

## Environment

Buat

.env

.env.example

Berisi

PORT

MONGO_URI

JWT_SECRET

BOT_TOKEN

DOMAIN

---

## API

Buat endpoint

GET /

GET /health

Response:

{
  "success": true,
  "message": "Telegram Drive API Running"
}

---

## Telegram Bot

Hubungkan bot Telegram.

Command

/start

Response

Telegram Drive sedang dalam tahap pengembangan.

Belum membuat upload.

---

## Logging

Gunakan Morgan.

---

## Security

Helmet

CORS

Compression

Rate Limit

---

## Error Handler

404 Handler

Global Error Handler

---

## README

Isi:

Cara Install

Cara Menjalankan

Struktur Folder

Roadmap Project

Cara Deploy

Cara Menjalankan PM2

Konfigurasi Nginx / 9router

---

## Rules

Gunakan ES Modules.

Gunakan async/await.

Semua kode modular.

Semua fungsi dipisahkan.

Semua konfigurasi berada di folder config.

Jangan membuat fitur Authentication.

Jangan membuat Login.

Jangan membuat Upload.

Jangan membuat Download.

Jangan membuat Search.

Jangan membuat Preview.

Jangan membuat Dashboard.

Fokus hanya Foundation.

---

## Output

Project harus dapat dijalankan menggunakan

npm install

npm run dev

tanpa error.

Berikan daftar file yang dibuat dan struktur folder lengkap setelah selesai.


```

```
