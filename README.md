# Giriş
Bu repository, Global AI Hub & Akbank Deep Learning Bootcamp'i için geliştirilmiş bir görüntü sınıflandırma projesidir. Projenin temel amacı, veri setinde bulunan hayvanları derin öğrenme tekniklerini kullanarak 10 farklı sınıfa ayırmaktır.

Proje kapsamında, Kaggle'daki [Animals-10 Veri Seti] seçilmiştir. Görüntü verileri TenserFlow kütüphanesi kullanılarak işlenip Data Augmentation adımıyla çoğaltılmıştır. TenserFlow ve Keras kütüphaneleri kullanılarak da Evrişimli Sinir Ağı (CNN) modeli tasarlanmış ve eğitilmiştir. Modelin performansındaki değişiklikleri gözlemlemek amacıyla "Learning Rate" ve "Batch Size" hiperparametreleri için optimizasyon çalışmaları yapılmıştır.

# Veri Seti
Projede, Kaggle üzerinde bulunan **[Animals-10]** veri seti kullanılmıştır. 
* **Sınıf Sayısı:** 10 ('cane', 'cavallo', 'elefante' vb.)
* **Toplam Görüntü:** ~26,000
* **Kullanılan Boyut:** Görüntüler modele verilmeden önce 120x120 piksele yeniden boyutlandırılmıştır.

## Kullanılan Teknolojiler ve Yöntemler
- **Kütüphaneler:** Python, TensorFlow, Keras, Scikit-learn, Pandas, Matplotlib, Seaborn
- **Model Mimarisi:** `SeparableConv2D` katmanları ile normalden düşük ama verinli parametre sayısı ile bir Evrişimli Sinir Ağı (CNN) kullanılmıştır. Overfitting'i engellemek için `BatchNormalization`, `Dropout` ve `L2 Regularization` teknikleri uygulanmıştır.

- **SeparableConv2D**
Proje geliştirilirken Conv2D filtrelerinin kullanılmasına karar verilmiş olup ilerleyen aşamalarda overfitting sorununu çözmek amacıyla SeperableConv2D katmanına geçilmiştir. Bunun başlıca sebebi olarak Conv2D'nin yapmış olduğu eylemi daha az parametre ile yaparak daha hafif bir model oluşturmayı hedefler.

- **BatchNormalization, Dropout ve L2 Regularization**
Proje geliştirilirken overfitting sorununu azaltmak amacıyla bu katmanların kullanılmasına karar verilmiştir. 
Dropout, aktif nöronların bazılarını kapatarak modelin öğrenme başarısını arttırmayı hedefler.
L2 Regularization, Aşırı öğrenmiş nöronlara ceza vererek onları 'weight' gibi parametrelerini azaltır.
BatchNormalization, bir katmandan çıkan ve bir sonraki katmana giren verileri (aktivasyonları) her bir veri yığını (mini-batch) için 'normalize eder'.

- **Veri Önişleme:** Modelin genelleme yeteneğini artırmak için yüksek değerlerde `RandomFlip`, `RandomRotation`, `RandomZoom` gibi veri artırma (Data Augmentation) teknikleri kullanılmıştır.
- **Optimizasyon:** En iyi `learning_rate` (öğrenme oranı) ve `batch_size` (yığın boyutu) değerlerini bulmak için bir hiperparametre arama döngüsü oluşturulmuştur.
- **Değerlendirme:** Modelin başarımı; Accuracy/Loss grafikleri, Karmaşıklık Matrisi (Confusion Matrix), Sınıflandırma Raporu (Classification Report) ve Grad-CAM ısı haritaları ile detaylı bir şekilde analiz edilmiştir.

## Elde Edilen Sonuçlar
Yapılan hiperparametre optimizasyonu sonucunda en iyi performansı veren `batch_size = 128`, `learning_rate = 0.01` parametrelerine ulaşılmıştır. 

## Kaggle Notebook Linki
Projenin tüm kod ve analizlerini içeren Kaggle Notebook'una aşağıdaki linkten ulaşabilirsiniz:
(https://www.kaggle.com/code/baranberkdincer/notebook423df0143b)
