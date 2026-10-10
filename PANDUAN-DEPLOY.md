# Panduan Push ke GitHub dan Deploy ke Vercel

Panduan ini untuk kamu yang belum pernah pakai GitHub sama sekali. Tidak perlu
install apa pun dan tidak perlu mengetik perintah di terminal. Semuanya lewat
browser.

Waktu yang dibutuhkan sekitar 20 menit untuk pertama kali. Setelah itu, setiap
revisi cuma butuh 2 menit.

---

## Daftar isi

1. [Apa yang sebenarnya terjadi](#1-apa-yang-sebenarnya-terjadi)
2. [Berkas yang akan diunggah](#2-berkas-yang-akan-diunggah)
3. [Bikin akun GitHub](#3-bikin-akun-github)
4. [Bikin repository](#4-bikin-repository)
5. [Unggah berkasnya](#5-unggah-berkasnya)
6. [Cek dulu lewat GitHub Pages](#6-cek-dulu-lewat-github-pages-opsional)
7. [Deploy ke Vercel](#7-deploy-ke-vercel)
8. [Cara merevisi nanti](#8-cara-merevisi-nanti)
9. [Kalau ada yang salah](#9-kalau-ada-yang-salah)
10. [Lampiran: cara pakai Git di komputer](#10-lampiran-cara-pakai-git-di-komputer)

---

## 1. Apa yang sebenarnya terjadi

Tiga hal yang perlu kamu bedakan, karena orang sering tertukar:

| Istilah | Artinya di sini |
|---|---|
| **GitHub** | Tempat menyimpan berkas. Anggap saja Google Drive khusus kode, yang mencatat setiap perubahan. |
| **Repository (repo)** | Satu folder proyek di dalam GitHub. Portofolio kamu jadi satu repo. |
| **Vercel** | Yang mengubah berkas di repo jadi situs web yang bisa dibuka orang lewat alamat internet. |

Alurnya: **berkas di komputer → GitHub → Vercel → alamat web.**

Yang penting dipahami: setelah tersambung, Vercel **otomatis** memperbarui situs
setiap kali berkas di GitHub berubah. Kamu tidak perlu deploy ulang manual.

---

## 2. Berkas yang akan diunggah

Isi folder `site` ada lima berkas:

```
index.html                      <- halaman portofolio, halaman utama
analisis-emiten.html            <- dashboard proyek 1
regresi-nilai-perusahaan.html   <- dashboard proyek 2
og-image.jpg                    <- gambar yang muncul saat tautan dibagikan
assets/
  sertifikat-ojk.jpg
  sertifikat-bucharest.jpg
README.md                       <- keterangan repo
PANDUAN-DEPLOY.md               <- berkas ini
```

Tiga hal yang tidak boleh salah:

1. **`index.html` harus berada paling luar**, bukan di dalam folder lain.
   Nama `index.html` itu yang dicari server sebagai halaman pertama.
2. **Folder `assets` harus ikut terunggah.** Kalau tidak, gambar sertifikat
   hilang dan muncul ikon gambar rusak.
3. **Huruf besar kecil berpengaruh.** `assets` tidak sama dengan `Assets`.
   Di komputermu mungkin sama saja, di server tidak.

---

## 3. Bikin akun GitHub

1. Buka [github.com](https://github.com) lalu klik **Sign up**.
2. Isi email, password, dan username.
   Username ini akan muncul di alamat situsmu, jadi pilih yang rapi.
   Misalnya `chelsianadyatama`, bukan `chelsian_ganteng99`.
3. Buka email, masukkan kode verifikasi.
4. Saat ditanya paket, pilih yang **Free**.

---

## 4. Bikin repository

1. Setelah masuk, klik tanda **+** di kanan atas, lalu **New repository**.
2. Isi seperti ini:

   | Kolom | Isi |
   |---|---|
   | Repository name | `portofolio` (baca catatan di bawah sebelum memilih) |
   | Description | `Portofolio financial research dan data analytics` |
   | Public / Private | **Public** |
   | Add a README file | **jangan dicentang** |
   | .gitignore | None |
   | License | None |

3. Klik **Create repository**.

**Kenapa harus Public:** GitHub Pages versi gratis hanya jalan di repo public.
Vercel sebenarnya bisa membaca repo private, tapi karena ini memang portofolio
yang ingin dilihat orang, tidak ada alasan menyembunyikannya.

### Soal nama repo

Nama repo bebas, tapi ia selalu muncul setelah username di alamat GitHub Pages.
Jadi pertimbangkan hasil akhirnya, bukan cuma namanya:

| Nama repo | Alamat yang dihasilkan |
|---|---|
| `portofolio` | `username.github.io/portofolio/` |
| `portofolio-chelsian-adyatama` | `username.github.io/portofolio-chelsian-adyatama/` |
| `chelsianadyatama.github.io` | `https://chelsianadyatama.github.io` |

Pilihan ketiga itu kasus khusus: kalau nama repo dibuat **persis sama** dengan
`username.github.io`, GitHub menjadikannya situs utama akun dan alamatnya tidak
punya embel-embel di belakang. Hanya boleh ada satu repo seperti ini per akun.
Ini yang paling rapi kalau situs ini memang jadi satu-satunya portofolio kamu.

Kalau tidak memakai cara itu, `portofolio` saja sudah cukup. Username sudah
membawa namamu, jadi menulis nama lagi di repo membuat alamatnya panjang tanpa
menambah informasi.

Aturan penamaan: boleh huruf, angka, tanda hubung, garis bawah, dan titik.
Spasi otomatis berubah jadi tanda hubung. Pakai huruf kecil semua.

Nama repo bisa diganti kapan saja lewat **Settings** lalu **Rename**, dan
GitHub mengalihkan alamat lama ke yang baru. Jadi ini bukan keputusan permanen.

Catatan penting: nama repo hanya memengaruhi alamat **GitHub Pages**. Alamat
Vercel diambil dari **Project Name** yang diisi terpisah saat impor. Jadi repo
bernama `portofolio` tetap bisa menghasilkan `portofolio-chelsian.vercel.app`.

Setelah dibuat, kamu akan melihat halaman kosong berisi perintah-perintah.
Abaikan saja semuanya, cari tulisan **uploading an existing file**.

---

## 5. Unggah berkasnya

1. Di halaman repo yang masih kosong, klik tautan **uploading an existing file**.
   Kalau repo sudah berisi sesuatu, klik tombol **Add file** lalu **Upload files**.
2. Buka folder `site` di komputermu.
3. **Pilih isinya, bukan foldernya.** Blok `index.html`,
   `analisis-emiten.html`, `regresi-nilai-perusahaan.html`, `README.md`,
   `PANDUAN-DEPLOY.md`, dan folder `assets`, lalu seret semuanya ke area unggah
   di browser.

   > Ini bagian yang paling sering salah. Kalau kamu menyeret folder `site`
   > itu sendiri, berkasnya akan tersimpan di `site/index.html` dan situsmu
   > nanti kosong. Yang diseret harus **isi** foldernya.

4. Tunggu sampai semua berkas muncul di daftar, termasuk
   `assets/sertifikat-ojk.jpg` dan `assets/sertifikat-bucharest.jpg`.
5. Di kotak **Commit changes** paling bawah, tulis pesan singkat:
   `Portofolio versi pertama`.
6. Klik **Commit changes**.

Sekarang berkasmu sudah di GitHub. Halaman repo akan menampilkan daftar berkas
dan isi README di bawahnya.

---

## 6. Cek dulu lewat GitHub Pages (opsional)

Langkah ini bukan keharusan, tapi berguna untuk memastikan berkasnya benar
sebelum menyentuh Vercel.

1. Di halaman repo, klik tab **Settings**.
2. Di menu kiri, klik **Pages**.
3. Bagian **Source**, pilih **Deploy from a branch**.
4. Bagian **Branch**, pilih `main` dan folder `/ (root)`, lalu **Save**.
5. Tunggu satu sampai dua menit, lalu muat ulang halaman itu. Akan muncul
   alamat seperti `https://chelsianadyatama.github.io/portofolio/`.
6. Buka alamat tersebut. Pastikan gambar sertifikat muncul dan tombol
   "Buka analisis" berpindah halaman dengan benar.

Kalau semuanya tampil, berarti berkasmu sudah benar. Lanjut ke Vercel.

---

## 7. Deploy ke Vercel

### 7.1 Daftar

1. Buka [vercel.com](https://vercel.com), klik **Sign Up**.
2. Pilih **Continue with GitHub**. Jangan daftar pakai email,
   karena menyambung lewat GitHub membuat langkah berikutnya jauh lebih pendek.
3. GitHub akan bertanya izin akses. Klik **Authorize Vercel**.
4. Saat ditanya untuk keperluan apa, pilih **Hobby** atau **Personal**.
   Ini yang gratis.

### 7.2 Impor repo

1. Di dashboard Vercel, klik **Add New** lalu **Project**.
2. Akan muncul daftar repo GitHub-mu. Cari `portofolio`, klik **Import**.

   Kalau repo-nya tidak muncul, klik **Adjust GitHub App Permissions**,
   lalu beri Vercel akses ke repo itu.

### 7.3 Atur dan deploy

Di halaman konfigurasi, isi seperti ini:

| Kolom | Isi |
|---|---|
| Project Name | `portofolio-chelsian` (ini jadi bagian alamat webnya) |
| Framework Preset | **Other** |
| Root Directory | `./` biarkan apa adanya |
| Build Command | kosongkan |
| Output Directory | kosongkan |
| Install Command | kosongkan |

Tiga kolom terakhir memang harus kosong. Situs ini HTML biasa, tidak perlu
dibangun dulu. Kalau diisi, Vercel akan mencari perintah yang tidak ada dan
deploy-nya gagal.

Klik **Deploy**. Tunggu sekitar 30 detik.

### 7.4 Selesai

Akan muncul layar ucapan selamat dan tangkapan layar situsmu. Alamatnya kira
kira `https://portofolio-chelsian.vercel.app`.

Klik alamat itu, buka di ponsel juga, dan cek tiga hal:

- [ ] Gambar sertifikat muncul di bagian Pengalaman & Prestasi
- [ ] Tombol "Buka analisis" di kedua proyek berpindah halaman
- [ ] Tombol "Kembali ke portofolio" di dashboard berfungsi
- [ ] Tombol ID / EN mengganti bahasa

Alamat inilah yang kamu pasang di LinkedIn, di CV, dan kamu sebut saat interview.

### 7.5 Wajib: pasang alamatmu supaya tautannya ada gambarnya

Saat tautan dibagikan di LinkedIn atau WhatsApp, yang muncul biasanya kartu
berisi gambar, judul, dan keterangan. Gambarnya sudah disiapkan, namanya
`og-image.jpg`. Tapi LinkedIn dan WhatsApp hanya mau membaca alamat gambar yang
**lengkap**, dan alamat situsmu baru diketahui setelah deploy. Karena itu di
berkas HTML masih ada penanda yang harus kamu ganti sekali.

Lakukan ini setelah alamat Vercel-mu jadi:

1. Buka repo di GitHub, klik `index.html`, klik ikon pensil.
2. Tekan Ctrl+F (atau Cmd+F), cari `ALAMAT-SITUS-KAMU`. Ada 5 tempat.
3. Ganti semuanya dengan alamat situsmu **tanpa garis miring di akhir**.

   Contoh, kalau alamatmu `https://portofolio-chelsian.vercel.app`, maka

   ```
   https://ALAMAT-SITUS-KAMU/og-image.jpg
   ```

   berubah jadi

   ```
   https://portofolio-chelsian.vercel.app/og-image.jpg
   ```

4. Commit dengan pesan `Pasang alamat situs untuk pratinjau tautan`.
5. Ulangi hal yang sama untuk `analisis-emiten.html` dan
   `regresi-nilai-perusahaan.html`.

**Cek hasilnya.** Setelah Vercel selesai memperbarui, buka
[LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/), tempelkan
alamat situsmu, klik Inspect. Kartunya akan muncul di situ.

Alat ini juga berguna kalau kamu pernah membagikan tautan sebelum langkah ini
dikerjakan. LinkedIn menyimpan hasil bacaan pertama cukup lama, dan menekan
tombol Inspect memaksanya membaca ulang. Untuk WhatsApp tidak ada alat serupa,
cara paling mudah adalah menambahkan `?v=2` di belakang alamat saat mengirim
pertama kali.

---

## 8. Cara merevisi nanti

Inilah alasan berkasnya dipisah. Mau ganti satu kalimat di portofolio, kamu
cuma menyentuh `index.html`, dashboard tidak ikut terganggu.

### Cara cepat, revisi kecil langsung di browser

1. Buka repo di GitHub, klik berkas yang mau diubah, misalnya `index.html`.
2. Klik ikon pensil di kanan atas.
3. Ubah teksnya.
4. Scroll ke bawah, tulis pesan commit, misalnya `Perbaiki typo di About`.
5. Klik **Commit changes**.

Vercel langsung mendeteksi perubahan dan memperbarui situs dalam waktu sekitar
30 detik. Tidak perlu membuka Vercel sama sekali.

### Cara aman, revisi besar

Kalau berkasnya dikerjakan ulang di komputer:

1. Buka repo, klik **Add file** lalu **Upload files**.
2. Seret berkas versi baru dengan **nama yang sama persis**.
   Nama sama artinya menimpa, bukan menambah berkas kedua.
3. Tulis pesan commit, klik **Commit changes**.

### Melihat riwayat dan membatalkan

Setiap commit tersimpan. Klik tab **Commits** di repo untuk melihat semua
perubahan beserta tanggalnya. Kalau ada revisi yang ternyata merusak tampilan,
buka commit itu lalu klik **Revert**. Situs akan kembali ke versi sebelumnya.

Ini juga alasan kenapa pesan commit sebaiknya ditulis jelas. Tiga bulan lagi,
`Update` tidak memberi tahu apa pun, sedangkan `Tambah hasil regresi di proyek 2`
langsung jelas.

---

## 9. Kalau ada yang salah

| Gejala | Penyebab | Cara perbaiki |
|---|---|---|
| Halaman 404 NOT FOUND | `index.html` tidak di lapisan paling luar, kemungkinan terunggah ke dalam folder | Buka repo. Kalau yang terlihat folder `site`, berarti salah seret. Hapus berkasnya, unggah ulang isinya saja. |
| Situs tampil tapi gambar sertifikat rusak | Folder `assets` tidak ikut terunggah, atau namanya berubah jadi `Assets` | Cek di repo apakah folder `assets` ada dan isinya dua berkas jpg. Nama folder harus huruf kecil semua. |
| Tombol "Buka analisis" jadi 404 | Berkas dashboard belum terunggah atau namanya tidak sama | Pastikan ada `analisis-emiten.html` dan `regresi-nilai-perusahaan.html`, dieja persis seperti itu. |
| Deploy gagal, muncul tulisan merah | Build Command terisi padahal harusnya kosong | Di Vercel buka **Settings** lalu **General**, kosongkan Build Command dan Output Directory, lalu **Redeploy**. |
| Sudah commit tapi situs tidak berubah | Browser menyimpan versi lama | Tekan Ctrl+Shift+R (Windows) atau Cmd+Shift+R (Mac). Kalau masih sama, cek tab **Deployments** di Vercel, pastikan deploy terbaru berstatus Ready. |
| Repo tidak muncul di Vercel | Vercel belum diberi izin ke repo itu | Di halaman impor, klik **Adjust GitHub App Permissions**, pilih repo-nya. |
| Dibagikan di LinkedIn tapi tidak ada gambarnya | `ALAMAT-SITUS-KAMU` belum diganti, atau LinkedIn masih memakai bacaan lamanya | Kerjakan langkah 7.5, lalu paksa baca ulang lewat LinkedIn Post Inspector |
| Huruf aneh seperti `â€"` | Berkas tersimpan bukan dalam UTF-8 | Jangan buka dan simpan ulang HTML pakai Notepad atau Word. Pakai editor teks biasa seperti VS Code, atau edit langsung di GitHub. |

---

## 10. Lampiran: cara pakai Git di komputer

Tidak wajib. Pakai ini kalau nanti kamu sudah nyaman dan merasa unggah lewat
browser terlalu lambat.

**Pertama kali:**

1. Install Git dari [git-scm.com](https://git-scm.com/downloads).
2. Buka Terminal (Mac) atau Git Bash (Windows).
3. Kenalkan identitasmu, cukup sekali seumur hidup:

```bash
git config --global user.name "Chelsian Adyatama"
git config --global user.email "email-github-kamu@contoh.com"
```

4. Masuk ke folder proyek lalu sambungkan ke GitHub:

```bash
cd /path/ke/folder/site
git init
git add .
git commit -m "Portofolio versi pertama"
git branch -M main
git remote add origin https://github.com/USERNAME/portofolio.git
git push -u origin main
```

Ganti `USERNAME` dengan username GitHub-mu. Saat diminta password, GitHub tidak
menerima password akun. Kamu harus membuat **Personal Access Token** lewat
Settings, Developer settings, Personal access tokens, lalu menempelkannya
sebagai pengganti password.

**Setiap kali revisi:**

```bash
git add .
git commit -m "Jelaskan perubahannya di sini"
git push
```

Tiga baris itu saja. `add` menandai berkas yang berubah, `commit` menyimpannya
sebagai satu titik riwayat, `push` mengirimnya ke GitHub. Vercel menangani
sisanya.

---

## Ringkasan satu layar

1. Daftar GitHub, bikin repo `portofolio`, Public.
2. Add file, Upload files, seret **isi** folder `site`, commit.
3. Daftar Vercel pakai akun GitHub.
4. Add New, Project, Import repo `portofolio`.
5. Framework **Other**, tiga kolom build dikosongkan, Deploy.
6. Buka alamatnya, cek di ponsel.
7. Ganti `ALAMAT-SITUS-KAMU` di ketiga berkas HTML dengan alamat aslimu,
   supaya tautannya punya gambar saat dibagikan. Lihat langkah 7.5.
8. Revisi berikutnya: edit di GitHub, commit, selesai.
