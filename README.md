# 🔍 Wood Surface Anomaly Detection with Unsupervised Models

Bu proje, **ahşap yüzeylerdeki kusurları tespit etmek ve segmentasyon maskeleri üretmek** amacıyla, denetimsiz öğrenme (unsupervised learning) temelli modeller kullanılarak geliştirilmiştir. Kullanılan veri seti, **MVTec AD** veri setinin yalnızca **wood** alt kümesini içermektedir.

## 🧠 Kullanılan Modeller

- **Autoencoder**
- **LCAE (Latent-space Constrained Autoencoder)**
- **MemoryBank Model (FastFlow benzeri)**

Modeller yalnızca "good" (kusursuz) görüntülerle eğitilmiş ve test aşamasında kusur tespiti gerçekleştirilmiştir.

## 📁 Veri Seti Yapısı

```
wood/
├── train/
│   └── good/
├── test/
│   ├── good/
│   └── defect/
└── ground_truth/
    └── defect/
```

## ⚙️ Kurulum

```bash
# (Opsiyonel) Sanal ortam oluşturun
python -m venv venv
source venv/bin/activate  # Windows için: venv\Scripts\activate

# Gerekli paketleri yükleyin
pip install -r requirements.txt
```

## 🚀 Kullanım

```bash
# Eğitim ve test işlemleri için:
python main.py
```

> Veri yollarını kod içinden doğru şekilde ayarlamayı unutmayın (`config.py` veya ilgili script içinde).

## 📊 Performans Sonuçları

| Model            | F1 Score | ROC AUC | Avg IoU | Best Threshold |
|------------------|----------|---------|---------|----------------|
| Autoencoder      | 0.758    | 0.785   | 0.045   | 0.0017         |
| LCAE             | 0.731    | 0.739   | 0.056   | 0.0029         |
| MemoryBankModel  | 0.732    | 0.705   | 0.041   | 0.0100         |

Performans, hem segmentasyon maskesi kalitesi (IoU), hem de anomali skorlarına dayalı sınıflandırma (F1, ROC AUC) ile ölçülmüştür.

## 📌 Özellikler

- Sadece "good" görüntülerle denetimsiz eğitim
- Anomali skoru üretimi ve eşik değeri ile sınıflandırma
- Gerçek maskelerle karşılaştırmalı segmentasyon değerlendirmesi
- Her model için ayrı sonuç görselleştirme ve skor analizi

## 📚 Kaynakça

- Bergmann et al., *MVTec AD: A Real-World Dataset for Unsupervised Anomaly Detection*, CVPR 2019.
- Batzner et al., *EfficientAD*, arXiv 2022.
- Ruff et al., *Deep One-Class Classification*, ICML 2018.
- Papers with Code, *Anomaly Detection on MVTec AD*
