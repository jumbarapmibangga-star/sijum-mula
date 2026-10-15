# Sistem Penjurian & PWA Jumbara PMR Mula

Sistem penilaian digital multi-pos berbasis PWA (Progressive Web App), Google Apps Script API, Google Sheets Database, serta Direct Thermal Bluetooth Printing (RPP02N).

## File dalam Repositori
- `Code.gs` : Kode Apps Script Backend untuk ditaruh di Google Sheets (Extensions > Apps Script).
- `manifest.json` : Konfigurasi PWA Web App Manifest.
- `sw.js` : Service Worker PWA.
- `index.html` : Aplikasi HP untuk 50 Juri (Login PIN, Dynamic Rubrik, Bluetooth Print, Anti-Double Input).
- `dashboard.html` : Tampilan Layar Lebar TV / Proyektor (Live Leaderboard Juara Umum, Top 3 Pos, & Tracking Progress).

## Panduan Singkat Implemetasi

### 1. Google Sheets Setup
Buat tab-tab berikut:
1. `KONTINGEN` -> `ID_KONTINGEN`, `NAMA_TIM`, `KECAMATAN`
2. `JURI` -> `ID_JURI`, `NAMA_JURI`, `PIN`, `KODE_POS`
3. `POS` -> `KODE_POS`, `NAMA_POS`, `SKOR_MAKSIMAL`
4. `RUBRIK` -> `KODE_POS`, `NAMA_ITEM`, `BOBOT_MAKS`
5. `NILAI` -> `TIMESTAMP`, `NAMA_JURI`, `POS_LOMBA`, `KONTINGEN`, `TOTAL_SKOR`, `DURASI_DETIK`, `CATATAN`, `DETAIL_RUBRIK_JSON`
6. `JUARA_POS` -> Masukkan rumus QUERY per pos
7. `JUARA_UMUM` -> Masukkan rumus QUERY akumulasi total skor (LIMIT 3)

### 2. Deploy Apps Script
1. Buka `Extensions` > `Apps Script` pada Google Sheets.
2. Salin kode `Code.gs` ke editor.
3. Klik `Deploy` > `New deployment` > `Web app`.
4. Set `Execute as: Me`, `Who has access: Anyone`.
5. Salin URL Web App yang dihasilkan.

### 3. Update URL di HTML
Buka file `index.html` dan `dashboard.html`, ganti variabel `GAS_API_URL` dengan URL Web App Apps Script.

### 4. Upload ke GitHub & Vercel
1. Upload `manifest.json`, `sw.js`, `index.html`, `dashboard.html` ke Repositori GitHub (`portal-juri`).
2. Aktifkan GitHub Pages (Settings > Pages > Branch `main`).
3. Import Repositori GitHub ke Vercel untuk link hosting utama.
