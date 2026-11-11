# Buku Tapak (PWA)

App boleh di-install di telefon tanpa claude.ai. Fail: index.html, config.js, manifest.webmanifest, sw.js, icon-192.png, icon-512.png.

## 1. Letak di internet (percuma, pilih satu)
App PWA mesti dihos melalui HTTPS.
- **GitHub Pages (disyorkan, boleh buat dari telefon)**:
  1. Log masuk github.com, tekan New repository, namakan `buku-tapak`, pilih Public, Create.
  2. Extract zip ini dulu (guna app Files). Dalam repo, tekan Add file, Upload files, pilih semua 8 fail dalam folder, kemudian Commit changes. Kalau pilihan tak nampak, buka menu browser dan pilih Desktop site.
  3. Settings, Pages, Source: Deploy from a branch, Branch: main, folder / (root), Save.
  4. Tunggu 1 hingga 2 minit. Link app: `https://NAMA-GITHUB-AWAK.github.io/buku-tapak/`
  Nota: link GitHub Pages boleh dibuka oleh sesiapa yang ada link. Tanpa Firebase, data kekal pada telefon masing-masing.
- **Netlify Drop**: buka app.netlify.com/drop, seret folder ini. Siap, dapat link.
- **Cloudflare Pages** atau **GitHub Pages**: muat naik semua fail dalam folder ini.
- **Firebase Hosting**: `firebase deploy --only hosting` (kalau dah guna Firebase untuk team).

## 2. Install di telefon
- **Android (Chrome)**: buka link, tekan butang "Install app" dalam app, atau menu titik tiga, "Install app".
- **iPhone (Safari)**: tekan Share, kemudian "Add to Home Screen".
Selepas install, app boleh dibuka tanpa internet. Data disimpan pada telefon.

## 3. Kongsi data dengan team (Firebase, percuma pada pelan Spark)
1. Pergi console.firebase.google.com, Create project.
2. Build, Authentication, Get started, Sign-in method: aktifkan **Anonymous**.
3. Build, Firestore Database, Create database (mod production). Tab Rules: tampal isi `firestore.rules`, Publish.
4. Project settings, Your apps, ikon web (</>), daftar app. Salin objek `firebaseConfig`.
5. Buka `config.js`, tampal ke `firebase:{...}`, hos semula.
6. Dalam app, tekan **Kod team**, masukkan kod yang sama untuk semua ahli (guna kod panjang dan rawak, ia berfungsi macam kata laluan).
7. Authentication, Settings, Authorized domains: pastikan domain app anda ada.

Gambar dimampat (di bawah 600KB) dan disimpan dalam Firestore supaya team nampak. Data lama pada peranti dihantar ke team secara automatik pada sambungan pertama.

## Nota
- Sesiapa yang tahu kod team boleh baca dan tulis data team. Jangan kongsi kod di tempat awam.
- Export Excel terus dimuat turun sebagai fail .xlsx (perlu internet buat kali pertama untuk muat library).
- Untuk kemas kini app, hos semula dan ubah `V` dalam sw.js (cth bt-v2).
