# Portofolio Chelsian Adyatama

Financial research dan data analytics. Situs statis, HTML murni, tanpa
kerangka kerja dan tanpa proses build. Cukup unggah berkasnya, situsnya jalan.

**Baru pertama kali deploy?** Ikuti [PANDUAN-DEPLOY.md](PANDUAN-DEPLOY.md).

## Isi

| Berkas | Isinya |
|---|---|
| `index.html` | Halaman portofolio: profil, dua proyek beserta metodologinya, pengalaman, sertifikat, pendidikan |
| `analisis-emiten.html` | Dashboard proyek 1, analisis 12 rasio keuangan pada tiga emiten satu sektor |
| `regresi-nilai-perusahaan.html` | Dashboard proyek 2, regresi linear berganda enam prediktor dengan empat uji asumsi klasik |
| `og-image.jpg` | Gambar pratinjau yang muncul saat tautan dibagikan di LinkedIn atau WhatsApp |
| `assets/` | Gambar sertifikat |

## Cara merevisi

Tiap halaman berdiri sendiri. Mengubah satu berkas tidak memengaruhi yang lain.

| Mau ubah apa | Buka berkas |
|---|---|
| Teks profil, daftar keahlian, pengalaman, sertifikat | `index.html` |
| Ringkasan dan metodologi proyek di halaman depan | `index.html`, cari `class="method"` |
| Isi dashboard analisis rasio | `analisis-emiten.html` |
| Isi dashboard regresi | `regresi-nilai-perusahaan.html` |
| Mengganti gambar sertifikat | ganti berkas di `assets/`, pertahankan namanya |
| Alamat situs untuk pratinjau tautan | ketiga berkas HTML, cari `ALAMAT-SITUS-KAMU` |

Dua bahasa ditangani lewat atribut `data-id` dan `data-en` pada elemen teks.
Kalau menambah kalimat baru di `index.html`, tulis keduanya mengikuti pola yang
sudah ada, supaya tombol ID / EN tetap konsisten.

## Catatan isi

Kedua proyek memakai data latihan dan data kuliah, bukan data perusahaan
sebenarnya. Hal ini dinyatakan terbuka di halaman depan dan di tiap dashboard.
Yang ditunjukkan adalah metodenya: urutan kerja, uji yang dipakai, dan cara
membaca hasilnya.

Angka pada dashboard regresi dihitung dari berkas data yang sama yang dianalisis
di SPSS, sehingga bisa direproduksi: R² 0,817, F(6,43) = 32,06, Durbin-Watson
1,861, VIF tertinggi 1,211.

## Yang masih bisa ditambah

- Hasil akhir regresi setelah dijalankan ulang di SPSS, untuk dicocokkan dengan
  angka di dashboard
- Proyek ketiga
- Tautan ke tulisan di Medium
