# SOLANA RADAR PRO — versi GitHub Pages statis

## Isi
- `index.html`: dashboard market dan analisis on-chain berbasis API publik.
- Tidak membutuhkan Python, PHP, MySQL, atau secret API key untuk dibuka.

## Deploy ke repository yang sudah ada
1. Download ZIP dan ekstrak.
2. Backup file `index.html` lama di GitHub.
3. Upload `index.html` dari folder ini ke root repository `solana-anti-rug-viral-screener` dan commit perubahan.
4. Tunggu GitHub Pages selesai deploy, lalu buka https://babamitoon-cpu.github.io/solana-anti-rug-viral-screener/ dan tekan Scan sekarang.

## Data dan batasan
- Data pasar (nama, simbol, gambar jika tersedia, market cap/FDV, likuiditas, volume 1 jam, perubahan harga 5 menit, buy/sell, umur pair) diambil dari API publik DEX Screener.
- On-chain: browser mencoba membaca suplai, 20 akun token terbesar, serta mint/freeze authority melalui Solana Mainnet RPC publik. RPC publik dapat membatasi permintaan atau tidak tersedia dari jaringan/browser tertentu.
- Top 10/top 20 adalah konsentrasi akun token terbesar berdasarkan RPC, bukan jaminan 10/20 wallet unik. Belum ada agregasi owner lintas token account.
- Holder count penuh tidak tersedia dari getTokenLargestAccounts.
- Dev Supply % tetap UNKNOWN sampai creator/dev wallet teridentifikasi dengan bukti dan saldo tokennya berhasil diperiksa. Tidak mengasumsikan creator sama dengan deployer tanpa bukti.
- Pembeli pertama, bundle, sniper, reputasi dev, dan keamanan likuiditas tetap UNKNOWN sampai ada analisis transaksi/penyedia data yang memadai.
- GitHub Pages hanya menjalankan front-end statis. Tidak ada pemantauan 24/7 saat halaman tertutup.
- Skor pasar adalah heuristik, bukan jaminan keamanan atau saran finansial.

## Pemeriksaan lokal
Buka `index.html` di browser dengan koneksi internet. Jika browser memblokir permintaan API, coba GitHub Pages atau server statis lokal.

## Tampilan visual
- Background putih, teks hitam, font Comic dengan target 14 px untuk seluruh elemen.
- Tombol dan tautan hijau.
- Ini adalah front-end statis; data yang tidak terverifikasi tetap ditampilkan sebagai UNKNOWN.
