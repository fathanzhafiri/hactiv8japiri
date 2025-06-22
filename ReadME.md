# Barak Militer untuk Siswa Bermasalah di Jawa Barat: Analisis Opini Publik di Twitter Menggunakan IBM Granite dan AI

## **📌 Project Overview**

Kebijakan kontroversial yang diusulkan oleh salah satu tokoh publik di Jawa Barat mengenai pengiriman siswa bermasalah ke barak militer telah memicu perdebatan luas di media sosial, khususnya Twitter. Proyek ini bertujuan untuk memahami persepsi dan opini publik terhadap kebijakan tersebut dengan menganalisis komentar masyarakat yang dipublikasikan secara daring.

Data dikumpulkan dari Twitter dengan menggunakan berbagai kata kunci relevan seperti “nakal barak”, “bermasalah barak”, “pelajar barak”, dan penyebutan langsung terhadap akun tokoh yang terlibat (@DediMulyadi71), dengan rentang waktu dari 27 April hingga 27 Mei 2025\. Seluruh tweet kemudian digabungkan dan dibersihkan dari duplikat untuk dianalisis lebih lanjut.

Melalui pendekatan analisis sentimen berbasis kecerdasan buatan (menggunakan LLM IBM Granite dan indoBERT model dari HuggingFace), proyek ini menggali insight mengenai sentimen masyarakat (positif, netral, negatif), serta subkategori opini yang muncul seperti persetujuan terhadap kebijakan, ujaran kebencian, dan harapan publik. Analisis ini ditujukan untuk membantu pengambilan keputusan berbasis data oleh pembuat kebijakan, akademisi, maupun masyarakat luas dalam memahami respons publik secara lebih objektif dan menyeluruh.

## **🔍 Analysis Process**

Proyek ini dilakukan melalui tahapan analisis data yang runtut dan berbasis metode yang tepat guna untuk mengungkap opini publik secara mendalam. Berikut tahapan lengkapnya:

---

### **1\. Data Collection (Crawling Twitter)**

Data diambil menggunakan *tweet-harvest*, dengan kata kunci relevan seperti `nakal barak`, `siswa barak`, `pelajar barak`, dan `@DediMulyadi71 barak`, dalam rentang 27 April – 27 Mei 2025\. Crawling dilakukan dalam Bahasa Indonesia dengan limit tweet yang disesuaikan untuk menjaga representativitas.

Hasil crawling Twitter/X sudah diupload pada gdrive berikut:
bit.ly/3G9A5nA

---

### **2\. Data Cleaning & Preprocessing**

Setelah data digabungkan, dilakukan pembersihan dan normalisasi, termasuk:

* Penghapusan duplikat dan noise (URL, emoji, karakter aneh)

* Lowercasing

* Normalisasi slang (menggunakan kamus bahasa gaul Indonesia)

* Stopword removal dan stemming dengan **Sastrawi**

Langkah ini memastikan data yang masuk ke model AI dalam kondisi lebih bersih dan terstruktur.

---

### **3\. Sentiment Classification (HuggingFace Model)**

Klasifikasi sentimen dilakukan menggunakan model dari HuggingFace: **`taufiqdp/indonesian-sentiment`**, bukan IBM Granite.  
 Model ini dipilih karena:

* Secara empiris lebih akurat dalam memahami konteks bahasa Indonesia

* Menghasilkan label yang stabil: **positif, netral, negatif**

---

### **4\. Exploratory Data Analysis (EDA)**

Sebelum masuk ke tahap kategorisasi dan AI reasoning, dilakukan eksplorasi terhadap distribusi sentimen:

* **Distribusi Sentimen** menunjukkan dominasi sentimen negatif (\~75%)

* **Wordcloud** per sentimen digunakan untuk mengidentifikasi kata-kata kunci dominan  
   → Misalnya, “anak”, “nakal”, “barak”, “masalah”, dan “kirim” mendominasi sentimen negatif dan positif.

EDA ini penting untuk menentukan arah kategorisasi dan menyusun subkategori opini yang merepresentasikan variasi isi komentar.

---

### **5\. Subkategori Opini & Prompt Classification (IBM Granite)**

Berdasarkan hasil EDA, dilakukan klasifikasi lebih lanjut terhadap komentar berdasarkan isi dan maksudnya menggunakan **IBM Granite LLM**. Prompt digunakan untuk mengelompokkan komentar ke dalam subkategori seperti:

* Positif: *Setuju dengan Kebijakan*, *Apresiasi terhadap Figur*, *Harapan*

* Negatif: *Tidak Setuju dengan Kebijakan*, *Ujaran Kebencian*, *Lainnya*

* Netral: *Pernyataan Fakta atau Informasi*, *Pertanyaan atau Diskusi*, *Lainnya*

Model Granite digunakan di tahap ini karena keunggulannya dalam pemahaman konteks dan reasoning berbasis prompt.

---

### **6\. Summarization (IBM Granite Output)**

Sebagai output akhir, dilakukan **abstractive summarization** terhadap komentar publik — khususnya untuk subkategori dengan komentar terbanyak. Ringkasan ini memberikan **gambaran naratif** atas opini yang berkembang, bukan hanya statistik atau kutipan mentah.

Hasil summarization menjadi bahan utama untuk **insight, temuan, dan rekomendasi**, karena mampu merangkum pandangan publik dalam bentuk paragraf yang utuh dan bermakna.

## **💡 Insight & Findings**

Analisis opini publik terhadap kebijakan Gubernur Jawa Barat dalam mengirim siswa bermasalah ke barak militer menghasilkan temuan yang beragam, dengan nuansa emosi dan perspektif yang kompleks dari masyarakat. Temuan ini didapatkan dari klasifikasi sentimen dan subkategori, serta dirangkum melalui proses summarization berbasis AI.

---

### **🔴 Sentimen Negatif (75.5%)**

Mayoritas komentar masyarakat menunjukkan **penolakan terhadap kebijakan** barak militer, terutama karena dinilai tidak menyelesaikan akar masalah siswa.

**Insight utama:**

* **Tidak setuju dengan kebijakan (51%)**: Masyarakat mengkritik kebijakan ini karena dianggap solusi instan yang mengabaikan masalah utama seperti kondisi keluarga dan sistem pendidikan.

* **Kritik hukum dan implikasi sosial**: Kebijakan dianggap melampaui kewenangan gubernur, serta berpotensi menimbulkan efek psikologis negatif.

* **Alih fokus dari pendidikan ke militerisasi**: Banyak komentar menyayangkan bahwa solusi yang dipilih bukanlah perbaikan sekolah atau kurikulum, melainkan tindakan koersif.

*“Disiplin bukan soal dimiliterisasi. Anak-anak ini butuh lingkungan sehat, bukan barak.”*

---

### **🟡 Sentimen Netral (16.3%)**

Komentar netral mayoritas berupa **deskripsi kebijakan** atau **permintaan klarifikasi/usulan alternatif**.

**Insight utama:**

* **Pernyataan Fakta**: Publik menyampaikan kronologi kebijakan, dana APBD yang digunakan, serta keterlibatan orang tua dalam proses persetujuan.

* **Permintaan atau Usulan**:

  * Usulan penggunaan alternatif lain seperti pesantren, gunung, RSJ, atau lembaga sipil.

  * Pertanyaan tentang prosedur masuk barak dan transparansi program.

  * Sindiran terhadap figur publik yang diminta ikut merasakan pengalaman barak.

*“Kalau anggota DPR juga masuk barak, mungkin mereka lebih paham gimana rasanya.”*

---

### **🟢 Sentimen Positif (8.2%)**

Meskipun proporsinya kecil, komentar positif menunjukkan **dukungan** dan **harapan** bahwa kebijakan ini dapat membawa dampak baik jika dijalankan secara benar.

**Insight utama:**

* **Setuju dengan kebijakan (28.9%)**:

  * Melihat barak sebagai tempat pembinaan karakter dan solusi untuk anak yang tidak cocok dengan pendekatan pendidikan formal.

  * Menilai pendekatan militer lebih tegas dan terstruktur dibanding metode pendidikan konvensional.

* **Harapan untuk diterapkan (30%)**:

  * Harapan agar program ini bisa membantu siswa miskin, membuka peluang karir, dan membentuk karakter positif.

  * Diharapkan menjadi tempat pembinaan sosial, teknis, dan budaya—bukan sekadar hukuman.

*“Barak bisa jadi tempat binaan anak-anak bandel, asal bukan dengan kekerasan.”*

---

### **🧠 Kesimpulan Tematik**

* **Opini masyarakat sangat polar**, tetapi didominasi oleh resistensi terhadap pendekatan koersif.

* **Narasi positif lebih banyak datang dari harapan akan pembinaan karakter dan masa depan siswa**, bukan semata karena dukungan terhadap kebijakan itu sendiri.

* **Komentar netral berperan penting dalam menyebarkan informasi dan menyuarakan alternatif**.

## **✅ Conclusion & Recommendation**

### **🔚 Conclusion**

Berdasarkan analisis opini publik terhadap kebijakan Gubernur Jawa Barat yang mengirim siswa bermasalah ke barak militer, mayoritas masyarakat menunjukkan **sentimen negatif** terhadap pendekatan tersebut. Meskipun ada sebagian dukungan, persepsi publik umumnya menyoroti potensi dampak buruk, pelanggaran prinsip pendidikan, dan kekhawatiran terhadap pendekatan koersif yang mengabaikan akar masalah sosial dan psikologis siswa.

Komentar positif dan netral lebih banyak mengandung **nuansa harapan dan informasi**, bukan pembenaran total terhadap kebijakan. Ini menandakan bahwa publik masih terbuka terhadap inovasi solusi, selama dilakukan secara partisipatif, legal, dan manusiawi.

---

### **📌 Recommendations**

1. **Kembangkan Model Pembinaan Kolaboratif (Militer \+ Pendidikan)**

   * Menggabungkan pendekatan disiplin dari militer dengan **pendampingan psikologis dan edukatif** dari Kementerian Pendidikan dan lembaga profesional.

   * Hindari menjadikan barak militer sebagai satu-satunya solusi tunggal.

2. **Lakukan Kajian Ulang Legalitas Kebijakan**

   * Libatkan Kementerian Pendidikan dan Kementerian Hukum & HAM untuk **memastikan bahwa program tidak melanggar hak-hak siswa**, baik secara hukum nasional maupun konvensi internasional.

   * Pastikan ada **aturan turunan, payung hukum, dan SOP yang transparan.**

3. **Libatkan Orang Tua dan Tenaga Ahli dalam Keputusan**

   * Setiap keputusan pengiriman siswa ke barak harus berdasarkan **persetujuan orang tua dan asesmen tenaga profesional** seperti guru BK, psikolog, atau pekerja sosial.

4. **Sediakan Alternatif Solusi Non-Militer**

   * Kembangkan opsi rehabilitasi berbasis komunitas seperti pesantren modern, pelatihan kewirausahaan, atau boarding school yang humanis dan mendidik.

   * Libatkan LSM, komunitas lokal, dan lembaga agama untuk mendukung keberlanjutan pembinaan.

5. **Evaluasi dan Publikasikan Dampak Kebijakan Secara Berkala**

   * Lakukan evaluasi program setiap 3 atau 6 bulan dan **publikasikan hasilnya ke publik** untuk membangun kepercayaan dan menghindari spekulasi negatif.

   * Gunakan insight ini sebagai alat ukur keberhasilan atau kegagalan untuk pengambilan keputusan kebijakan jangka panjang.

## **🔄 Recommendation for Future Development**

Sebagai lanjutan dari analisis ini, terdapat beberapa catatan penting untuk pengembangan proyek serupa di masa mendatang agar menghasilkan insight yang lebih tajam dan dapat diandalkan:

1. **Pemilihan Model Bahasa Indonesia yang Lebih Optimal**

   * Disarankan untuk menggunakan atau mengembangkan model yang telah dilatih khusus untuk Bahasa Indonesia, terutama dalam konteks sosial-politik. Selain model seperti `taufiqdp/indonesian-sentiment` atau LLM lokal yang telah di-fine-tune, penggunaan model AI yang lebih canggih seperti `ChatGPT` atau layanan dari `Azure AI` juga dapat dipertimbangkan untuk meningkatkan akurasi dan kedalaman pemahaman dalam analisis sentimen dan klasifikasi opini.

2. **Peningkatan Preprocessing dengan Resource Lokal**

   * Gunakan kamus slang yang lebih kaya, termasuk padanan bahasa daerah seperti **Sunda**.

   * Terapkan **deteksi komentar dari buzzer atau spam** agar sentimen yang tidak otentik dapat difilter.

   * Buat sistem untuk **menghapus komentar tidak bermakna** (e.g., satu kata, noise, interjeksi netral) agar hasil analisis lebih bersih.

3. **Evaluasi dan Fine-Tuning IBM Granite (Prompt-Based LLM)**

   * Untuk klasifikasi subkategori, akan lebih akurat jika model **fine-tuned** menggunakan dataset berlabel (annotated).

   * Evaluasi akurasi klasifikasi model LLM dapat dilakukan melalui perbandingan manual dengan data yang telah divalidasi.

   * Penting untuk memastikan **kebersihan data dan kejelasan label** sebelum proses fine-tuning dilakukan.

## **🤖 AI Support Explanation**

Dalam proyek ini, teknologi Artificial Intelligence (AI) berperan penting untuk menganalisis opini publik secara skalabel dan mendalam. AI digunakan pada dua tahap utama dengan fungsi dan model yang berbeda sesuai kebutuhan:

---

### **1\. Sentiment Classification – HuggingFace (`taufiqdp/indonesian-sentiment`)**

Pada tahap pertama, AI digunakan untuk melakukan **klasifikasi sentimen** terhadap komentar publik (positif, netral, negatif) secara otomatis.

* **Model**: `taufiqdp/indonesian-sentiment` dari HuggingFace

* **Alasan pemilihan**:

  * Sudah dilatih khusus untuk **teks berbahasa Indonesia**

  * Ringan dan efisien untuk dijalankan di Google Colab

  * Lebih akurat dibanding model dari IBM Granite untuk konteks Bahasa Indonesia

Model ini memproses seluruh teks komentar dan memberikan label polaritas awal, yang menjadi dasar untuk analisis lebih lanjut.

---

### **2\. Subcategory Classification & Summarization – IBM Granite LLM**

Setelah sentimen diklasifikasikan, komentar dianalisis lebih dalam menggunakan **Large Language Model (LLM) IBM Granite** untuk dua tugas:

#### **a. Subkategori Opini (Prompt-Based Classification)**

* **Fungsi**: Mengklasifikasikan opini masyarakat ke dalam subkategori seperti:

  * *Setuju dengan kebijakan*, *Ujaran kebencian*, *Harapan*, dsb.

* **Metode**: Menggunakan prompt kustom untuk setiap label sesuai karakteristik teks

* **Alasan penggunaan**:

  * IBM Granite unggul dalam memahami konteks semantik dan makna tersirat

  * Mampu mengenali niat dan nada komentar yang tidak eksplisit

#### **b. Summarization**

* **Fungsi**: Merangkum komentar-komentar publik menjadi **paragraf insight naratif**

* **Kegunaan**:

  * Memberikan pemahaman makro atas opini publik tanpa membaca ribuan komentar

  * Memudahkan penyusunan insight dan rekomendasi berbasis narasi

Model LLM IBM Granite digunakan melalui API Replicate dengan pengaturan prompt yang disesuaikan untuk Bahasa Indonesia.

---

### **🔍 Ringkasan Pemanfaatan AI**

| Tahap Analisis | Model AI | Fungsi |
| ----- | ----- | ----- |
| Sentiment Classification | HuggingFace `taufiqdp/indonesian-sentiment` | Klasifikasi polaritas (positif/negatif/netral) |
| Subkategori & Reasoning | IBM Granite LLM | Klasifikasi topik opini berdasarkan prompt |
| Data Summarization | IBM Granite LLM | Merangkum isi komentar ke dalam paragraf naratif |

