# Projekku — Panduan Pemula

Panduan ini untuk orang yang **belum pernah memakai AI sama sekali**. Tidak perlu install apa pun, tidak
ada biaya, tidak ada kunci API. Cukup satu folder dan satu tool AI.

Folder `` bisa dipakai di **AI agent apa pun** — dari yang baca `AGENTS.md` langsung, sampai yang
tidak punya fitur skill sama sekali. Bagian 3 dan 4 menjelaskan cara memasangnya di tiap tool.

## 🤖 Kamu adalah AI agent? Lewati bagian lain.

Kalau kamu agent dan diberi link ke file ini, lakukan empat langkah ini dan berhenti. Tidak perlu
menanyakan izin dulu, tidak perlu install apa pun, dan jangan mengubah isi file-nya.

**1. Ambil repo-nya.** Ganti `<user>` dengan nama akun GitHub kamu, lalu jalankan:

```sh
git clone https://github.com/<user>/agent-pack.git agent-pack
```

Kalau `git` tidak tersedia, unduh repo ini sebagai ZIP, lalu ekstrak. Hasilnya sama saja.

**2. Pasang ke tool tempat kamu berjalan.** Salin isi `agent-pack/` ke root project yang sedang kamu
kerjakan, lalu buat file penunjuk sesuai tabel di bawah.

| Tool tempat kamu berjalan | Yang harus kamu buat |
|---|---|
| Antigravity, Codex, Gemini CLI | Tidak perlu apa-apa |
| Claude Code | `CLAUDE.md` berisi satu baris: `@AGENTS.md` |
| OpenHands | `.openhands/microagents/repo.md` berisi satu baris: `@AGENTS.md` |
| Cursor | `.cursorrules` berisi satu baris: `@AGENTS.md` |
| Windsurf | `.windsurfrules` berisi satu baris: `@AGENTS.md` |
| Hermes | Setelah menyalin, jalankan `hermes skills trust` sekali |
| Tool lain | Buat file instruksi yang paling umum dibaca tool itu, isi: `Baca AGENTS.md dan SOUL.md sebelum menjawab.` |

**3. Baca dua file itu sekarang.** `AGENTS.md` sepenuhnya, dan `SOUL.md`. Kamu harus tahu isi
aturannya, bukan cuma menyalin namanya.

**4. Verifikasi, lalu lapor.** Jawab pertanyaan ini ke user: "apa yang bisa kamu lakukan?" Kalau jawabanmu
menyebut aturan dari `AGENTS.md`, pemasangan berhasil. Kalau tidak, sebut file mana yang gagal dibaca.

**Yang tidak boleh kamu lakukan:**

- Jangan menyalin isi `AGENTS.md` atau `SOUL.md` ke file lain. Dua salinan akan berbeda, dan yang berbeda
  itu yang dipakai — bukan yang benar.
- Jangan mengedit isi file di ``. Kalau ada aturan yang tidak cocok, katakan ke user, jangan
  ubah diam-diam.
- Jangan menghapus `MEMORY.md` atau `memory/`. Itu isinya, bukan cache.

Kalau user memberi link README ini tanpa instruksi lain, empat langkah di atas sudah dianggap sebagai
permintaan. Kerjakan, lalu lapor hasilnya singkat.

**Kalau user mau pack-nya dipakai permanen** (bukan sekali), tanyakan satu hal saja: folder di mana.

### Cara paling cepat — salin kalimat ini ke chat AI-mu

```
Pasang agent pack ini untuk project ini: <LINK README INI>
Baca bagian "Kamu adalah AI agent?", lalu ikuti persis.
```

Link README-nya: `https://github.com/<user>/agent-pack/blob/main/README.md` — ganti `<user>` dengan nama akun GitHub kamu.

---

## 1. Sebenarnya apa ini?

Bayangkan kamu punya asisten yang sudah hafal cara kerjamu, ingat keputusan minggu lalu, dan tahu aturan
mainmu. Assistantship itu sebenarnya cuma **beberapa file teks**. Tanpa kode, tanpa database, tanpa biaya
tambahan. Kalau file-nya dihapus, tidak ada yang tersisa.

Jadi "AI agent" itu dua hal yang digabung:

- **Model AI** = otaknya. Otak itu kuat tapi **lupa**: setiap sesi baru, dia mulai dari nol.
- **File markdown** = catatan yang selalu menempel di otaknya. Inilah yang bikin dia terasa "_AH_": nama
  kamu, aturan kamu, memori kamu, dan modul kebiasaan yang dia pakai saat dibutuhkan.

Kita tidak membangun otaknya. Kita hanya menempelkan catatannya.

## 2. Isi repo

```
agent-pack/
├── SOUL.md          siapa dia, cara bicara, apa yang dia tolak
├── AGENTS.md        aturan kerja, gaya kerja, memori, batasannya
├── MEMORY.md        fakta penting yang harus diingat
├── memory/          catatan harian
└── .agents/skills/  9 modul kebiasaan kerja
```

| File | Ukuran | Dipakai ketika |
|------|--------|---------------|
| `SOUL.md` | 3,2 KB | Selalu. Ini kepribadiannya. |
| `AGENTS.md` | 9,6 KB | Selalu. Ini otak prosedurnya. |
| `MEMORY.md` | 0,9 KB | Hanya sesi utama, bukan subagent. |
| 9 modul skill | 2,2 KB | Hanya ketika cocok. |

Total yang menempel di kepala AI: **sekitar 16.000 karakter**. Tidak banyak.

**Repo ini bisa dipakai di mana saja.** Semua path di dalamnya relatif, jadi boleh di-clone ke mana pun,
disalin ke dalam project lain, atau diberi nama lain. Tidak ada yang bergantung pada nama folder.

## 3. Cara pasang — tool yang langsung baca

Kalau tool-mu salah satu di bawah ini, **tidak perlu apa-apa**. Salin folder `` ke project-mu,
atau buka tool langsung di folder itu.

| Tool | Yang perlu dilakukan |
|------|---------------------|
| **Antigravity** | Buka folder. Selesai. |
| **Codex** | Buka folder. Selesai. |
| **Gemini CLI** | Buka folder. Selesai. |
| **Claude Code** | Salin folder, lalu buat `CLAUDE.md` di root project berisi satu baris: `@AGENTS.md` |
| **OpenHands** | Salin folder, lalu buat `.openhands/microagents/repo.md` berisi satu baris: `@AGENTS.md` |
| **Hermes** | Salin folder, lalu jalankan sekali di dalamnya: `hermes skills trust` |

Cek nyala: ketik `apa yang bisa kamu lakukan?`. Kalau jawabannya tahu aturanmu, sudah benar.

## 4. Cara pasang — tool yang butuh file penghubung

Tool di bawah ini tidak membaca `AGENTS.md` sendiri. Buat file kecil di root project, isinya cuma penunjuk.
Jangan menyalin isi `AGENTS.md` ke sana — satu salinan akan lama-lama basi, dan yang basi justru yang
dipakai AI.

| Tool | Nama file | Isi file |
|------|-----------|----------|
| **Cursor** | `.cursorrules` | `@AGENTS.md` |
| **Windsurf** | `.windsurfrules` | `@AGENTS.md` |
| **Aider** | `CONVENTIONS.md` | `Baca AGENTS.md, SOUL.md, dan MEMORY.md. Bacaan tidak diedit.` |
| **GitHub Copilot** | `.github/copilot-instructions.md` | `Baca AGENTS.md dan SOUL.md sebelum menjawab.` |

Untuk Aider, tambahkan juga di `.aider.conf.yml`:

```yaml
read:
  - AGENTS.md
  - SOUL.md
  - MEMORY.md
```

Tambahkan `memory/` (bukan `MEMORY.md`) kalau kamu mau catatan harian ikut terbaca.

## 5. Kalau tool-mu tidak ada di tabel

Almost semua tool menerima instruksi lewat file. Ambil cara paling umum:

1. Salin isi `agent-pack/` ke dalam project-mu.
2. Buat file instruksi yang paling umum dibaca tool itu, isinya: `Baca AGENTS.md dan SOUL.md di dalam
   agent-pack sebelum menjawab.`
3. Uji dengan `apa yang bisa kamu lakukan?`

Kalau tool-nya benar-benar tidak punya file instruksi, salin saja isi `AGENTS.md` dan `SOUL.md` ke dalam
system prompt atau custom instructions miliknya. Dua file itu mandiri, tidak butuh file lain.

## 6. Langkah 1 — cek nyala

Buka tool AI-mu di folder ini, lalu ketik:

```
apa yang bisa kamu lakukan?
```

Kalau jawabannya menunjukkan dia tahu aturanmu, berarti sudah membaca `AGENTS.md`.

## 7. Langkah 2 — pakai seperti asisten biasa

| Kamu ketik | Yang terjadi |
|---|---|
| "hapus file `a.txt`" | Dilakukan langsung, tanpa bertanya |
| "kenapa `npm install` gagal?" | Mode debug: reproduksi dulu, baru perbaiki |
| "query SQL ini lambat, kenapa?" | Modul `data` dimuat otomatis |
| "deploy ke server" | Berhenti dan bertanya, karena keluar dari mesin |
| "tulis README untuk tool ini" | Modul `content` dimuat otomatis |

Kamu **tidak perlu menyebut nama modunya**. Dia memilih sendiri dari isi kalimatmu. Kalau salah, dia
menyebut modul mana yang dipakai.

## 8. Tiga mode yang bisa kamu panggil

- **deep** — untuk keputusan besar. Dia membandingkan beberapa opsi dulu sebelum memilih.
  Contoh: `deep: pakai Postgres atau SQLite?`
- **debug** — untuk error yang belum ketemu. Reproduksi dulu, baru perbaiki, dan meninggalkan satu
  pengecekan supaya bug yang sama Ketahuan kalau balik lagi.
- **review** — untuk menilai kode orang lain. Hanya daftar temuan, tanpa pujian, tanpa saran di luar
  lingkup.

## 9. Batasnya: boleh dan tidak boleh

Ini bagian paling penting, karena "_nya_" tidak akan berhenti sendiri di hal yang berbahaya.

**Dikerjakan langsung, tanpa bertanya** — semua pekerjaan lokal: hapus file, `git reset --hard`, drop
database, hapus kode milikmu sendiri, install paket, jalankan test, ubah konfigurasi.

**Selalu berhenti dan bertanya** — yang keluar dari mesin atau tidak bisa dibatalkan:

- push, deploy, kirim email, kirim pesan, posting ke mana pun
- hal yang mengeluarkan uang
- server produksi, database di luar folder ini
- password, API key, file kredensial

Kalau kamu setuju, dia lanjut. Kalau tidak, dia berhenti.

Lima kasus yang abu-abu sudah ditulis jelas di `AGENTS.md` bagian `Autonomy`. Tidak perlu dihafal, tapi
baca sekali kalau kamu sering menyuruh pekerjaan berisiko.

## 10. Memory — supaya tidak lupa

Dua tempat catatan:

- `memory/2026-09-30.md` — catatan harian: apa yang dikerjakan, apa yang rusak, apa yang diputuskan.
- `MEMORY.md` — fakta yang masih relevan setelah seminggu. Satu baris per fakta.

Akhir setiap task, dia menulis satu baris: **apa yang tadi salah, dan masuk ke file mana**. Contoh:
`2026-09-30 — install tanpa --user gagal di Termux, pakai --user`.

Kalau `_nya lupa`_ dan kamu tidak suka, isi sendiri `MEMORY.md`. Baca lagi dari awal di sesi berikutnya.

## 11. Sembilan modul

Dia memilih sendiri. Ini supaya kamu tahu saja:

| Modul | Dipakai kalau kamu bilang |
|-------|--------------------------|
| `business` | harga, untung-rugi, worth it atau tidak, produk |
| `coding` | menulis, mengubah, memperbaiki kode |
| `content` | menulis dokumen, README, commit message |
| `vps` | server, SSH, deploy, TLS, firewall |
| `automation` | cron, script, pekerjaan otomatis |
| `api` | endpoint, REST, webhook, token |
| `data` | SQL, database, migrasi, query lambat |
| `files` | memindah, menghapus, merapikan file |
| `web` | HTML, CSS, halaman web, tampilan |

Yang bikin hemat: yang menempel di kepala AI cuma **satu baris deskripsi per modul**. Isi modulnya baru
dimuat kalau cocok. Total 2,2 KB, bukan 15 KB.

## 12. Batasnya — baca juga

- **File ini bukan sihir.** Cuma instruksi. Instruksi yang salah menghasilkan jawaban yang salah. README
  ini sendiri sudah salah beberapa kali dan diperbaiki.
- **Batas 12.000 karakter per file.** Kalau `AGENTS.md` lewat, ujung file hilang tanpa pesan error dan
  aturannya ikut hilang. Cek dengan: `wc -c ""*.md`
- **Tidak ada install, tidak ada biaya, tidak ada kunci API.**
- **Tidak ada yang berjalan otomatis.** Perulangan perbaikan itu atas permintaan: kalau diminta, dia
  jalan; kalau lupa, ya lupa.

## 13. Kalau ada yang aneh

| Gejala | Penyebab | Perbaikan |
|--------|---------|-----------|
| Aturan diabaikan | Tool tidak membaca `AGENTS.md` | Buat file penghubung (bagian 3 atau 4) |
| Terus bertanya | Permintaan keluar dari mesin | Jawab permintaannya, atau bilang langsung saja |
| Modul tidak terlihat | Tool tidak punya fitur skill | Minta dia baca `.agents/skills/<nama>/SKILL.md` |
| Aturan menghilang | File lewat 12.000 karakter | `wc -c ""*.md` |
| Lupa di sesi lalu | Memory belum ditulis | Isi `MEMORY.md` sendiri |

---

Ringkasnya: **`SOUL.md` dan `AGENTS.md` adalah dua file yang wajib**, sisanya opsional. Kalau hanya mau
agent yang tidak ngomong nonsense, dua file itu sudah cukup.
