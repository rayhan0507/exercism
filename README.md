<div align="center">

# Exercism Track

**My solusi [Exercism C++ Track](https://exercism.org/tracks/cpp/exercises) — lewat Test-Driven Development.**

[![C++](https://img.shields.io/badge/-C%2B%2B17-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)](https://isocpp.org/)
[![Exercism](https://img.shields.io/badge/-Exercism-6a5eeb?style=for-the-badge&logo=exercism&logoColor=white)](https://exercism.org/tracks/cpp)
[![CMake](https://img.shields.io/badge/-CMake-064F8C?style=for-the-badge&logo=cmake&logoColor=white)](https://cmake.org/)
[![Status](https://img.shields.io/badge/-in%20progress-yellow?style=for-the-badge)]()

![Repo Views](https://komarev.com/ghpvc/?username=rayhan0507&label=Repo%20Views&color=6a5eeb&style=for-the-badge)
[![Last Commit](https://img.shields.io/github/last-commit/rayhan0507/exercism?style=for-the-badge&color=6a5eeb)](https://github.com/rayhan0507/exercism/commits/main)
[![Repo Size](https://img.shields.io/github/repo-size/rayhan0507/exercism?style=for-the-badge&color=6a5eeb)](https://github.com/rayhan0507/exercism)

</div>

---

```
download -> baca README exercise -> tulis test yg gagal -> implementasi -> test lulus -> submit
```

## Daftar Isi

- [Progress](#progress)
- [Struktur Folder](#struktur-folder)
- [Instalasi & Setup CLI](#instalasi--setup-cli)
- [Download Exercise](#download-exercise)
- [Menjalankan Code Secara Manual](#menjalankan-code-secara-manual)
- [Submit Solusi](#submit-solusi)
- [Referensi Flag CLI](#referensi-flag-cli)
- [Statistik](#statistik)
- [Tentang Exercism](#tentang-exercism)

---

## Progress

![Progress](https://progress-bar.dev/10/?title=selesai&width=350&color=6a5eeb)

| Exercise | Status | Konsep |
|---|:---:|---|
| [Pacman Rules](https://exercism.org/tracks/cpp/exercises/pacman-rules) | ✅ | `bool`, operator logika (`&&` `\|\|` `!`), precedence |
| *(exercise berikutnya)* | ⏳ | |

<details>
<summary>🏅 Legenda status</summary>
<br>

| Simbol | Arti |
|:---:|---|
| ✅ | Selesai & sudah submit |
| ⏳ | Sedang dikerjakan |
| 🔒 | Belum dibuka |

</details>

## Struktur Folder

```
exercism/
└── cpp/
    └── pacman-rules/
        ├── pacman_rules.cpp     # solusi kamu
        ├── pacman_rules.h
        ├── CMakeLists.txt       # build config bawaan Exercism
        ├── README.md            # soal
        ├── HELP.md               # cara run test
        └── test/
            ├── pacman_rules_test.cpp
            ├── catch.hpp         # framework testing (Catch2)
            └── tests-main.cpp
```

---

## Instalasi & Setup CLI

<details open>
<summary><b>1️⃣ Install Exercism CLI</b></summary>
<br>

Ikuti [Interactive CLI Walkthrough](https://exercism.org/cli-walkthrough) resmi untuk OS kamu (Windows/macOS/Linux).

Cek instalasi berhasil:
```bash
exercism version
```
</details>

<details>
<summary><b>2️⃣ Configure token</b></summary>
<br>

Ambil token dari [exercism.org/settings/api_cli](https://exercism.org/settings/api_cli), lalu:
```bash
exercism configure --token=<token-kamu>
```
</details>

## Download Exercise

```bash
exercism download --exercise=pacman-rules --track=cpp
```

Command lengkap dengan slug yang benar selalu tersedia di halaman exercise, contoh: [Pacman Rules](https://exercism.org/tracks/cpp/exercises/pacman-rules).

<details>
<summary>⚙️ Opsi tambahan saat download</summary>
<br>

| Flag | Fungsi |
|---|---|
| `--exercise=<slug>` | Nama exercise yang mau didownload |
| `--track=<slug>` | Track/bahasa (contoh: `cpp`) |
| `-t, --track` | Alias singkat dari `--track` |
| `--force` atau `-f` | Timpa file lokal tanpa konfirmasi kalau sudah ada |
| `--uuid=<uuid>` | Download solusi spesifik (punya orang lain / solusi lama) berdasarkan UUID |

```bash
# contoh: paksa download ulang meski file sudah ada
exercism download --exercise=pacman-rules --track=cpp --force
```
</details>

---

## Menjalankan Code Secara Manual

Setelah exercise ke-download, ada 2 cara buat compile & jalankan test — pakai CMake (direkomendasikan, karena sudah disiapkan Exercism) atau langsung pakai `g++`.

<details open>
<summary><b>🔧 Cara 1 — CMake (bawaan Exercism)</b></summary>
<br>

```bash
cd pacman-rules
mkdir -p build && cd build
cmake ..
make
./pacman_rules
```

Kalau ada perubahan kode, cukup ulangi `make` lagi di folder `build/` — tidak perlu `cmake ..` ulang kecuali `CMakeLists.txt` berubah.
</details>

<details>
<summary><b>⚙️ Cara 2 — Compile manual pakai g++</b></summary>
<br>

```bash
g++ -std=c++17 -Wall -I test \
  pacman_rules_test.cpp \
  pacman_rules.cpp \
  test/tests-main.cpp \
  -o pacman_rules_test

./pacman_rules_test
```

- `-I test` → supaya compiler nemu `catch.hpp` di folder `test/`
- `-std=c++17` → standar C++ yang dipakai Exercism track ini
- Binary hasil compile bisa dijalankan langsung tanpa argumen tambahan
</details>

<details>
<summary><b>🐛 Kalau cuma test pertama yang jalan</b></summary>
<br>

File test C++ di Exercism biasanya membungkus test lanjutan dengan:
```cpp
#if defined(EXERCISM_RUN_ALL_TESTS)
```
Pindahkan baris itu ke atas test berikutnya satu per satu — sesuai prinsip TDD (RED → GREEN → REFACTOR) — jangan buka semua test sekaligus.
</details>

---

## Submit Solusi

```bash
exercism submit pacman_rules.cpp
```

Bisa juga submit beberapa file sekaligus:
```bash
exercism submit pacman_rules.cpp pacman_rules.h
```

Command ini upload solusi ke Exercism dan mencetak link ke halaman solusi kamu. Solusi belum sempurna pun boleh disubmit — berguna buat lihat solusi orang lain atau minta mentoring.

---

## Referensi Flag CLI

<details>
<summary>📖 Flag global (berlaku di semua command)</summary>
<br>

| Flag | Fungsi |
|---|---|
| `-h, --help` | Tampilkan bantuan untuk command tsb |
| `-v, --verbose` | Tampilkan log detail (debug mode) — berguna kalau download/submit gagal |
| `--timeout=<detik>` | Ubah batas waktu request ke API Exercism |

```bash
exercism -h                 # lihat semua command yang tersedia
exercism download -h        # lihat opsi khusus command download
exercism download --exercise=pacman-rules --track=cpp --verbose
```
</details>

<details>
<summary>🧰 Command lain yang sering dipakai</summary>
<br>

| Command | Fungsi |
|---|---|
| `exercism help` | Daftar lengkap semua command |
| `exercism version` | Cek versi CLI yang terpasang |
| `exercism workspace` | Tampilkan path folder workspace lokal |
| `exercism open <slug>` | Buka halaman exercise di browser |
| `exercism troubleshoot` | Diagnosa masalah CLI (buat lampiran issue GitHub) |
</details>

---

## Statistik

<div align="center">

![Streak](https://streak-stats.demolab.com?user=rayhan0507&theme=tokyonight&hide_border=true)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=rayhan0507&layout=compact&theme=tokyonight&hide_border=true)

</div>

> Ganti `rayhan0507` di URL widget kalau username GitHub kamu berbeda.

---

## Tentang Exercism

[Exercism](https://exercism.org) adalah platform belajar coding gratis dengan 65+ bahasa pemrograman dan mentoring dari komunitas. Setiap solusi diverifikasi lewat test otomatis sebelum bisa direview mentor.

---

<div align="center">

Dibuat oleh **[rayhan0507](https://github.com/rayhan0507)** · ⭐ kasih star kalau membantu

</div>
