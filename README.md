# mrg_tool - Tsukihime Remake (Switch) Script Extractor & Repacker

Tool Python untuk mengekstrak dan melakukan *repack* file `script_text.mrg` dari Tsukihime Remake (Nintendo Switch). Tool ini membaca format arsip MZP (`mrgd00`) dan mendukung encoding UTF-8 untuk mempermudah proses translasi visual novel.

**CATATAN PENTING:**
Saat ini, teks yang diekstrak masih acak dan belum disortir. Baris dialog belum dibagi per rute. Jika proses penyortiran sudah selesai di masa mendatang, teks akan dikelompokkan ke dalam direktori masing-masing (contoh: rute Arcueid, rute Ciel, dst).

## Preview Terjemahan

* **Sebelum (Original):** ![Sebelum](https://i.imgur.com/Fl6iTqW.png)

* **Sesudah (Indonesia):** ![Sesudah](https://i.imgur.com/eEtdYFB.jpeg)

## Cara Penggunaan

Pastikan kamu sudah menginstal Python 3. Tool ini tidak memerlukan *library* eksternal tambahan.

### GUI Mode
Cara paling mudah, jalankan skrip tanpa argumen untuk membuka tampilan antarmuka:
```bash
python mrg_tool.py
