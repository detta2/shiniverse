# ShiniVerse & MangaBrush Studio

SPA All-in-One: **Portal Baca Komik** ala shinigami.asia + **MangaBrush AI Translator Studio** (CMS & editor admin) dalam satu file `index.html`.

## Fitur Portal
- Hero Carousel Trending, filter Manhwa/Manga/Manhua, grid update proyek + 3 tombol chapter terakhir, Sidebar Top Ranking (views), Live Search
- Detail series: cover, rating, genre, sinopsis, bookmark, daftar chapter + cari chapter, tombol "✏️ Edit / Translate di Studio"
- Reader webtoon vertikal zero-gap, dynamic text-layer rendering dari JSON `text_layers`, HUD auto-hide (klik tengah), anti-scrape toggle, prev/next + dropdown chapter + Fit Width

## Fitur Studio
- CMS: tambah komik (cover URL/upload/otomatis), tambah chapter multi-upload halaman + sampel manga Jepang bawaan
- Brush Translator (Fabric.js): Brush Mask merah 55%, cluster sapuan → region, animasi scan 1,2 dtk, inpainting Bubble (elips menyampel warna balon — gelap tetap gelap, teks kontras, Anime Ace) & SFX (patch tekstur + Bangers outline)
- Prompt preset Muse AI per mode (positive/negative persis), slider Inpainting Strength / CFG / Mask Blur
- OCR asli via Gemini Vision API (key di Settings) atau Mode Simulasi Cerdas tanpa key; endpoint Muse Inpaint opsional
- Inspector teks (font Bangers/Comic Neue/Anime Ace/Montserrat/Inter, ukuran, warna, outline, rotasi, toggle SFX Style), daftar layer + JSON inspector `text_layers`
- 💾 Simpan & Publish ke Chapter (WebP 0.80 + JSON) — reader portal langsung menampilkan versi flatten; Download PNG/WebP

## Autonomous Mirror Agent (tab di Studio)
Pusat kendali sync otomatis: form target (URL MangaDex atau judul), Sync Mode **Full Auto-Mirror** (metadata + 3 chapter terakhir, re-sync otomatis tiap 30 menit selama tab terbuka) atau **RAW + Auto-Translate Queue** (halaman masuk antrean Brush Studio), **Terminal Live Log** real-time, daftar target tersimpan, dan antrean translate per chapter. Sumber: **MangaDex API** resmi (tanpa key, jalan penuh di browser, chapter diprioritaskan Bahasa Indonesia) atau **Agent Worker Endpoint** — backend VPS milikmu yang membalas kontrak JSON `{series, chapters:[{number, title, pages:[{image,w,h}]}]}`.

## Database
Hybrid: isi `SUPABASE_URL` + `SUPABASE_ANON_KEY` di ⚙️ Settings untuk mode Supabase (`@supabase/supabase-js`), kosongkan untuk fallback `localStorage` dengan struktur data identik. Tombol **📋 Copy SQL Schema** di Settings berisi DDL lengkap (`series`, `chapters`, `chapter_pages` dengan `text_layers JSONB`, `bookmarks`).

100% client-side, tanpa build step. Jalankan dengan membuka `index.html` atau static hosting apa pun.
