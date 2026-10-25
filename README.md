# 0x4research — Minimalist Terminal Research Archive & Personal Blog (Jekyll Theme)

<p align="center">
  <img src="https://i.ibb.co.com/XkxnDfMv/0x4research-Terminal-UI-Collage.png" width="100%" alt="0x4research Preview">
</p>


Copied from: Editing 0x4research/README.md at main · 0xrwise/0x4research - <https://github.com/0xrwise/0x4research/edit/main/README.md>


Copied from: Editing 0x4research/README.md at main · 0xrwise/0x4research - <https://github.com/0xrwise/0x4research/edit/main/README.md>

**0x4research** adalah template website statis berbasis **Jekyll** dengan konsep *Unix Terminal* murni untuk arsip penelitian pribadi (*personal research archive*) dan blog catatan teknis. Seluruh konfigurasi identitas, perintah terminal, serta halaman CV dengan efek ketikan otomatis (*typewriter effect*) dipusatkan di dalam satu file **`_config.yml`**.

## Fitur Utama

- **Interactive Home Shell (`index.html`)**: Terminal interaktif yang mendukung perintah `help`, `whoami`, `skills`, `contact`, dan `clear`, dilengkapi navigasi riwayat ketikan (`ArrowUp` / `ArrowDown`) dan proteksi XSS.
- **Typewriter CV & Split Photo Layout (`cv.html`)**: Menggunakan perintah Unix standar (`cat ~/cv.txt`) yang diketik otomatis, diikuti efek *typewriter* karakter-per-karakter (terinspirasi dari *rataalada.com*) di samping bingkai foto profil, serta bagian *timeline* riset/pendidikan dan topik keahlian. (Klik di mana saja pada area CV untuk mempercepat/menyelesaikan animasi ketikan seketika).
- **Minimalist Post Archive (`posts.html` & `_layouts/post.html`)**: Menampilkan daftar artikel layaknya output perintah `cd ~/posts && ls` dan membuka isi artikel dengan `cat judul-artikel.md`.
- **Single-File Configuration (`_config.yml`)**: Tanpa *hardcode* data pribadi di dalam HTML atau JavaScript.

## Struktur Direktori Repositori

```text
0x4research/
├── _config.yml               # Pusat seluruh konfigurasi identitas, shell, & CV
├── _layouts/
│   ├── default.html          # Kerangka utama window terminal, SEO meta, & navigasi tab
│   └── post.html             # Layout tampilan artikel blog saat diklik
├── _posts/
│   └── 2026-01-01-welcome-to-0x4research.md  # Contoh artikel (format: YYYY-MM-DD-judul.md)
├── assets/
│   ├── css/
│   │   └── style.scss        # Stylesheet terpusat (SCSS)
│   ├── js/
│   │   └── terminal.js       # Mesin shell interaktif & efek typewriter CV
│   └── images/               # Folder untuk foto profil CV & gambar preview OpenGraph
├── index.html                # Halaman utama (HOME - Interactive Shell)
├── posts.html                # Halaman direktori artikel (POST - simulasi `ls`)
├── cv.html                   # Halaman profil & CV (CV - Typewriter & Split Layout)
├── Gemfile                   # Dependensi Ruby/Jekyll untuk pengembangan lokal
├── .gitignore                # File yang diabaikan oleh Git
└── README.md                 # Dokumentasi & panduan kustomisasi
```

## Panduan Bagian yang Harus Diubah (`_config.yml`)

Anda cukup membuka file **`_config.yml`** dan mengubah bagian-bagian berikut:

### 1. Metadata Website & SEO (`_config.yml` Baris 11–21)

| Key di `_config.yml` | Fungsi | Contoh Pengisian |
| :--- | :--- | :--- |
| `title` | Judul utama website di tab browser & share link | `"0x4research \| Personal Research Archive"` |
| `description` | Deskripsi singkat untuk mesin pencari (Google/SEO) | `"Personal research archive and blog."` |
| `url` | Domain utama website Anda | `"https://username.github.io"` |
| `baseurl` | Kosongkan `""` jika memakai `username.github.io`, atau isi `"/0x4research"` jika di-host sebagai project repo | `""` |
| `email` | Alamat email kontak | `"contact@domain.com"` |
| `image` | Gambar thumbnail saat link dibagikan | `"/assets/images/og-preview.jpg"` |
| `twitter_username` | Username X/Twitter (tanpa `@`) | `"your_handle"` |

### 2. Prompt Terminal, Banner ASCII & Perintah Interaktif (`_config.yml` Baris 24–48)

| Key di `_config.yml` | Fungsi | Bagian yang Terpengaruh |
| :--- | :--- | :--- |
| `terminal.window_title` | Teks judul di tengah top-bar window | Header di semua halaman |
| `terminal.username` | Nama user sebelum tanda `@` pada prompt (`user@0x4research:~$`) | Prompt di semua halaman |
| `terminal.hostname` | Nama host setelah tanda `@` pada prompt | Prompt di semua halaman |
| `terminal.ascii_banner` | Teks ASCII Art di halaman utama | Banner hijau di `index.html` |
| `terminal.commands.whoami` | Data `name`, `alias`, `bio`, dan `focus` | Output perintah `whoami` di halaman Home |
| `terminal.commands.skills` | Deskripsi fokus keahlian / metodologi | Output perintah `skills` di halaman Home |
| `terminal.commands.contact` | Label, teks tampilan, dan URL kontak | Output perintah `contact` di halaman Home |

### 3. Halaman CV & Efek Typewriter (`_config.yml` Baris 51–110)

| Key di `_config.yml` | Fungsi | Keterangan |
| :--- | :--- | :--- |
| `cv.command` | Perintah Unix yang diketik otomatis saat halaman `/cv/` dibuka | Default: `"cat ~/cv.txt"` |
| `cv.typewriter_speed` | Kecepatan ketikan per karakter (dalam milidetik) | Default: `18` (makin kecil makin cepat) |
| `cv.photo` | Path foto profil rasio 3:4 di samping teks | Isi `"/assets/images/profile.jpg"` atau kosongkan `""` |
| `cv.photo_caption` | Nama file yang tampil di bar atas bingkai foto | Default: `"profile.jpg"` |
| `cv.full_name` | Nama lengkap pada judul atas CV | Contoh: `"Nama Lengkap Anda"` |
| `cv.role` | Peran atau fokus utama di bawah nama | Contoh: `"Independent Researcher"` |
| `cv.location` | Kota / negara tempat tinggal | Contoh: `"Jakarta, Indonesia"` |
| `cv.bio_lines` | Daftar paragraf deskripsi diri yang diketik otomatis (*typewriter*) | Bisa diisi 1, 2, atau lebih paragraf |
| `cv.metadata` | Daftar info singkat (`key : value`) di bawah kotak ketikan | Mendukung warna `""`, `"c-green"`, `"c-blue"`, `"c-red"` |
| `cv.timeline` | Riwayat riset, pengalaman, atau pendidikan (`period`, `title`, `org`, `description`) | Ditampilkan dengan garis *timeline* terminal |
| `cv.skills` | Daftar topik riset / keahlian teknis | Ditampilkan sebagai *tag* terminal |
| `cv.links` | Daftar tautan kontak (`github`, `email`, dll.) di bagian bawah CV | Ditampilkan dengan format `label : link` |

## Cara Menambahkan Artikel Baru (`POST`)

1. Buat file baru di dalam folder **`_posts/`** dengan format nama: `YYYY-MM-DD-judul-artikel.md`.
2. Gunakan *Front Matter* berikut di bagian paling atas file:
   ```yaml
   ---
   layout: post
   title: "Judul Catatan Riset Anda"
   date: 2026-10-26 10:00:00 +0700
   categories: [research]
   ---

   Tulis isi catatan riset atau artikel blog Anda di sini...
   ```

## Menjalankan Secara Lokal & Deploy ke GitHub Pages

1. Untuk menjalankan di komputer lokal:
   ```bash
   bundle install
   bundle exec jekyll serve
   ```
2. Untuk mengunggah ke GitHub Pages: *push* seluruh isi folder ke repositori GitHub Anda, lalu aktifkan **Settings > Pages > Deploy from a branch (`main` / `/root`)**.
