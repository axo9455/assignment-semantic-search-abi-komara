# Retrieval Test Results

- Embedding model: `gemini-embedding-2` (768 dim)
- LLM: `gemini-3.5-flash-lite` (fallback `gemini-3.1-flash-lite`, temperature 0.2)
- Top-k: 3, similarity: cosine (FAISS IndexFlatIP)
- Dijalankan: 2026-10-20 16:28 UTC

> File ini dibuat otomatis oleh notebook (section 8). Analisis relevansi ada di README.md.

## Ringkasan

| No | Tipe | Query | Expected | Top-3 retrieved (skor) | Hit@1 | Hit@3 | Fallback |
|---|---|---|---|---|---|---|---|
| 1 | direct | Bagaimana cara membatalkan pesanan yang sudah dibuat? | 3 | #3 (0.831), #5 (0.737), #8 (0.727) | ✅ | ✅ | tidak |
| 2 | direct | Metode pembayaran apa saja yang tersedia? | 17 | #17 (0.819), #22 (0.752), #20 (0.748) | ✅ | ✅ | tidak |
| 3 | paraphrase | Saldo saya sudah terpotong tapi pesanannya masih tertulis belum dibayar | 21 | #21 (0.827), #19 (0.712), #8 (0.706) | ✅ | ✅ | tidak |
| 4 | paraphrase | paketnya udah nyampe tapi barangnya pecah, harus gimana? | 16 | #16 (0.775), #12 (0.692), #54 (0.678) | ✅ | ✅ | tidak |
| 5 | paraphrase | aku lupa kata sandi buat masuk | 32 | #32 (0.777), #55 (0.718), #35 (0.653) | ✅ | ✅ | tidak |
| 6 | partial | Berapa minimal belanja supaya bisa pakai cicilan? | 20 | #20 (0.791), #17 (0.670), #18 (0.646) | ✅ | ✅ | tidak |
| 7 | out_of_kb | Apakah bisa kirim barang ke luar negeri? | - | #15 (0.678), #11 (0.673), #10 (0.657) | - | - | ya |
| 8 | out_of_kb | Bagaimana cara mendaftar menjadi penjual dan membuka toko di platform ini? | - | #31 (0.712), #1 (0.701), #50 (0.665) | - | - | ya |

## Uji konsistensi (3x run)

| Tipe | Query | Expected | Hasil 3x | Konsisten & benar |
|---|---|---|---|---|
| partial | Berapa minimal belanja supaya bisa pakai cicilan? | menjawab | menjawab, menjawab, menjawab | ✅ |
| out_of_kb | Bagaimana cara mendaftar menjadi penjual dan membuka toko di platform ini? | fallback | fallback, fallback, fallback | ✅ |

## Jawaban LLM per query

### 1. (direct) Bagaimana cara membatalkan pesanan yang sudah dibuat?

> Halo! Anda dapat membatalkan pesanan yang sudah dibuat melalui halaman 'Pesanan Saya' selama status pesanan masih 'Diproses'. Namun, perlu diingat bahwa setelah status berubah menjadi 'Dikirim', pembatalan sudah tidak dapat dilakukan. 
>
> Sumber: FAQ #3

### 2. (direct) Metode pembayaran apa saja yang tersedia?

> Halo! Kami mendukung transfer bank, kartu kredit/debit, e-wallet, dan pembayaran melalui minimarket rekanan untuk metode pembayaran Anda. 
>
> Sumber: FAQ #17

### 3. (paraphrase) Saldo saya sudah terpotong tapi pesanannya masih tertulis belum dibayar

> Halo, hal tersebut biasanya terjadi karena adanya keterlambatan sinkronisasi pada sistem pembayaran. Anda dapat menunggu selama 15 hingga 30 menit atau segera menghubungi customer service jika status pesanan Anda belum juga berubah.
>
> Sumber: FAQ #21

### 4. (paraphrase) paketnya udah nyampe tapi barangnya pecah, harus gimana?

> Halo, jika paket Anda diterima dalam kondisi rusak, silakan ikuti langkah berikut:
> 1. Segera ambil foto atau video kondisi paket saat diterima.
> 2. Laporkan melalui menu komplain dalam waktu 2x24 jam sejak barang diterima.
>
> Sumber: FAQ #16

### 5. (paraphrase) aku lupa kata sandi buat masuk

> Halo! Untuk mengatur ulang kata sandi akun Anda, silakan ikuti langkah-langkah berikut:
> 1. Klik 'Lupa Password' pada halaman login.
> 2. Masukkan email yang terdaftar.
> 3. Ikuti instruksi reset password yang dikirim ke email Anda.
>
> Sumber: FAQ #32

### 6. (partial) Berapa minimal belanja supaya bisa pakai cicilan?

> Halo! Fitur cicilan tersedia untuk transaksi dengan kartu kredit tertentu pada nominal minimal yang ditentukan pihak bank. Namun, detail mengenai nominal minimal belanja tersebut tidak tersedia di FAQ kami. Silakan hubungi customer service kami untuk bantuan lebih lanjut.
>
> Sumber: FAQ #20

### 7. (out_of_kb) Apakah bisa kirim barang ke luar negeri?

> Maaf, saya belum memiliki informasi mengenai hal tersebut di FAQ kami. Silakan hubungi customer service kami untuk bantuan lebih lanjut.

### 8. (out_of_kb) Bagaimana cara mendaftar menjadi penjual dan membuka toko di platform ini?

> Maaf, saya belum memiliki informasi mengenai hal tersebut di FAQ kami. Silakan hubungi customer service kami untuk bantuan lebih lanjut.
