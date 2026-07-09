```

Lakukan audit menyeluruh pada project Telegram Drive.

Gejala:
- Backend Express berjalan normal.
- CSS bisa diakses (contoh: /css/styles.css mengembalikan HTTP 200).
- HTML juga bisa diakses.
- Namun saat membuka halaman utama, website tampil seperti HTML polos tanpa styling dan JavaScript tidak bekerja.

Tugas:

1. Audit seluruh frontend.
2. Temukan penyebab mengapa CSS/JS tidak diterapkan dengan benar.
3. Periksa seluruh path static Express.
4. Periksa semua link CSS dan JavaScript pada index.html serta semua halaman di folder public/pages.
5. Pastikan seluruh file JS dimuat tanpa error.
6. Pastikan tidak ada Content Security Policy atau konfigurasi Helmet yang memblokir asset.
7. Periksa console browser dan Network untuk semua asset yang gagal dimuat.
8. Perbaiki seluruh masalah sampai website tampil normal dengan CSS dan JavaScript aktif.
9. Jangan mengubah desain, layout, fitur, maupun backend API.
10. Setelah selesai, berikan daftar file yang diubah beserta alasan setiap perubahan.

Fokus hanya memperbaiki masalah frontend.

```
