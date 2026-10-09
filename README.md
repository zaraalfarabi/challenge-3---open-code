# CHALLENGE - OpenCode Harness & AGENTS.md

## 1. Memeriksa Lokasi dan Struktur Project

```powershell
pwd
Get-ChildItem
```

## 2. Memeriksa Instalasi OpenCode

```powershell
opencode.cmd --version
where.exe opencode
```

## 3. Memeriksa Node.js, npm, dan TypeScript

```powershell
node --version
npm.cmd --version
npx.cmd tsc --version
```

## 4. Memeriksa Model OpenCode

```powershell
opencode.cmd models
```

Pastikan `opencode/big-pickle` tersedia.

## 5. Menjalankan OpenCode pada Project 

```powershell
opencode.cmd --model opencode/big-pickle
```

Prompt:

```text
Baca struktur project ini dan jelaskan file serta konfigurasi TypeScript yang sudah tersedia. Jangan mengubah atau membuat file apa pun dulu. Sebutkan juga instruksi project yang kamu temukan, termasuk AGENTS.md jika ada.
```

Keluar dari OpenCode:

```text
/exit
```

## 6. Menampilkan Isi AGENTS.md

```powershell
Get-Content AGENTS.md
```

Alternatif membuka file:

```powershell
notepad AGENTS.md
```

## 7. Memverifikasi Project Tanpa AGENTS.md

Pindah ke folder salinan:

```powershell
cd ..\task-tracker-no-agents
```

Periksa keberadaan file instruksi:

```powershell
Test-Path AGENTS.md
```

Hasil yang diharapkan:

```text
False
```

Tampilkan struktur project:

```powershell
Get-ChildItem
```

## 8. Menjalankan OpenCode Tanpa AGENTS.md

```powershell
opencode.cmd --model opencode/big-pickle
```

Prompt pembanding:

```text
Analisis struktur project Task Tracker ini dan buat rencana implementasi CLI dengan perintah add, list, done, dan remove. Pecah rencana menjadi file-file kecil di dalam src/. Jangan mengubah atau membuat file apa pun. Sebutkan asumsi, risiko, dan edge case yang perlu diperhatikan.
```

Keluar dari OpenCode:

```text
/exit
```

## 9. Kembali ke Project Asli

```powershell
cd ..\task-tracker
```

## 10. Verifikasi TypeScript

Menjalankan typecheck:

```powershell
npm.cmd run typecheck
```

Menjalankan build:

```powershell
npm.cmd run build
```

## 11. Memeriksa Status Git

```powershell
git status --short
```

## 12. Kesimpulan Eksperimen

Berdasarkan pengujian, OpenCode mampu menganalisis struktur proyek dan menyusun rencana implementasi CLI, baik dengan maupun tanpa file AGENTS.md. Namun, ketika AGENTS.md tersedia, agent memperoleh instruksi proyek yang lebih spesifik mengenai standar penulisan kode, validasi data, penggunaan dependency, dan proses verifikasi. Tanpa file tersebut, agent tetap dapat memberikan rencana yang terstruktur, tetapi tidak merujuk pada aturan khusus yang telah ditetapkan dalam file tersebut. Dengan demikian, AGENTS.md berfungsi sebagai panduan untuk membantu agent bekerja sesuai standar dan batasan proyek.
