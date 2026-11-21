# Smart Irrigation – Widget Blynk

Antarmuka web (HTML satu file) untuk memantau dan mengendalikan sistem **Smart Irrigation ESP32 + Blynk**.
Dipasang di aplikasi Blynk lewat widget **Web Page**, atau dibuka langsung di browser HP.

## Fitur
- Beranda: suhu, kelembapan udara, kelembapan tanah, level air tangki, status pompa
- Kendali pompa langsung (ON/OFF) dan pilihan mode **Auto / Manual / Jadwal**
- Pengaturan batas nyala, jeda, jadwal 1 dan 2, kalibrasi sensor, ambang peringatan
- Status event: air habis, tanah kering, suhu tidak wajar, WiFi terputus
- Mode demo (tanpa token) untuk mencoba tampilan

## Cara pakai
Buka alamat situs dengan token dan server Blynk Anda:

```
https://USERNAME.github.io/smart-irrigation/?token=TOKEN_ANDA&server=sgp1.blynk.cloud
```

- `token`  : Auth Token perangkat (Blynk Console → Devices → Device Info)
- `server` : sesuai region akun (`blynk.cloud`, `sgp1.blynk.cloud`, `blr1.blynk.cloud`, `fra1.blynk.cloud`, `lon1.blynk.cloud`, `ny3.blynk.cloud`)

Tanpa token, widget berjalan di **mode demo**. Token juga bisa diisi lewat ikon ⚙️ di pojok kanan atas.

> **Jangan menulis token di repository ini.** Token hanya ada di link yang Anda pakai sendiri.

## Data stream (harus sama dengan firmware)

| Pin | Fungsi | Tipe | Rentang |
|---|---|---|---|
| V0 | Suhu | Double | 0–60 |
| V1 | Kelembapan udara | Double | 0–100 |
| V2 | Kelembapan tanah | Integer | 0–100 |
| V3 | Ketinggian air | Integer | 0–100 |
| V4 | Indikator air habis | Integer | 0–255 |
| V5 | Pompa ON/OFF | Integer | 0–1 |
| V6 | Kondisi tanah | String | |
| V7 | Peringatan air | String | |
| V8 | Mode (0 Auto, 1 Manual, 2 Jadwal) | Integer | 0–2 |
| V9 / V11 | Jam jadwal 1 / 2 (detik sejak 00:00) | String | |
| V10 / V12 | Durasi jadwal 1 / 2 (menit) | Integer | 1–240 |
| V13 / V14 | Aktif jadwal 1 / 2 | Integer | 0–1 |
| V15 | Jam alat | String | |
| V16 | Maks. nyala mode Auto (detik) | Integer | 0–21600 |
| V17 | Jeda mode Auto (menit) | Integer | 0–1440 |
| V18 | Status jeda | String | |
| V19 | Maks. nyala mode Manual (menit) | Integer | 0–240 |
| V20 / V21 | Jarak sensor tangki penuh / habis (cm) | Double | 2–400 |
| V22 / V23 | Offset suhu / kelembapan DHT22 | Double | ±20 / ±30 |
| V24 | Ambang tanah kering (%) | Integer | 1–95 |
| V25 / V26 | Batas suhu rendah / tinggi (°C) | Double | 0–60 |
| V27 | Tunda WiFi terputus (detik) | Integer | 5–3600 |
| V28 | Jeda ulang pengingat (menit) | Integer | 0–1440 |
| V29 / V30 / V31 | Aktif event tanah kering / suhu / WiFi | Integer | 0–1 |

Event Blynk (kode harus persis): `air_habis`, `tanah_kering`, `suhu_tidak_wajar`, `wifi_terputus`.

## Publikasi (GitHub Pages)
Settings → Pages → Deploy from a branch → `main` → `/ (root)` → Save.
