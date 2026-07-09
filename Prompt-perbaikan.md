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
