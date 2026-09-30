<p align="center">
  <img src="svg/logo_sambasku.svg" alt="SambasKu" width="320" />
</p>

# SambasKu Assets

Repositori **aset desain** untuk aplikasi **SambasKu** (Kamus Digital
Sambas-Indonesia). Isinya logo, maskot, dan animasi status. Variasinya
ikut dipakai situs web, aplikasi mobile, dan konsol admin.

## Apa isi repo ini?

Berbeda dengan `audios/` dan `images/`, file di sini **di-commit manual**
oleh tim desain — bukan diunggah otomatis oleh backend. Tidak ada API yang
menulis ke repo ini, dan tidak ada baris database yang menunjuk ke file di
sini. Yang disimpan adalah sumber visual yang versioning-nya ikut Git.

| Jenis | Isi |
| ----- | --- |
| `svg/` | Logo horizontal (vektor) |
| `png/` | Maskot Paksamku |
| `gif/` | Animasi status (menunggu tinjauan, 404) |

## Struktur path

```text
assets/
├── svg/
│   └── logo_sambasku.svg
├── png/
│   ├── PakSamku.png                    # maskot polos
│   └── Paksamku_pakaipakaian_adat.png # maskot berpakaian adat
└── gif/
    ├── Menunggu_Tinjauan.gif           # light mode
    ├── Menunggu_Tinjauan_darkmode.gif  # dark mode
    ├── 404_warning_white.gif           # light mode
    └── 404_warning_black.gif           # dark mode
```

## Ukuran & format

| File | Ukuran | Format |
| ---- | ------ | ------ |
| `svg/logo_sambasku.svg` | 2000 × 522 | SVG (vektor) |
| `png/PakSamku.png` | 1000 × 1000 | PNG RGBA |
| `png/Paksamku_pakaipakaian_adat.png` | 1000 × 1000 | PNG RGBA |
| `gif/Menunggu_Tinjauan.gif` | 600 × 400 | GIF 89a |
| `gif/Menunggu_Tinjauan_darkmode.gif` | 600 × 400 | GIF 89a |
| `gif/404_warning_white.gif` | 400 × 400 | GIF 89a |
| `gif/404_warning_black.gif` | 400 × 400 | GIF 89a |

## Dipakai di aplikasi

Klien tidak menarik file langsung dari repo ini. Setiap aset dijadikan
turunan dengan format dan ukuran sesuai target, lalu dilayani sebagai
aset build.

| Aset di repo ini | Bentuk turunan | Dipakai di |
| --------------- | -------------- | ----------- |
| `svg/logo_sambasku.svg` | `logo_hor_light.webp`, `logo_hor_dark.webp` | web |
| `svg/logo_sambasku.svg` | `logo_horizontal_light.png`, `logo_horizontal_dark.png` | mobile |
| `svg/logo_sambasku.svg` | `logo_white.webp` | console |
| `png/Paksamku_pakaipakaian_adat.png` | `paksamku-maskot-pakaian-adat-melayu.webp` | web |

Logo dipakai ketiga klien, masing-masing dalam format dan ukuran yang
cocok untuk targetnya. Maskot **hanya** dipakai web, pada kartu **Kata
Hari Ini** (`word-of-the-day-card.tsx`): tinggi `30rem`, disembunyikan di
bawah `62em` (Mantine `md`) karena ruang vertikal mobile terlalu sempit.
Teks alt-nya di i18n (`home_wotdMascotAlt`) dalam dua dialek, `id` dan
`id-SBS`.

Keempat GIF di `gif/` **belum** terpasang di klien mana pun. Status
"menunggu tinjauan" dan 404 sudah ada gambarnya, tinggal disambungkan.

Repo ini tetap **publik** supaya jsDelivr bisa menyajikan file asli bila
dibutuhkan tanpa menarik image build:

```text
https://cdn.jsdelivr.net/gh/sambasku/assets@main/<path>
```

## Aturan pemakaian

- Penamaan file asli belum seragam. Yang ada sekarang campuran PascalCase
  dan snake_case, dan `Paksamku_pakaipakaian_adat.png` masih punya spasi
  serta salah ketik (`pakaip`). Untuk file baru, pakai **snake_case** tanpa
  spasi.
- Setiap animasi status punya **sepasang varian**: terang dan gelap.
  `Menunggu_Tinjauan_*` menandai mode lewat nama file (`_darkmode`);
  `404_warning_*` memakai `white` / `black`, yang menunjuk warna latar,
  bukan nama mode. Kalau menambah status baru, pilih satu pola dan
  konsisten.
- Latar GIF mode gelap sengaja mendekati warna permukaan gelap web, bukan
  hitam murni: `Menunggu_Tinjauan_darkmode.gif` `#2A2A2A`,
  `404_warning_black.gif` `#2E2C2E`. Kalau latar web berubah, GIF gelap
  perlu diekspor ulang — warna teksnya ikut terkunci ke latar lama.
- PNG maskot 1000 × 1000 adalah ukuran master. Untuk UI, turunkan ke webp
  dan setinggi tetap seperti yang sudah dilakukan web, supaya repo ini
  tidak jadi tempat file berat.
- Jangan menimpa file yang sudah dipakai. Tambah file baru dan arahkan
  pemakai ke nama baru supaya histori tetap bisa dirujuk.

## Yang tidak ada di repo ini

- Bukan repo media pengguna. Gambar kata, avatar, dan bukti lampiran
  milik `images/`.
- Bukan repo audio. Pelafalan milik `audios/`.
- Tidak ada alur upload. Perubahan lewat commit.

## Lisensi

Aset dan dokumentasi repo ini dilisensikan di bawah **MIT** - lihat
[`LICENSE`](./LICENSE).

Logo dan maskot adalah identitas SambasKu. Repo ini harus tetap publik
agar klien bisa memuat aset via jsDelivr.