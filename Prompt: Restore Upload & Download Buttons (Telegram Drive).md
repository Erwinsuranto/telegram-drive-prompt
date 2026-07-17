










# 
```

Perbaiki fungsi tombol Download pada Action Menu di halaman My Files.

Saat ini terjadi bug:

- Klik tombol titik tiga (⋮).
- Muncul Action Menu.
- Klik Download.
- Action Menu hanya tertutup dan kembali ke daftar file.

Ini salah.

Perilaku yang benar:

1. Klik ⋮.
2. Klik Download.
3. Tutup Action Menu.
4. Langsung navigasi ke halaman Download file.

Contoh:
GET /download/{downloadToken}
atau route download yang digunakan aplikasi.

Halaman Download harus:
- menampilkan nama file,
- ukuran file,
- tipe file,
- tombol Download,
- tombol Copy Link,
- tombol Share.

Jangan melakukan download langsung dari Action Menu.

Action Menu hanya melakukan navigasi ke halaman Download.

Pastikan tombol Download benar-benar menjalankan router.push() atau Link ke halaman Download menggunakan downloadToken/fileId yang benar.

Verifikasi:
- Download dari My Files berhasil.
- Download dari halaman Upload berhasil.
- Download dari halaman Share berhasil.
- Tidak ada lagi kasus tombol Download hanya menutup popup.




```
# 
```


Perbaiki UX halaman My Files agar mengikuti pola Google Drive dan MEGA.

Saat ini perilakunya salah.

Yang diinginkan:

1. Klik nama file, thumbnail, atau seluruh area file
- Jangan membuka panel informasi.
- Langsung buka halaman Preview File.
- Jika gambar:
  tampilkan image viewer.
- Jika video:
  tampilkan video player.
- Jika PDF:
  tampilkan PDF viewer.
- Jika audio:
  tampilkan audio player.
- Jika file lain:
  tampilkan halaman detail dengan ikon file.

Halaman preview harus memiliki tombol:
- Download
- Copy Link
- Share
- Informasi File

2. Tombol titik tiga (⋮)
JANGAN membuka panel informasi seperti sekarang.

Harus membuka Action Menu seperti Google Drive atau MEGA.

Isi menu:

• Preview / Open
• Download
• Copy Link
• Share
• Rename (admin)
• Move
• Delete (admin)
• Favorite
• Detail / Properties

Menu ditampilkan sebagai bottom sheet atau popup menu.

3. Pisahkan Preview dan Action Menu.

Preview adalah halaman untuk membuka isi file.

Action Menu hanya berisi aksi terhadap file.

Jangan mencampur keduanya.

4. Panel informasi yang sekarang muncul dari bawah dihapus.

Informasi file dipindahkan ke menu:
Detail / Properties.

5. Semua tombol harus berfungsi:
- Preview
- Download
- Copy Link
- Share
- Detail

6. Pastikan seluruh perilaku bekerja baik di desktop maupun mobile.

Jangan mengubah desain Telegram Drive selain memperbaiki alur interaksi ini.



```

# Prompt 2 - Tombol Download tidak berfungsi
```


Perbaiki tombol "Download" pada panel detail file.

Masalah:
- Tombol Download dapat ditekan tetapi tidak melakukan apa pun.

Yang diinginkan:
1. Saat tombol Download ditekan, file langsung mulai diunduh.
2. Gunakan downloadToken yang tersimpan di database.
3. Jangan membuka halaman kosong.
4. Jangan menampilkan error di browser.
5. Pastikan download berhasil untuk semua tipe file.
6. Jangan mengubah tampilan tombol.



```
# Prompt 1 (Prioritas) - Nama file harus bisa ditekan
```


Perbaiki interaksi pada halaman "My Files".

Masalah saat ini:
1. Nama file tidak bisa ditekan.
2. Thumbnail/icon file juga tidak bisa ditekan.
3. Pengguna harus menekan tombol titik tiga terlebih dahulu untuk melihat detail file.

Yang diinginkan:
- Seluruh area item file (thumbnail, nama file, dan informasi file) harus bisa ditekan.
- Saat ditekan, langsung buka panel/detail file seperti yang sekarang muncul dari tombol titik tiga.
- Tombol titik tiga tetap dipertahankan untuk menu tambahan.
- Jangan mengubah tampilan desain yang sudah ada.
- Pastikan berfungsi di desktop dan mobile.



```
# Prompt 1 – Tombol "Open File" salah (Prioritas 1)
```


Perbaiki fitur "Open File" setelah upload berhasil.

Masalah saat ini:
- Setelah upload selesai, tombol "Open File" langsung mengunduh file.
- Seharusnya tombol ini membuka halaman preview/detail file, bukan langsung mengunduh.

Yang diinginkan:
1. Tombol "Open File" membuka halaman detail file menggunakan downloadToken atau fileId.
2. Halaman tersebut menampilkan:
   - Nama file
   - Ukuran file
   - Tanggal upload
   - Preview (jika gambar/video/PDF)
   - Tombol Download
   - Tombol Copy Link
   - Informasi file
3. File hanya diunduh jika pengguna menekan tombol Download.
4. Jangan mengubah alur upload yang sudah berjalan.
5. Pastikan link yang dibuka menggunakan downloadToken yang sama dengan database.



```
# Prompt 2 – Tombol "Copy Link" tidak berfungsi (Prioritas 2)

```

Perbaiki tombol "Copy Link".

Masalah:
- Tombol dapat ditekan tetapi tidak menyalin apa pun ke clipboard.

Yang diinginkan:
1. Tombol harus menyalin link download lengkap.
2. Contoh:
http://domain/download/{downloadToken}

3. Setelah berhasil:
- tampilkan toast:
"Link berhasil disalin."

4. Jika clipboard gagal:
- tampilkan pesan error yang jelas.

5. Jangan mengubah tampilan tombol.
6. Pastikan link yang disalin sama dengan link yang digunakan halaman download






```
# Prompt 3 – Pisahkan halaman Upload dan Download (Prioritas 3)
```


Pisahkan halaman Upload dan halaman Download.

Masalah saat ini:
Halaman Upload masih menampilkan form Download sehingga pengguna bingung.

Yang diinginkan:

Halaman Upload (/upload):
- Hanya berisi fitur upload.
- Daftar upload.
- Progress upload.
- Hasil upload.
- Tidak boleh ada form download.

Halaman Download (/download):
- Halaman khusus download.
- Memiliki input downloadToken atau link.
- Jika pengguna menempel link atau token lalu menekan Download, langsung diarahkan ke halaman detail file.
- Halaman detail menampilkan preview file, informasi file, dan tombol Download.

Pastikan:
- Upload dan Download menjadi dua halaman yang benar-benar terpisah.
- Semua route lama tetap kompatibel.
- Jangan mengubah desain yang sudah ada.



```


#
```

Perbaiki menu sidebar (drawer) pada tampilan mobile.

Masalah yang terjadi:

1. Setelah menu (drawer) terbuka, pengguna tidak bisa menutupnya dengan menekan area kosong di luar menu.
2. Overlay/backdrop tidak menutupi seluruh layar sehingga klik pada area luar tidak menutup menu.
3. Tombol menu (hamburger) terlihat tidak menyatu dengan drawer sehingga setelah drawer terbuka tombol tersebut tidak berfungsi sebagai toggle.
4. Pengguna seperti terjebak di dalam menu karena tidak ada cara untuk kembali selain me-refresh halaman.

Yang harus diperbaiki:

- Gunakan satu state yang sama untuk mengatur buka/tutup drawer.
- Tambahkan backdrop/overlay yang menutupi seluruh layar.
- Overlay harus berada di bawah drawer tetapi di atas seluruh konten halaman.
- Menekan area overlay harus langsung menutup drawer.
- Menekan tombol hamburger lagi juga harus menutup drawer (toggle).
- Tekan tombol Escape pada desktop juga harus menutup drawer.
- Saat drawer terbuka, body tidak boleh bisa di-scroll.
- Drawer tetap slide dari kiri seperti sekarang.
- Pastikan z-index drawer lebih tinggi daripada overlay.
- Jangan mengubah tampilan desktop.
- Jangan mengubah desain atau warna menu.

Lakukan pengecekan setelah selesai:

✓ Menu dapat dibuka.
✓ Menu dapat ditutup dengan menekan area kosong.
✓ Menu dapat ditutup dengan tombol hamburger.
✓ Tidak ada area yang membuat pengguna terjebak.
✓ Berfungsi dengan baik di Android Chrome dan browser mobile lainnya.
✓ Pastikan tidak ada regresi pada fitur lain.




```
# Prompt: Fix Mobile Layout Overlap (Telegram Drive)
```


You are a senior Next.js + React + Tailwind CSS engineer.

The mobile UI has serious layout issues.

Current problems:

1. "Shared with me" and "Collaborate" chips overlap the Telegram Drive header.
2. The slide menu overlaps the My Files page content.
3. Header spacing is incorrect on mobile.
4. Navigation drawer is not positioned correctly.
5. Elements stack on top of each other.

Your task is to fix the layout WITHOUT changing backend logic.

Requirements

## Header

- Telegram Drive logo must always be fully visible.
- Header must never be covered.
- Respect mobile safe-area.
- Add correct top spacing.

## Shared with me

- Remove floating position.
- Never render above the header.
- If these buttons are part of the file toolbar, move them below the page title.
- Otherwise hide them on mobile.

## Side Menu

When menu opens:

- Display as a Drawer.
- Slide from the right.
- Position: fixed.
- Top aligned below the header.
- Height:
  calc(100vh - headerHeight)

The drawer must never cover:

- Header
- Search box
- My Files title

Instead:

Overlay only page content.

## Z-index

Create a clean layer order.

Header
z-50

Drawer
z-40

Content
z-10

Floating buttons
z-20

Never use random z-index values.

## My Files

Keep layout:

Header

↓

Toolbar

↓

Search

↓

Sort

↓

Files

↓

Floating buttons

Nothing may overlap.

## Mobile

Test widths:

320px

360px

390px

412px

430px

768px

No horizontal scrolling.

No overlapping.

No clipped content.

## CSS

Remove any:

position:absolute

negative margin

translateY hacks

hardcoded top values

that cause overlap.

Use flex/grid and proper spacing instead.

## Final verification

✓ Header always visible

✓ Shared with me no longer overlaps

✓ Drawer opens correctly

✓ Drawer does not cover header

✓ My Files layout clean

✓ Upload button still works

✓ Responsive

✓ No TypeScript errors

Output:

- Every modified file.
- Root cause.
- Exact fixes applied.
- Before/after explanation.



```
#Prompt: Restore Upload & Download Buttons (Telegram Drive)
```


You are a senior Next.js + React + Tailwind engineer.

The Upload page was accidentally modified.

Current situation:
- Route /upload still works.
- The page title "Upload" is visible.
- Description "Choose My Files to manage uploads." is visible.
- However, the Upload and Download buttons have disappeared.

Your task is to restore the previous functionality WITHOUT changing any existing backend logic.

Requirements:

1. Restore the Upload button.
   - Large primary button.
   - Opens file picker.
   - Supports drag & drop.
   - Uses existing upload API.
   - Show upload progress.
   - Mobile friendly.

2. Restore the Download button.
   - Display directly below Upload (not on the same row).
   - Use existing download logic.
   - Keep previous styling if available.
   - Mobile friendly.

3. Do NOT create new APIs.
   Use existing upload/download functions.

4. Search the project for previous Upload and Download components.
   Reuse them instead of rewriting.

5. If the buttons disappeared because of conditional rendering:
   - Fix the condition.
   - Remove incorrect hidden state.
   - Ensure buttons always appear.

6. If the buttons disappeared because of CSS:
   - Restore visibility.
   - Remove display:none, hidden, invisible or opacity issues.

7. Keep current design.
   Do not redesign the page.

8. Verify:
   ✓ Upload button visible.
   ✓ Download button visible.
   ✓ Upload works.
   ✓ Download works.
   ✓ Responsive on mobile.
   ✓ No TypeScript or ESLint errors.

Before finishing:
- Search git history if available.
- Search all Upload page commits.
- Restore missing JSX instead of creating fake placeholders.

Output:
- List every modified file.
- Explain why the buttons disappeared.
- Show the exact fix.



```
