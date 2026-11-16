# Rasa AI

Prototipe chat persona AI berbahasa Indonesia. Jalankan dengan Node.js dari folder ini:

```powershell
node server.js
```

Buka `http://127.0.0.1:4173/` di browser. Gunakan `PORT=...` bila port 4173 sudah dipakai.

## Fitur

- Identitas persona: nama, deskripsi, MBTI, arketipe (Deredere, Tsundere, Yandere, Kuudere, Dandere, Custom), watak, dan tiga penggeser sifat.
- Koleksi persona lokal: simpan beberapa profil karakter, aktifkan lagi dari pengaturan, atau hapus profil yang tidak dipakai. Koneksi model dan kunci API tidak ikut tersimpan dalam profil.
- Diskusi multi-persona: buka panel diskusi, pilih sekurangnya dua persona tersimpan, lalu kirim pesan. Persona merespons bergiliran dan konteks mencakup balasan sebelumnya. Pengaturan emosi diterapkan berdasarkan respons sebelumnya dari persona yang sama.
- Respons mode API dikirim lewat streaming Chat Completions. Penyedia dan model harus mendukung streaming dan CORS.
- Lampiran TXT, Markdown, DOCX dan PDF dengan teks dapat dibaca di browser; dokumen maksimal 5 MB dan 100.000 karakter, PDF maksimal 100 halaman. PDF hasil pindai memerlukan OCR yang belum tersedia. Gambar maksimal 512 KB dan memerlukan model yang mendukung gambar. Lampiran memerlukan mode API dan isi akan dikirim ke penyedia model.
- Foto profil JPG, PNG, atau WebP untuk setiap persona. Foto dikecilkan sebelum disimpan dan tampil di header, sidebar, dashboard, serta avatar balasan; kaomoji tetap tampil pada kartu ekspresi.
- Menu Pengaturan di sidebar atau ikon roda gigi: nama panggilan, hubungan dengan persona, tema terang/gelap/rosé, pilihan font, dan ukuran huruf. Preferensi tersimpan di browser. Nama dan hubungan dipakai sebagai konteks saat mode model API aktif.
- Tiap respons menampilkan kaomoji dan grafik persentase enam ekspresi: senang, marah, takut, bingung, sedih, jijik.
- Tampilan chat bergaya kartu: emosi dominan, persentase dan perubahan enam emosi, waktu pesan, serta narasi “Batin” fiksi karakter. Kolom input menampilkan perkiraan intensitas pesan secara langsung.
- Warna dan animasi kaomoji mengikuti mood dominan. Klik atau sentuh wajah persona dan avatar balasan untuk melihat reaksi sesaat. Gerakan otomatis dinonaktifkan jika perangkat memilih pengurangan animasi.
- Live Char: buka dari sidebar untuk tampilan kaomoji besar, dikte speech-to-text, dan pembacaan text-to-speech. Dikte harus dimulai lewat tombol mikrofon, hasilnya dapat diedit sebelum dikirim, dan dukungan serta pilihan suara bergantung pada browser dan perangkat. Percakapan memakai riwayat chat aktif.
- Riwayat percakapan dan persona tersimpan di `localStorage` browser.
- Mode demo interaktif tanpa layanan eksternal.
- Mode model API melalui endpoint Chat Completions yang kompatibel OpenAI. Isi endpoint, nama model, dan kunci API pada pengaturan persona. Kunci API hanya disimpan dalam memori tab dan hilang saat halaman dimuat ulang.

Mode demo menggunakan respons simulasi berbasis kata kunci. Untuk percakapan yang benar-benar dihasilkan model, gunakan mode model API. Persentase emosi adalah interpretasi ekspresi karakter, bukan pengukuran perasaan AI yang nyata. Endpoint API perlu mendukung permintaan lintas origin dari browser.

## Pemeriksaan lokal

Jalankan `node --check dist/app.js` dari folder ini. Pemeriksaan logika tambahan ada di `../../work/check-rasa-ai.js`.
