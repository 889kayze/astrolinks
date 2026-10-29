# ASTRO LINKS

Website bio-link minimalis yang responsif. HTML, CSS, dan JavaScript dipisahkan agar mudah diedit dari HP Android.

## Isi folder
- `index.html` — struktur halaman dan dashboard.
- `css/style.css` — semua gaya tampilan.
- `js/app.js` — data awal, pengelolaan tautan, dashboard, dan statistik lokal.
- `assets/favicon.svg` — ikon situs.
- `_headers` — header keamanan dasar untuk Cloudflare Pages.

## Uji di HP
1. Ekstrak ZIP.
2. Buka folder dengan editor seperti Acode.
3. Buka `index.html` lewat preview lokal atau browser.
4. Tekan ikon pengaturan di kanan atas.
5. PIN awal: `1234`. Ganti di tab Keamanan.
6. Edit profil atau tambah tautan. Gunakan URL lengkap, misalnya `https://instagram.com/namakamu`.

## Mengubah tautan awal yang tampil untuk semua pengunjung
Buka `js/app.js`, cari `DEFAULT_DATA`. Ubah `profile` dan daftar `links`, lalu simpan dan deploy ulang. Contoh:
```js
{
  id: "instagram",
  title: "Instagram",
  url: "https://www.instagram.com/username/",
  category: "social",
  clicks: 0
}
```
Kategori yang tersedia: `website`, `social`, `other`.

## Deploy gratis ke Cloudflare Pages dari Android
Metode mudah untuk pemula:
1. Ekstrak `ASTRO-LINKS.zip` di HP.
2. Buka browser dan masuk ke https://dash.cloudflare.com/
3. Buat akun atau login.
4. Cari **Workers & Pages** → **Create** → **Pages** (label menu bisa berubah).
5. Pilih opsi unggah aset statis / direct upload jika tersedia.
6. Unggah isi folder proyek (file `index.html`, folder `css`, `js`, `assets`, dan `_headers`) sesuai petunjuk Cloudflare. Jangan mengunggah ZIP jika layar meminta folder/file hasil ekstrak.
7. Selesaikan deploy. Cloudflare akan memberikan alamat `*.pages.dev`.
8. Buka URL tersebut dan uji semua tombol di HP.

Jika dashboard Cloudflare tidak menawarkan unggah langsung pada alur Pages yang terlihat, gunakan alur **Connect to Git**: unggah folder proyek ke repositori GitHub, lalu hubungkan repositori itu dari Cloudflare Pages. Untuk proyek statis ini, build command biasanya dikosongkan dan output directory diisi `/` atau root proyek sesuai instruksi UI Cloudflare.

## Domain sendiri
Di Cloudflare Pages, buka proyek → **Custom domains** → tambahkan domain yang sudah dimiliki dan ikuti verifikasi DNS. Domain biasanya berbayar; hosting Pages dapat tetap gratis. Domain root dan subdomain dapat memerlukan pengaturan DNS yang berbeda sesuai petunjuk dashboard.

## Batasan penting
- Dashboard saat ini menyimpan perubahan di `localStorage` browser/perangkat yang digunakan. Perubahan tersebut **tidak otomatis terlihat oleh pengunjung lain** dan dapat hilang jika data browser dihapus.
- Statistik klik juga lokal di browser tersebut, bukan total klik semua pengunjung. Klik dicatat saat tautan dibuka dari halaman yang sedang berjalan; pemblokir browser atau navigasi tertentu dapat memengaruhi hitungan.
- PIN dashboard adalah pengunci antarmuka lokal, **bukan sistem login aman**. Jangan anggap data tersembunyi dari pengunjung teknis. Jangan menyimpan rahasia di file JS.
- Agar dashboard dapat mengedit tautan yang tampil untuk semua orang dan statistik terkumpul lintas perangkat, dibutuhkan backend/API atau layanan database/analitik. Versi ini tidak mengirim data pribadi ke server.
- Tautan contoh memakai `example.com` dan profil sosial umum. Ganti dengan akun milik sendiri sebelum dipublikasikan.
