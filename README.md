# TsukiRe-Translator & mrg_tool

Kumpulan alat (tools) untuk proses lokalisasi game **Tsukihime -A piece of blue glass moon-** (Nintendo Switch). Mendukung ekstraksi, pengeditan teks secara langsung (GUI), hingga pengemasan ulang (*repacking*) ke format aslinya.

---

## 1. TsukiRe-Translator (GUI Editor)
Alat utama untuk menerjemahkan tanpa perlu berurusan dengan file teks mentah secara manual. Memungkinkan pengeditan langsung dengan tampilan dua kolom yang intuitif.

### Preview Interface
<p align="center">
  <kbd>
    <img src="https://i.imgur.com/wxw2gl5.png" width="750" alt="GUI Preview">
  </kbd>
</p>

**Fitur:**
- **Visual Divider:** Garis pemisah vertikal antara kolom Original dan Translation untuk keterbacaan maksimal.
- **Direct Editing:** Klik dua kali pada kolom terjemahan untuk mengedit teks secara instan.
- **Route Tree:** Navigasi berdasarkan rute (**Arcueid**, **Ciel**, **Common**) yang sudah disortir otomatis menggunakan `scene_map.json`.
- **Live Search:** Mencari baris dialog tertentu dengan cepat menggunakan kata kunci.
- **Project System:** Menyimpan progres kerja dalam format `.tsproj` sebelum di-patch ke game.

---

## 2. mrg_tool (CLI & GUI Extractor)
Tool teknis untuk menangani ekstraksi dan injeksi file `script_text.mrg` (format MZP/mrgd00).
**Repository:** [Jannabie/TsukiRe-mrg-txt](https://github.com/Jannabie/TsukiRe-mrg-txt)

### Perbandingan Hasil Patch
<div align="center">
  <table style="margin-left: auto; margin-right: auto;">
    <tr>
      <td align="center"><b>Sebelum (Original)</b></td>
      <td align="center"><b>Sesudah (Indonesian Patch)</b></td>
    </tr>
    <tr>
      <td><kbd><img src="https://i.imgur.com/Fl6iTqW.png" width="350"></kbd></td>
      <td><kbd><img src="https://i.imgur.com/eEtdYFB.jpeg" width="350"></kbd></td>
    </tr>
  </table>
</div>

### Preview Format Teks (.txt)
Jika Anda lebih suka pengeditan manual via teks editor (VS Code/Notepad++), hasil ekstraksinya tetap mempertahankan struktur offset:
<p align="center">
  <kbd>
    <img src="https://i.imgur.com/yALew5y.png" width="450" alt="Preview TXT">
  </kbd>
  <br>
  <i>Hasil ekstraksi mempertahankan ID Offset agar proses repack tetap presisi.</i>
</p>

---

## Penjelasan Teknis Repacker
Sistem pengemasan ulang pada tool ini memastikan stabilitas game dengan:
- **Auto-Offset Calculation:** Menghitung ulang seluruh tabel pointer secara otomatis saat panjang teks berubah (mencegah game *crash*).
- **10-Section Management:** Rekonstruksi 10 bagian utama arsip MZP termasuk penyelarasan byte (*alignment*) yang sangat presisi.
- **Sector Precision:** Mengikuti standar sektor `0x800` untuk kompatibilitas penuh pada emulator maupun hardware Switch asli.

---

## Cara Penggunaan

### A. Menggunakan Translator GUI (Rekomendasi)
1. Jalankan `tsuki_trans.py`.
2. Buka file `script_text.mrg`.
3. Pilih rute/scene pada panel kiri, lalu mulai menerjemahkan di kolom kanan.
4. Gunakan menu **File > Patch MRG** untuk menerapkan terjemahan ke file game.

### B. Menggunakan mrg_tool (Manual)
**Ekstrak ke TXT:**
```bash
python mrg_tool.py extract script_text.mrg output.txt
