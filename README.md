# 🎵 AURA — Music Player

> Music Player berbasis web modern, setara Spotify mini. Dibangun dengan HTML, CSS, dan JavaScript murni — tanpa framework.

![Preview](https://images.unsplash.com/photo-1511379938547-c1f69419868d?w=1200&q=80)

---

## 📁 Struktur Folder yang Direkomendasikan

Sebelum mulai, siapkan struktur folder seperti ini di repository GitHub kamu:

```
nama-repo/
│
├── index.html          ← File utama aplikasi
├── README.md           ← File ini
│
├── music/              ← Semua file lagu (.mp3)
│   ├── song1.mp3
│   ├── song2.mp3
│   └── ...
│
└── images/             ← Semua cover lagu (.jpg / .png)
    ├── cover1.jpg
    ├── cover2.jpg
    └── ...
```

---

## 🚀 Langkah-Langkah Deploy ke GitHub Pages

### STEP 1 — Buat Repository GitHub

1. Buka [github.com](https://github.com) → Login ke akun kamu
2. Klik tombol **"New"** (atau tanda **+** di pojok kanan atas → *New repository*)
3. Isi form:
   - **Repository name**: misalnya `aura-music-player`
   - **Visibility**: pilih **Public** *(wajib Public agar GitHub Pages bisa aktif)*
   - Centang **"Add a README file"**
4. Klik **"Create repository"**

---

### STEP 2 — Upload File ke Repository

**Cara A — Via GitHub Web (paling mudah, tanpa install apapun):**

1. Di halaman repository, klik **"Add file"** → **"Upload files"**
2. Upload file `index.html`
3. Klik **"Commit changes"**

**Cara B — Upload folder sekaligus (untuk musik & cover):**

1. Di halaman repository, klik **"Add file"** → **"Upload files"**
2. Seret (drag & drop) seluruh folder `music/` dan `images/` ke area upload
3. Tunggu proses upload selesai (tergantung ukuran file)
4. Isi commit message, misalnya: `Add music and cover images`
5. Klik **"Commit changes"**

> ⚠️ **Perhatian ukuran file:** GitHub membatasi ukuran file **maksimal 25 MB per file** via web upload. Jika file .mp3 kamu lebih besar, gunakan Git LFS (lihat bagian bawah).

---

### STEP 3 — Aktifkan GitHub Pages

1. Di halaman repository, klik tab **"Settings"** (ikon ⚙️)
2. Di sidebar kiri, klik **"Pages"**
3. Di bagian **"Source"**, pilih:
   - Branch: **`main`**
   - Folder: **`/ (root)`**
4. Klik **"Save"**
5. Tunggu 1–3 menit
6. Refresh halaman — akan muncul link seperti:
   ```
   https://username-kamu.github.io/aura-music-player/
   ```
7. Buka link tersebut — **AURA Music Player kamu sudah live! 🎉**

---

### STEP 4 — Sambungkan Lagu ke Aplikasi

Setelah semua file terupload, kamu perlu mengubah data lagu di `index.html`.

**Buka `index.html`**, cari bagian ini (sekitar baris 350):

```javascript
const songs = [
  {
    id: 1,
    title: "Ocean Breeze",
    artist: "Lofi Collective",
    src: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3",
    cover: "https://images.unsplash.com/photo-...",
    mood: "chill",
    duration: "3:52"
  },
  // ... lagu lainnya
];
```

**Ganti `src` dan `cover` dengan path file dari GitHub kamu:**

```javascript
const songs = [
  {
    id: 1,
    title: "Judul Lagu Kamu",
    artist: "Nama Artist",
    src: "music/nama-file.mp3",        // ← path relatif ke folder music/
    cover: "images/nama-cover.jpg",    // ← path relatif ke folder images/
    mood: "chill",                     // ← pilih: chill / focus / night / workout
    duration: "3:45"                   // ← durasi manual (format menit:detik)
  },
  {
    id: 2,
    title: "Lagu Kedua",
    artist: "Artist Dua",
    src: "music/lagu2.mp3",
    cover: "images/cover2.jpg",
    mood: "focus",
    duration: "4:10"
  },
  // tambah lagu sesuai kebutuhan...
];
```

> 💡 **Tips:** Nama file **jangan pakai spasi**. Gunakan tanda `-` atau `_` sebagai pengganti spasi. Contoh: `sunday-morning.mp3` ✅, `sunday morning.mp3` ❌

---

## 🎵 Pilihan Mood

Setiap lagu wajib punya satu nilai `mood`. Berikut pilihan yang tersedia:

| Mood | Emoji | Deskripsi |
|------|-------|-----------|
| `chill` | 🌊 | Santai, lo-fi, ambient |
| `focus` | 🎯 | Produktif, instrumental, deep work |
| `night` | 🌙 | Synthwave, gelap, malam hari |
| `workout` | ⚡ | Energik, EDM, motivasi |

---

## ⌨️ Keyboard Shortcuts

| Tombol | Fungsi |
|--------|--------|
| `Space` | Play / Pause |
| `→` Arrow Right | Lagu berikutnya |
| `←` Arrow Left | Lagu sebelumnya |
| `↑` Arrow Up | Volume naik |
| `↓` Arrow Down | Volume turun |
| `M` | Mute / Unmute |

---

## ✨ Fitur Lengkap

- **4 Halaman:** Home, Library, Playlists (by Mood), Now Playing
- **Audio Visualizer** — bar animasi mengikuti beat lagu
- **Dynamic Background** — warna berubah sesuai mood lagu
- **Search real-time** di Library
- **Sort by Mood / A–Z**
- **Shuffle & Repeat** mode
- **Mini floating player**
- **localStorage** — ingat lagu terakhir, volume, dan mode
- **Responsive** — sidebar di desktop, bottom nav di mobile
- **Keyboard shortcuts** lengkap

---

## ⚠️ Tips & Troubleshooting

### Lagu tidak bunyi?
- Pastikan path `src` sudah benar dan file sudah terupload
- GitHub Pages bersifat **case-sensitive** — `Music/Song.mp3` ≠ `music/song.mp3`
- Coba buka Developer Tools (F12) → tab Console untuk melihat error

### File .mp3 terlalu besar (>25MB)?
Gunakan **Git LFS (Large File Storage)**:
```bash
# Install Git LFS
git lfs install

# Track file mp3
git lfs track "*.mp3"
git add .gitattributes

# Lanjut commit & push seperti biasa
git add .
git commit -m "Add music files via LFS"
git push
```

### Cover lagu tidak muncul?
- Gunakan format `.jpg` atau `.png`
- Ukuran cover ideal: **500x500 px** hingga **1000x1000 px**
- Nama file jangan pakai karakter spesial (`#`, `&`, `?`, spasi)

### GitHub Pages belum aktif setelah di-save?
- Tunggu 2–5 menit, lalu refresh halaman Settings → Pages
- Pastikan repository berstatus **Public**

---

## 🔄 Cara Update / Tambah Lagu

1. Upload file `.mp3` baru ke folder `music/`
2. Upload file cover baru ke folder `images/`
3. Edit `index.html`, tambahkan entri baru di array `songs`:
   ```javascript
   {
     id: 13,  // nomor berikutnya
     title: "Lagu Baru",
     artist: "Artist Baru",
     src: "music/lagu-baru.mp3",
     cover: "images/cover-baru.jpg",
     mood: "chill",
     duration: "3:30"
   },
   ```
4. Commit dan push — perubahan otomatis live dalam beberapa detik

---

## 🛠️ Pengembangan Lanjutan (Roadmap)

Berikut fitur yang bisa kamu kembangkan ke depannya:

### Fase 1 — Polish
- [ ] Tambah animasi "like" / favorit per lagu
- [ ] Custom cover art fallback jika gambar tidak load
- [ ] Tambah info durasi otomatis (bukan manual)

### Fase 2 — Fitur Baru
- [ ] **Playlist custom** — buat & simpan playlist sendiri
- [ ] **Lyrics display** — tampilkan lirik dari file `.lrc` atau teks statis
- [ ] **Equalizer sederhana** — bass, treble, preset
- [ ] **Sleep timer** — otomatis berhenti setelah X menit

### Fase 3 — Skala Lebih Besar
- [ ] Integrasi **Supabase** untuk database lagu online
- [ ] **User auth** (login) untuk playlist personal
- [ ] **PWA (Progressive Web App)** — bisa diinstall di HP
- [ ] **Offline mode** dengan Service Worker

---

## 📄 Lisensi

Project ini bebas digunakan untuk keperluan pribadi maupun belajar.
Pastikan musik yang kamu upload adalah milik sendiri atau sudah memiliki izin penggunaan.

---

> *"Without music, life would be a mistake."* — Friedrich Nietzsche
