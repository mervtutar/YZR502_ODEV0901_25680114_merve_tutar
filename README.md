# YZR502 — Robotik Görüntü İşleme ve Nesne Tanıma için Parametre Analizi

**Ders:** YZR502 Robotik Sistemler ve Algoritmalar  
**Ödev:** ODEV0901  
**Öğrenci:** Merve Tutar  


---

## 📌 Proje Hakkında

Bu çalışmada, robotik görü sistemlerinde nesne tanıma performansını etkileyen görüntü işleme parametrelerinin sistematik analizi yapılmıştır. Google Colab üzerinde çalışan bir pipeline'da **Gauss σ**, **CLAHE kırpma limiti**, **Canny eşikleri** ve **ORB öznitelik sayısı** parametrelerinin algılama metriklerine etkisi 5 farklı deney konfigürasyonuyla incelenmiştir.

---

## 🔗 Bağlantılar

| | Link |
|---|---|
| 📄 Makale | Bu repodaki `YZR502_ODEV0901_Merve.docx` |
| 💻 Colab Notebook | `YZR502_ODEV0901.ipynb` |
| 🎥 YouTube Video |(https://youtu.be/WuLpcilKcq4) |

---


---

## ⚙️ Deney Konfigürasyonları

| Deney | Değiştirilen Parametre | σ | CLAHE clip | Canny Low | Canny High | ORB n |
|-------|------------------------|---|-----------|-----------|-----------|-------|
| D1 – Varsayılan | — | 1.5 | 2.0 | 50 | 150 | 500 |
| D2 – Agresif Kenar | canny_low, canny_high | 1.5 | 2.0 | 30 | 90 | 500 |
| D3 – Güçlü Yumuşatma | gaussian_sigma | 3.0 | 2.0 | 50 | 150 | 500 |
| D4 – Yüksek Kontrast | clahe_clip | 1.5 | 5.0 | 50 | 150 | 500 |
| D5 – Az ORB / Yüksek σ | σ, clip, grid, ORB | 2.5 | 3.0 | 40 | 120 | 300 |

---

## 📊 Sonuçlar Özeti

| Deney | T. Kontur | G. Kontur | ORB KN | Ort. Dairesellik | Ort. Alan (px²) |
|-------|-----------|-----------|--------|-----------------|-----------------|
| D1 – Varsayılan | 334 | 2 | 500 | 0.010 | 839.8 |
| D2 – Agresif Kenar | 612 | 2 | 500 | 0.010 | 839.8 |
| D3 – Güçlü Yumuşatma | 316 | 0 | 500 | 0.000 | 0.0 |
| D4 – Yüksek Kontrast | 574 | 4 | 500 | 0.132 | 638.4 |
| D5 – Az ORB / Yüksek σ | 651 | 2 | 300 | 0.800 | 422.2 |

**Öne çıkan bulgular:**
- D2: Düşük Canny eşikleri toplam kontur sayısını **%83 artırdı** ama geçerli kontur değişmedi → saf gürültü artışı
- D3: σ=3.0 geçerli kontur sayısını **sıfıra indirdi** → aşırı yumuşatma nesne tespitini tamamen engeller
- D5: En yüksek dairesellik **(0.800)** → doğru parametre kombinasyonu şekil kalitesini optimize eder

---

## 🚀 Çalıştırma

1. [Google Colab](https://colab.research.google.com)'a gidin
2. `YZR502_ODEV0901.ipynb` dosyasını yükleyin
3. Hücreleri sırayla çalıştırın — tüm bağımlılıklar ilk hücrede kurulur
4. Çıktı görselleri otomatik olarak kaydedilir

```python
# Gerekli kütüphaneler
!pip install opencv-python opencv-contrib-python matplotlib numpy
```

---

## 🛠️ Kullanılan Teknolojiler

- Python 3.10
- OpenCV 4.x (`opencv-contrib-python`)
- NumPy
- Matplotlib
- Google Colab

---

## 📝 Lisans

Bu proje YZR502 dersi akademik ödev kapsamında hazırlanmıştır.

#YZR502 #ComputerVision #Robotics #OpenCV #ImageProcessing
