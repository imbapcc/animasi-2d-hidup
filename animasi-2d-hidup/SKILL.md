---
name: "animasi-2d-hidup"
description: "Buat video animasi 2D (HyperFrames) dengan tokoh yang bergerak hidup: kedip, rambut bergoyang, mulut ikut suara, jalan menapak, jari mengetik, gerakan halus sesuai emosi dan cerita."
---

# Animasi 2D Hidup

Pakai skill ini setiap kali diminta membuat video dengan tokoh kartun/anime 2D yang **bergerak**, bukan gambar diam yang cuma digeser atau diperbesar. Standarnya adalah video "Stop Judol yang lain!!! CopetBandar – Sahabat" versi 2D kafe: tokoh noleh saat ada alasan, kedip, rambut bergoyang, jempol mengetuk HP, teman berjalan masuk, mulut ikut suara, menangis dengan kepala menunduk pelan.

Semua gerakan harus halus, alami, dan **mengikuti perasaan serta kejadian di cerita**. Kerjakan semaksimal mungkin dengan alat yang ada.

## Pesan penutup CopetBandar (wajib)

- Kalimat penutup **hanya** "**Main CopetBandar aja.**" Boleh diawali kalimat yang sesuai cerita ("Lho, dompetku kok kosong?…", "Bos… tinta aja nggak kebeli."), tapi bagian CopetBandar-nya cukup "Main CopetBandar aja."
- **Jangan pernah** menambahkan "nggak pakai deposit, nggak ada yang dicopet" atau kalimat sejenis, baik di suara, subtitle, teks di layar, maupun kartu logo.
- Kartu logo di akhir: logo asli CopetBandar di layar HP, tulisan kecil "STOP JUDOL", dan satu baris "Main CopetBandar aja." Tidak ada teks lain.

## Setiap video harus beda

Kalau membuat banyak video (misalnya seri harian), yang sama hanya logo dan pesan CopetBandar. Selebihnya beda di setiap video:
- **Tokoh**: bentuk badan (kurus/normal/gendut), umur, rambut (pendek, gondrong, kuncir, sanggul, botak, hijab), topi (helm ojol, topi satpam, topi koki, caping, peci, kupluk), kumis, kacamata, baju.
- **Latar** dan benda-benda di dalamnya, masing-masing dengan gerakan kecilnya sendiri.
- **Tampilan judol di HP**: slot buah, pop-up bonus, slot petir, saldo e-wallet, roda putar, taruhan bola, notifikasi deposit, dsb. Jangan pakai layar yang sama.
- **Alur dan penutup**: jangan selalu "main judol → nangis → dinasihati". Variasikan siapa yang menyampaikan pesan (tokoh itu sendiri, nenek, printer yang bisa bicara, narator, robot) dan cara ngomongnya.
- **Musik**: tempo, nada, dan instrumen sesuai suasana (dangdut, tegang, ceria, lo-fi).

## Aturan gerakan (wajib)

**Selalu ada pada setiap tokoh yang tampil:**
- **Kedip**: tiap 2–4 detik, waktunya tidak rata (misalnya 1,9 s, 4,3 s, 6,0 s). Mata dipipihkan `scaleY 1 → 0.08 → 1` dalam ±0,14 detik.
- **Rambut bergoyang**: poni, helai samping dan rambut belakang masing-masing berayun pelan dengan periode berbeda (0,7–1,2 s) supaya tidak serempak. Kalau tokoh pakai topi/hijab, ujung kain atau topinya yang bergoyang.
- **Napas/idle**: badan naik-turun 2–4 px, periode ±1,1–1,4 s. Tokoh tidak pernah benar-benar diam.
- **Mulut ikut suara**: setiap kali tokoh bicara, mulut membuka-tutup mengikuti keras-pelannya suara aslinya (lihat Lip-sync). Tidak boleh buka-tutup dengan irama tetap. Saat diam, mulut tertutup. Benda yang "bicara" (printer, robot) juga punya "mulut" yang ikut suara.

**Hanya kalau ada alasannya di cerita:**
- **Noleh**: kalau ada orang datang, ada suara, atau dipanggil, tokoh menoleh ke arah itu (kepala berputar 5–8°, wajah bergeser ke arah itu, bola mata ikut). Jangan noleh terus tanpa sebab.
- **Pusing/bingung**: kepala noleh ke sana-sini dan geleng-geleng (rotasi ±8° bolak-balik 3–4 kali, makin pelan), bisa ditambah tangan menepuk dahi ("aduh"): lengan naik dalam lengkung, telapak menyentuh dahi, kepala sedikit terdorong ke belakang, lalu tangan turun pelan.
- **Menangis/sedih**: kepala menunduk **pelan** (0,6–1,0 s, ease `power2.inOut`), bahu turun, alis miring sedih, mulut melengkung ke bawah, air mata muncul lalu menetes turun pipi.
- **Kaget**: mata membesar cepat (`back.out`), bola mata mengecil, alis naik, mulut "O", badan tersentak sedikit ke atas; lalu lemas.
- **Senang/lega**: alis naik sedikit, mulut tersenyum, kepala sedikit miring.

**Aktivitas harus kelihatan nyata:**
- **Berjalan**: kaki melangkah **menapak tanah, tidak melayang**. Kaki berayun dari pinggul bergantian, lengan berayun berlawanan dengan kaki, badan naik-turun dua kali per siklus langkah (naik saat kaki lurus di bawah). Kecepatan geser badan harus cocok dengan panjang langkah, supaya kaki tidak terlihat meluncur. Saat berhenti, kaki dan lengan kembali tegak dengan halus. Jalan mengendap (copet/maling) memakai langkah kecil dan badan sedikit naik-turun.
- **Mengetik/mengetuk HP**: jempol atau jari bergerak naik-turun cepat (0,08–0,12 s per ketukan) dan benar-benar menyentuh tombol: tombol mengecil sedikit, ada riak/efek di layar, dan isi layar berubah. Tambah bunyi tap.
- **Mengambil benda (misal HP, dompet)**: gerakan melengkung (bukan garis lurus), ada antisipasi kecil sebelum bergerak, `power2.inOut`, tangan mendahului dan benda ikut, lalu sedikit menetap (overshoot kecil) di tujuan.
- **Menepuk bahu**: lengan menjangkau dalam lengkung, tangan menepuk 2 kali (turun-naik cepat), orang yang ditepuk ikut terguncang sedikit.

**Prinsip halus:**
- Hampir tidak ada gerakan `linear`; pakai `sine.inOut`, `power2.inOut`, `power3.out`, `back.out` sesuai sifat gerakan.
- Bagian tubuh tidak bergerak serempak: kepala sedikit mendahului badan, rambut menyusul belakangan (follow-through).
- Kamera juga hidup: dorong pelan (scale 1 → 1,05–1,08 sepanjang adegan) dan ganti sudut tiap 3–5 detik (wide → close-up tangan → close-up wajah).

## Cara membuat tokoh

Pakai HyperFrames (baca skill `hyperframes` dulu). Tokoh digambar sebagai **SVG berlapis**, tiap bagian punya `id` sendiri supaya bisa digerakkan:

```
<svg id="{p}-svg" viewBox="-300 -380 600 1200" ...>   // titik (0,0) = pangkal leher
  rambut-belakang, kaki-kiri, kaki-kanan
  <g id="{p}-upper"> badan, lengan (beberapa versi pose, ditukar dengan opacity)
    <g id="{p}-head"> leher, wajah
      <g id="{p}-face"> alis, <g id="{p}-eyes"> mata+iris </g>, hidung, mulut-tutup, mulut-buka, air mata </g>
      helai-kiri, helai-kanan, <g id="{p}-fringe"> poni </g>, topi
    </g>
  </g>
</svg>
```

- **Satu `<svg>` per tokoh**, diposisikan dengan CSS `left/top` dan diskalakan dengan `width/height`. Jangan menaruh `transform` pada grup induk, karena itu merusak titik putar.
- Titik putar SVG selalu pakai **`svgOrigin: "x y"`** dalam koordinat viewBox tokoh itu (misalnya kepala `"0 -20"`, pinggul kiri `"-45 292"`, bahu `"-112 40"`). **Jangan** pakai `transformOrigin` dengan px pada elemen SVG: kepala bisa lepas dari badan.
- Beri awalan id unik per tokoh dan per adegan (`c5d-`, `c5f-`), supaya tidak ada id kembar dalam satu halaman.
- Siapkan beberapa versi ekspresi (alis normal/sedih/marah, mulut tegang/sedih/senyum/O) dan pose lengan (tergantung, pegang HP, menepuk dahi, melambai, menjangkau), lalu tukar dengan `opacity`.
- Tokoh dibuat dari pilihan (badan, rambut, topi, kumis, kacamata, kerutan, warna baju) supaya setiap video punya tokoh yang benar-benar berbeda. Tokoh cowok berambut gondrong diberi alis tebal, poni berduri, dan bayangan jenggot supaya tidak terlihat seperti cewek.
- Gaya: anime/kartun 2D yang rapi, warna rata dengan satu bayangan, mata besar dengan kilau putih, pipi merona. Tokoh yang sama harus terlihat sama di semua adegan (warna baju, rambut, wajah).
- Latar juga digambar SVG dan diberi gerak kecil: lampu berkedip, uap kopi naik, daun bergoyang, kipas berputar, ombak, sinar matahari.

## Lip-sync dari suara

1. Buat suara dengan Edge TTS (`id-ID-ArdiNeural` cowok, `id-ID-GadisNeural` cewek). Bedakan tokoh dengan `--pitch` dan `--rate` (nenek: lebih rendah dan pelan; anak muda: lebih tinggi dan cepat; benda/robot: tambah efek ffmpeg seperti `aecho`). Di cloud harus lewat proxy:
   ```bash
   uvx edge-tts --proxy "$HTTPS_PROXY" --voice id-ID-GadisNeural --rate=+8% \
     --text "..." --write-media vo.mp3 --write-subtitles vo.vtt
   ```
   File `.vtt` dipakai untuk waktu subtitle.
2. Hitung kerasnya suara tiap 0,08 detik:
   ```python
   raw = subprocess.run(['ffmpeg','-v','error','-i','vo.mp3','-ac','1','-ar','8000','-f','s16le','-'], capture_output=True).stdout
   x = np.frombuffer(raw, np.int16).astype(float) / 32768
   step = int(8000 * 0.08)
   v = [np.sqrt(np.mean(x[i:i+step]**2)) for i in range(0, len(x), step)]
   m = max(v); env = [min(1, a/m*1.4) if a/m > 0.08 else 0 for a in v]
   ```
3. Gerakkan mulut-buka dengan nilai itu, mulai tepat saat suara mulai:
   ```js
   env.forEach((v, i) => tl.to("#f-mouthO", { scaleY: Math.max(0.05, v), duration: 0.08, ease: "none" }, start + i * 0.08));
   ```
   Tulis tween-nya langsung di file (hasil generate), jangan dihitung di browser. Titik putar mulut di bibir atas (`svgOrigin`).

Saat tokoh bicara, tambahkan juga kepala yang sedikit miring bolak-balik dan alis yang ikut ekspresi, supaya tidak cuma mulut yang bergerak.

## Suara dan teks

- Musik latar pelan (bisa disintesis dengan numpy), volume ±0,3, fade in/out; gaya musik beda tiap video.
- Efek suara untuk setiap aksi yang terlihat: tap HP, koin, langkah kaki, langkah mengendap, tepukan, bunyi error, sirine, desis, peluit, burung, ombak, "whoosh" untuk logo.
- Subtitle untuk semua ucapan (penonton sering menonton tanpa suara), ditaruh di area aman, memakai strip gelap.
- Video vertikal 9:16 (1080 × 1920): teks dan logo di antara y 168 dan 1330 px. Judul dan label jangan saling tumpuk.

## Langkah kerja

1. Pecah cerita jadi adegan 3–5 detik, dan tulis gerakan + emosi tiap tokoh per adegan sesuai aturan di atas.
2. Buat suara dan hitung amplop lip-sync.
3. Tulis generator Python yang menghasilkan file adegan HyperFrames (tokoh = fungsi yang mengembalikan SVG dengan awalan id), supaya tokoh konsisten di semua adegan.
4. `npx hyperframes check --json` (perbaiki semua error), lalu `npx hyperframes snapshot --at ...` di momen penting dan **lihat gambarnya**: kepala menempel ke badan, kaki menapak, tangan tidak menutupi teks, mulut terbuka saat bicara.
5. Kirim pratinjau (contact sheet) dulu. Render MP4 setelah disetujui atau kalau diminta langsung.

## Render di cloud (yang sudah terbukti)

- Simpan GSAP di proyek (`npm pack gsap@3.15.0` → `assets/gsap.min.js`), karena browser render tidak bisa mengambil dari CDN.
- Pakai Chromium bawaan:
  ```bash
  HYPERFRAMES_BROWSER_PATH=$(node -e "console.log(require('playwright').chromium.executablePath())") \
    npx hyperframes render -o hasil.mp4 --quiet
  ```
- Ambil beberapa frame dari MP4 dengan ffmpeg dan periksa sebelum dikirim.

## Batasan yang harus jujur disampaikan

Gerakan ini dibuat dengan menggerakkan bagian-bagian gambar 2D, bukan video AI. Hasilnya hidup, tetapi tidak sehalus klip anime buatan generator video AI (Kling, Hailuo, dsb.). Kalau pengguna mau sehalus itu, sarankan membuat klip di aplikasi tersebut lalu gabungkan di HyperFrames.
