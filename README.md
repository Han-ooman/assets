<p align="center">
  <img src="logo/logo.png" alt="SambasKu" width="320" />
</p>

# SambasKu Assets

Repositori **aset desain** untuk aplikasi **SambasKu**
(Kamus Digital Sambas-Indonesia). Isinya logo, maskot, animasi status,
dan tangkapan layar. Variasinya ikut dipakai situs web, aplikasi mobile,
dan konsol admin.

## Apa isi repo ini?

Berbeda dengan `audios/` dan `images/`, file di sini **di-commit manual**
oleh tim desain, bukan diunggah otomatis oleh backend. Tidak ada API yang
menulis ke repo ini, dan tidak ada baris database yang menunjuk ke file di
sini. Yang disimpan adalah sumber visual yang versioning-nya ikut Git.

| Folder | Isi |
| --- | --- |
| `svg/` | Logo vektor, varian terang dan gelap |
| `logo/` | Logo raster: ikon, horizontal, landscape, staging |
| `png/` | Maskot Paksamku |
| `gif/` | Animasi status (menunggu tinjauan, 404) |
| `features/` | Tangkapan layar fitur aplikasi |
| `concepts/` | Konsep logo |
| `images/` | Sampul |
| `v1/` | Aset rilis pertama (logo + tangkapan layar) |

Repo ini harus **publik** agar file asli bisa dimuat lewat **jsDelivr CDN**
(`cdn.jsdelivr.net/gh/…`) tanpa menarik aset build klien.

## Struktur path

```text
assets/
├── svg/
│   ├── logo_sambasku-light.svg
│   └── logo_sambasku-dark.svg
├── logo/
│   ├── logo.png
│   ├── logo_alpha_light.png
│   ├── logo_alpha_dark.png
│   ├── logo_horizontal_alpha_light.png
│   ├── logo_horizontal_alpha_dark.png
│   ├── logo_landscape.png
│   └── logo_staging.png
├── png/
│   ├── PakSamku.png
│   ├── PakSamKu_blue.png
│   └── Paksamku_pakaipakaian_adat.png
├── gif/
│   ├── Menunggu_Tinjauan.gif             # latar terang
│   ├── Menunggu_Tinjauan_darkmode.gif    # latar gelap
│   ├── 404_warning_white.gif             # latar terang
│   └── 404_warning_black.gif             # latar gelap
├── features/
│   ├── 1.jpg … 6.jpg                     # tangkapan potret
│   └── landscape.png
├── concepts/
│   └── Logo_Sambas-02.jpg … Logo_Sambas-04.jpg
├── images/
│   ├── cover.png
│   └── cover.webp
└── v1/
    ├── logo.webp
    └── screenshots/
        └── 1.jpeg
```

- Penamaan file lama belum seragam: campuran PascalCase dan snake_case,
  dan `Paksamku_pakaipakaian_adat.png` masih salah ketik (`pakaip`).
  File baru pakai **snake_case** tanpa spasi.
- Animasi status punya **sepasang varian**, terang dan gelap.
  `Menunggu_Tinjauan_*` menandai mode lewat nama file (`_darkmode`).
  `404_warning_*` memakai `white` / `black`, yang menunjuk warna latar,
  bukan nama mode. Status baru: pilih satu pola dan konsisten.
- Latar GIF gelap mendekati permukaan gelap web, bukan hitam murni:
  `Menunggu_Tinjauan_darkmode.gif` `#2A2A2A`,
  `404_warning_black.gif` `#2E2C2E`. Kalau latar web berubah, GIF gelap
  perlu diekspor ulang. Warna teksnya ikut terkunci ke latar lama.
- Jangan menimpa file yang sudah dipakai klien. Tambah file baru, lalu
  arahkan pemakai ke nama baru supaya histori tetap bisa dirujuk.

## URL publik (dipakai client)

Klien tidak menarik file master ke dalam build. Tiap aset dijadikan
turunan (ukuran dan format sesuai target), lalu dilayani sebagai aset
build. URL jsDelivr menyajikan file asli bila dibutuhkan:

```text
https://cdn.jsdelivr.net/gh/sambasku/assets@main/<path>
```

| Sumber | Turunan di klien | Dipakai di |
| --- | --- | --- |
| `svg/logo_sambasku-light.svg`, `svg/logo_sambasku-dark.svg` | `logo_hor_light.webp`, `logo_hor_dark.webp` | web |
| `logo/` | `assets/icons/` (ikon, horizontal, staging) | mobile |
| logo terang | `logo_white.webp` | console |
| `png/Paksamku_pakaipakaian_adat.png` | `paksamku-maskot-pakaian-adat-melayu.webp` | web |

Maskot pakaian adat hanya dipakai web, pada kartu **Kata Hari Ini**
(`word-of-the-day-card.tsx`): tinggi `30rem`, disembunyikan di bawah
`62em` (Mantine `md`) karena ruang vertikal mobile terlalu sempit.
Teks alt-nya di i18n (`home_wotdMascotAlt`), dialek `id` dan `id-SBS`.

Keempat GIF di `gif/` belum terpasang di klien mana pun.

## Yang tidak dilakukan di repo ini

- Bukan repo media pengguna. Gambar kata, avatar, dan bukti lampiran
  milik `images/`.
- Bukan repo audio. Pelafalan milik `audios/`.
- Tidak ada alur upload. Perubahan lewat commit.
- Jangan rename / pindah file yang sudah disalin ke aset build klien.
  Path CDN dan path build akan putus.

## Lisensi

Aset dan dokumentasi repo ini dilisensikan di bawah **MIT** - lihat
[`LICENSE`](./LICENSE).

Logo dan maskot adalah identitas SambasKu.
