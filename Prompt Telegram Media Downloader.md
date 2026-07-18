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
