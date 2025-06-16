
# 🛍️ Sentiment Analysis Shopee App - Google Play Review

Proyek ini bertujuan untuk melakukan scraping, preprocessing, dan analisis sentimen terhadap ulasan pengguna aplikasi Shopee di Google Play Store. Model yang digunakan adalah Naive Bayes dengan pendekatan TF-IDF dan evaluasi menggunakan metrik akurasi, presisi, recall, dan F1-score.

---

## 📦 Struktur Proyek

| File                          | Deskripsi |
|-------------------------------|----------|
| `Hasil scrape data.csv`          | Hasil scraping dari Google Play Store |
| `Hasil Preprocess.csv`     | Data bersih untuk analisis sentimen |
| `hasil_TextPreProcessing_shopee.csv` | Data bersih untuk analisis sentimen |
| `Scraping_dan_Preprocessing.ipynb` | Notebook untuk memperoleh dataset kemudian dibersihkan |
| `Implementasi_Model.ipynb` | Notebook yang menjalankan seluruh pipeline |

---

## 📥 Scraping Data

### Tools
- `google-play-scraper`
- `pandas`, `numpy`

### Deskripsi
Mengambil 1000 ulasan aplikasi Shopee Indonesia (`com.shopee.id`) dari Google Play Store dengan filter bahasa Indonesia dan urutan relevansi tertinggi.

```python
from google_play_scraper import reviews, Sort
result, continuation_token = reviews(
    'com.shopee.id',
    lang='id',
    country='id',
    sort=Sort.MOST_RELEVANT,
    count=1000,
    filter_score_with=None
)
```

---

## 🧼 Preprocessing

### Tahapan
- Menghapus data null
- Case folding dan cleaning teks
- Stopword removal (menggunakan `nltk`)
- Tokenisasi
- Stemming Bahasa Indonesia (`Sastrawi`)

Output disimpan dalam `hasil_TextPreProcessing_shopee.csv`

---

## 📊 Analisis Sentimen

### Model
- **TF-IDF Vectorizer**
- **Multinomial Naive Bayes** (dengan `GridSearchCV` untuk tuning `alpha`)

### Evaluasi
- Confusion Matrix
- Accuracy, Precision, Recall, F1-score
- Classification Report

### Visualisasi
- Bar chart jumlah label (Positif/Negatif)
- Heatmap confusion matrix

---

## 📈 Contoh Output Evaluasi

```text
Accuracy: 0.83
Precision: 0.84
Recall: 0.81
F1_score: 0.82
```

---
