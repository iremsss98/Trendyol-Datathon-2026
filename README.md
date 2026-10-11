# Trendyol E-Ticaret Datathon 2026: Arama–Ürün Alaka Sınıflandırması

Trendyol E-Ticaret Yarışması 2026 (Kaggle) için geliştirdiğim çözüm. Nihai Public Leaderboard skoru: **0.805 (macro-F1)**

## Problem

- **Görev:** Bir (arama terimi, ürün) çiftinin alakalı (1) mı alakasız (0) mı olduğunu tahmin etmek.
- **Metrik:** Macro-averaged F1
- **Zorluk:** Eğitim verisi yalnızca pozitif (alakalı) çiftler içeriyor; negatif örneklerin yarışmacı tarafından üretilmesi gerekiyor.

## Çözüm Süreci

| Aşama | Yaklaşım | Public LB (macro-F1) |
| --- | --- | --- |
| 1 | TF-IDF + elle oluşturulan özellikler + LightGBM | 0.704 → 0.743 |
| 2 | BGE cross-encoder reranker'a geçiş | 0.743 → 0.805 |

**Nihai çözüm:** `bge-reranker-v2-m3` modeli ile zero-shot (sıfır-atış) alaka skorlaması ve -1.5 karar eşiği. Model, göreve özel eğitim yapılmadan arama terimi ile ürün arasındaki alakayı doğrudan puanlıyor.

## Kullanılan Araçlar

Python, pandas, polars, NumPy, PyTorch, Hugging Face Transformers, LightGBM, scikit-learn (TF-IDF)

Notebook, Kaggle üzerinde 2× GPU T4 ile çalıştırılmıştır.

## Dosyalar

- `trendyol-e-ticaret-datathon-...ipynb`: Çözümün gelişim süreci ve nihai modeli içeren notebook

> Not: Yarışma verileri, yarışma kuralları gereği bu depoda paylaşılmamıştır.
