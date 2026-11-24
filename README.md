# Cleaner
Jasa kebersihan
Buatkan satu file HTML5 lengkap (single file: HTML + CSS + JavaScript inline, tanpa framework, tanpa build tool, tanpa file eksternal selain font sistem) untuk website jasa kebersihan bernama "Peugleh Shiner". Bahasa seluruh konten: Indonesia, nada ramah dan praktis. Website harus langsung bisa dibuka lewat double-click (file://), responsif dari 360px sampai desktop lebar.

## Tujuan bisnis
Pengunjung memilih layanan kebersihan, mengisi detail pesanan, melihat estimasi harga otomatis, lalu mengirim ringkasan pesanan ke WhatsApp admin. Tidak ada backend, tidak ada database, tidak ada payment gateway — pembayaran hanya diinformasikan (DANA / transfer BSI / tunai) dan dikonfirmasi admin lewat WhatsApp.

## Identitas visual
- Warna: biru utama #1565c0, biru gelap #0d47a1, biru muda #eaf3ff, ink #172b4d, muted #64748b, garis #e5edf6, hijau aksi #16a34a, putih #fff.
- Font: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", sans-serif. Body line-height 1.6.
- Latar body: gradasi linear 135deg dari #f8fcff ke #edf6ff ke #f7fbff, ditambah beberapa radial-gradient titik/gelembung biru transparan (pola "bersih & segar"), background-attachment: fixed.
- Ada lapisan dekoratif fixed (.cleaning-atmosphere) berisi bulatan cincin tipis biru transparan dan karakter "✦" besar dengan opacity rendah, pointer-events: none, aria-hidden="true".
- Sudut membulat besar (radius kartu 20px, panel 24–30px), shadow lembut 0 12px 35px rgba(21,101,192,.10), garis tipis 1px.
- Tombol: padding 12px 19px, radius 12px, font-weight 750, transisi .2s, hover naik 1px. Varian: primary (biru, teks putih), outline (teks biru, border #bfd7f5, latar putih), green (latar hijau, teks putih).
- Eyebrow: pill kecil latar #e1efff, teks biru, uppercase-ish kecil, font-weight 800.
- Heading memakai clamp(): h1 clamp(2.35rem, 5vw, 4.15rem) letter-spacing -2px; h2 section clamp(1.8rem, 3vw, 2.45rem).
- Kontainer: width min(1120px, calc(100% - 40px)); di bawah 560px jadi min(100% - 28px, 1120px).
- Semua animasi halus dan hemat; scroll-behavior: smooth.

## Struktur halaman (urutan)
1. **Topbar sticky** (tinggi min 72px, latar putih, border bawah): kiri logo brand "✦ Peugleh Shiner" (pakai placeholder logo berupa kotak/emoji atau SVG inline sederhana — JANGAN memakai gambar base64 raksasa; sediakan komentar "ganti src dengan logo sendiri"), tengah menu anchor: Beranda, Layanan, Estimasi Harga, Cara Pesan, kanan tombol primary "Pesan Sekarang" menuju #pemesanan. Menu disembunyikan di bawah 820px.

2. **Hero (#home)**: grid 2 kolom (1.05fr / .95fr), padding 72px atas-bawah, latar radial biru muda.
   - Kiri: eyebrow "✧ Layanan kebersihan terpercaya"; h1 "Rumah bersih,<br><span>hidup lebih praktis.</span>" (kata kedua biru); paragraf: "Jadwalkan jasa kebersihan kos dan rumah tanpa repot. Pilih layanan, hitung estimasi harga, lalu pesan langsung melalui WhatsApp."; dua tombol: "Lihat Layanan →" (primary, ke #layanan) dan "Hitung Estimasi" (outline, ke #pemesanan).
   - Kanan: panel ilustrasi (.hero-art) radius 30px, gradasi 145deg #cfe5ff → #8bbcf3, dua lingkaran putih transparan di sudut, berisi logo/ilustrasi di tengah (max-height 300px), plus dua kartu float kecil: kiri bawah "✓ Praktis & mudah dipesan", kanan atas "✨ Bersih dan nyaman".
3. **Layanan (#layanan)**: judul section "Temukan layanan yang kamu butuhkan" + subjudul "Mulai dari kamar kos hingga rumah, pilih layanan sesuai kebutuhan kebersihanmu." Grid 3 kolom (2 di ≤820px, 1 di ≤560px) berisi 6 kartu layanan, masing-masing: ikon emoji dalam kotak radius 16px latar biru muda, judul, deskripsi, harga biru tebal + label kecil "/ mulai dari", dan tombol outline "Pilih Layanan" (kecuali kartu terakhir berupa link "Atur Pesanan" ke #pemesanan):
   - 🛏️ Cleaning Kamar Kos — Rp50.000 — "Pembersihan kamar, menyapu, mengepel, merapikan area, dan membersihkan permukaan."
   - 🏠 Cleaning Rumah — Rp150.000 — "Pembersihan area rumah seperti ruang tamu, kamar tidur, dapur, dan lantai."
   - 🫧 Deep Cleaning — Rp200.000 — "Pembersihan lebih menyeluruh untuk area yang membutuhkan perhatian ekstra."
   - 🚿 Cleaning Kamar Mandi — Rp35.000 — "Membersihkan toilet, lantai, dinding, wastafel, dan kerak sesuai kondisi."
   - 🍽️ Cleaning Dapur — Rp45.000 — "Merapikan dan membersihkan meja, permukaan dapur, serta area sekitar."
   - 🧽 Layanan Tambahan — Rp15.000 "/ tambahan" — "Tambahkan kebutuhan khusus untuk menyesuaikan layanan dengan kondisi tempat."
   Di bawah grid: catatan kecil terpusat "*Harga pada website ini adalah contoh dan dapat disesuaikan dengan tarif usaha."
4. **Pemesanan (#pemesanan)**, latar #edf5ff: judul "Hitung biaya dan jadwalkan layanan", subjudul "Isi detail berikut untuk mendapatkan estimasi harga sebelum melanjutkan ke WhatsApp." Berisi panel dua kolom (1fr / .78fr; jadi 1 kolom di ≤820px) dengan bayangan dan radius 24px.
   - **Kiri, form (#bookingForm)**: judul "Detail pemesanan" + "Lengkapi informasi agar admin dapat mengonfirmasi pesananmu." Grid form 2 kolom (1 kolom di ≤560px), field wajib ditandai "*":
     - Nama lengkap (text, required, placeholder "Nama kamu")
     - Nomor WhatsApp (tel, required, placeholder "08xxxxxxxxxx")
     - Jenis layanan (select, required): kos, rumah, deep, mandi, dapur — tiap opsi menampilkan harga, mis. "Cleaning kamar kos — Rp50.000"
     - Ukuran area (select): 1 = Kecil (hingga 20 m²); 1.3 = Sedang (21–50 m²) — +30%; 1.6 = Besar (lebih dari 50 m²) — +60%
     - Jumlah kamar (select): 0 = Tidak ada / tidak berlaku, 1, 2, 3, 4 = "4 kamar atau lebih"
     - Jumlah kamar mandi (select): 0, 1, 2, 3 = "3 kamar mandi atau lebih"
     - Tanggal layanan (date, required)
     - Waktu kedatangan (select, required): placeholder "Pilih waktu", 08.00, 10.00, 13.00, 15.00, 17.00 WIB
     - Alamat lengkap (textarea, full width, required, placeholder "Nama jalan, nomor rumah/kos, kecamatan, kota...")
     - Metode pembayaran (select): DANA, Transfer Bank Syariah Indonesia (BSI), Tunai kepada petugas (jika tersedia); di bawahnya catatan kecil dua baris: "DANA: 0812-6240-6380" dan "BSI: 7268798317" plus "Pastikan nama penerima sesuai konfirmasi admin sebelum mengirim uang."
     - Layanan tambahan (select): 0 = Tidak ada, 15000 = Tambahan ringan — Rp15.000, 30000 = Tambahan ekstra — Rp30.000
     - Catatan tambahan (textarea, full width, opsional)
     Tombol submit selebar 100% berwarna hijau: "Checkout melalui WhatsApp ↗", di bawahnya teks kecil "Dengan melanjutkan, detail pesanan akan dibuka di WhatsApp untuk dikonfirmasi admin."
     Semua input: border 1px #d8e3f0, radius 11px, padding 12px 13px; fokus jadi border #65a5ef dengan ring 0 0 0 3px #e5f1ff.
   - **Kanan, panel estimasi (sticky/aside)**: gradasi 160deg #145db3 → #0d47a1, teks putih, padding 32px. Judul "Ringkasan estimasi", subjudul "Perkiraan biaya berdasarkan layanan dan ukuran area yang dipilih." Baris ringkasan (label kiri, nilai kanan, border bawah putih transparan): Layanan, Harga dasar, Ukuran area, Tambahan. Lalu blok total di bawah: label "Total estimasi" + angka besar 2.1rem. Catatan kaki: "*Estimasi bukan tagihan final. Admin akan mengonfirmasi harga dan ketersediaan jadwal berdasarkan detail serta kondisi lokasi."
5. **Cara Pesan (#cara-pesan)**: judul "Cara pesan Peugleh Shiner" + subjudul "Tidak perlu proses yang rumit. Pesan layanan kebersihan langsung dari website." Tiga langkah dengan nomor bulat: 1 Pilih layanan ("Tentukan jenis layanan dan isi kebutuhan kebersihanmu."), 2 Atur jadwal ("Pilih tanggal, waktu, alamat, dan metode pembayaran."), 3 Konfirmasi WhatsApp ("Kirim ringkasan pesanan dan tunggu konfirmasi admin."). Di bawahnya blok CTA biru radius 24px: kiri "Siap punya ruang yang lebih bersih?" + "Pilih layanan dan jadwalkan kebersihanmu hari ini.", kanan tombol putih "Mulai Pemesanan →" ke #pemesanan.
6. **Footer** latar #0d2850 teks #d7e5f8: brand putih + tagline singkat, dan teks kecil berisi nama usaha, layanan, area, serta kontak WhatsApp/email (isi placeholder yang mudah diganti).

7. **Elemen global**: tombol chat mengambang kanan bawah (bulat 58px, hijau #16a34a, ikon chat, shadow hijau) yang membuka WhatsApp; dan toast notifikasi di tengah bawah (latar #172b4d, teks putih, radius 12px, muncul/hilang dengan kelas .show) untuk umpan balik singkat.

## Logika JavaScript (wajib jalan)
- Konstanta di paling atas script, dengan komentar jelas:
  `const WHATSAPP_NUMBER = "6281262406380"; // GANTI dengan nomor admin, format 62...`
  serta objek harga per layanan (kos 50000, rumah 150000, deep 200000, mandi 35000, dapur 45000) dan tarif tambahan kamar / kamar mandi.
- Estimasi dihitung real-time setiap kali input berubah (event `input`/`change` pada form):
  total = (harga dasar × multiplier ukuran) + (biaya kamar × jumlah kamar) + (biaya kamar mandi × jumlah kamar mandi) + layanan tambahan.
  Tampilkan rupiah dengan `Intl.NumberFormat("id-ID", { style:"currency", currency:"IDR", maximumFractionDigits:0 })` pada #summaryService, #basePrice, #sizePrice, #extraPrice, #totalPrice.
- Tombol kartu layanan (.choose-service dengan data-service) mengisi select layanan lalu scroll halus ke #pemesanan dan menampilkan toast "Layanan dipilih".
- Submit form: `e.preventDefault()`, validasi field wajib (nama, nomor WA, tanggal, waktu, alamat) — kalau kosong tampilkan toast peringatan dan fokus ke field tersebut; normalisasi nomor WA (08... → 628...); susun pesan teks multi-baris berisi: sapaan, nama, nomor, layanan, ukuran area, jumlah kamar & kamar mandi, tanggal & waktu, alamat, metode pembayaran, layanan tambahan, catatan, dan total estimasi; lalu buka `https://wa.me/<WHATSAPP_NUMBER>?text=<encodeURIComponent(pesan)>` di tab baru (`window.open(..., "_blank")`) dan tampilkan toast "Membuka WhatsApp...".
- Tombol chat mengambang membuka `https://wa.me/<WHATSAPP_NUMBER>` dengan pesan sapaan.
- Tanggal minimal = hari ini (set atribut `min` pada input date).
- Tidak ada error di console, tidak ada dependensi eksternal, dan tidak ada data yang dikirim ke server mana pun.

## Batasan teknis
- Satu file .html, CSS di dalam <style>, JS di dalam <script> sebelum </body>.
- Semantik & aksesibilitas: header/nav/main/section/article/aside/footer, label terhubung ke input lewat for/id, alt pada gambar, aria-hidden pada elemen dekoratif, kontras teks memadai, target sentuh minimal 44px.
- Meta: charset UTF-8, viewport, theme-color #1565c0, title "Peugleh Shiner — Jasa Kebersihan Praktis", lang="id".
- Semua teks placeholder (nomor WhatsApp, nomor DANA/BSI, alamat, sosial media) dikumpulkan di satu komentar di atas file supaya mudah diganti.
- Hasil akhir harus enak dibaca di mobile (tanpa horizontal scroll) dan tetap rapi di desktop 1440px.
