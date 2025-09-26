# 🧠 Beyin Tümörü Tespiti - Derin Öğrenme Projesi 

## Giriş

- Bu proje, beyin MR görüntülerinden tümör varlığını tespit edip sınıflandırmayı amaçlayan bir derin öğrenme uygulamasıdır. Amaç, beyin MR görüntülerinden tümör varlığını tespit edip sınıflandırmaktır.
  
Projede yaklaşık 7023 MR görüntüsünden oluşan dört sınıflı bir veri seti  kullanılmıştır: meningioma, glioma, pituitary ve notumor. Eğitim ve doğrulama için veri artırma (data augmentation) teknikleri uygulanmıştır.

Model olarak kendi geliştirdiğim CNN mimarisi kullanılmıştır. Eğitim süreci SGD optimizasyonu ve MSE kaybı ile gerçekleştirilmiş, EarlyStopping veya checkpoint yöntemleri ile eğitim takip edilmiştir.

Modelin performansı doğruluk ve sınıflandırma raporlarıyla değerlendirilmiştir.

## Farklı Model Yapılandırmaları ve Optimizasyon Denemeleri

| Deneme No | Model Yapılandırması | Optimizasyon Algoritması | Epoch | Learning Rate | Kayıp Fonksiyonu |
|-----------|--------------------|------------------------|-------|---------------|----------------|
| 1         | Sequential CNN      | Adamax                 | 25    | 0.001         | MSE            |
| 2         | Sequential CNN      | Adamax                 | 50    | 0.001         | MSE            |
| 3         | Sequential CNN      | SGD                    | 25    | 0.01          | MSE            |
| 4         | Sequential CNN      | Adam                   | 25    | 0.01          | MSE            |
| 5         | Sequential CNN      | SGD                    | 25    | 0.001         | MSE            |


# Grafikler 

- 1.Deneme için 
<img width="945" height="428" alt="image" src="https://github.com/user-attachments/assets/a5f0dee7-8895-4d0c-9470-e24a4f6536ea" />

- 3.Deneme için 
<img width="915" height="455" alt="image" src="https://github.com/user-attachments/assets/b20cd10f-7a0b-49f5-a428-96067211ac65" />

- En son aldığım grafik :
<img width="1007" height="506" alt="image" src="https://github.com/user-attachments/assets/e9981454-640a-4cd0-a245-4bebfa8fb1ad" />

## METRİKLER

Beyin tümörü sınıflandırma modelinin performansı aşağıdaki metrikler ile değerlendirilmiştir:

1. **Sınıf Bazlı Doğruluk**
   - Model her tümör tipi için ayrı ayrı doğruluk değerleri sunar: meningioma, glioma, pituitary, notumor.
   - Böylece modelin hangi tümör türlerinde daha başarılı olduğu ve hangi türlerde iyileştirme gerektiği görülür.

2. **Kayıp Değeri (Loss)**
   - Eğitim ve doğrulama sırasında MSE kaybı grafiklerle takip edilmiştir.
   - Kayıp değerleri stabil ve dengeli olduğundan overfitting gözlenmemiştir.

3. **Confusion Matrix (Hata Matrisi)**
   - Test setindeki tahminler üzerinden hata matrisi hazırlanmıştır.
   - Her sınıfın doğru ve yanlış sınıflandırma sayıları görselleştirilmiştir.

4. **Precision ve Recall Analizi**
   - Özellikle klinik önemi olan tümör sınıflarında precision ve recall değerleri incelenmiştir.
   - Yanlış pozitif ve yanlış negatif tahminlerin analizi ile modelin güvenilirliği değerlendirilmiştir.

5. **Görsel İnceleme**
   - Test setinden rastgele seçilen MR görüntüleri ile gerçek ve tahmin edilen sınıflar görselleştirilmiştir.
   - Görsel karşılaştırma, modelin hatalarını hızlıca tespit etmeye ve yorumlamaya yardımcı olur.

## EKLER

- Model, GPU destekli bir ortamda (Kaggle) eğitilmiş ve test edilmiştir, böylece eğitim süresi önemli ölçüde kısaltılmıştır.  
- Projede model doğrudan notebook üzerinden çalıştırılarak MR görüntüleri üzerinde test edilebilir.  
- Eğitim ve test verileri organize edilmiş klasörler hâlinde tutulmuştur (meningioma, glioma, pituitary, notumor).  
- Veri artırma (augmentation) teknikleri uygulanarak modelin genelleme yeteneği geliştirilmiştir.  
- Notebook içerisinde test görüntüleri için tahmin ve görselleştirme hücreleri eklenmiştir; yanlış ve doğru tahminler hızlıca incelenebilir.

  ## SONUÇ VE GELECEK ÇALIŞMALAR

Bu proje, beyin MR görüntülerinden tümör varlığını tespit eden ve sınıflandıran bir derin öğrenme modeli sunmaktadır. Model, test verisi üzerinde sınıf bazlı yüksek doğruluk sağlamış ve overfitting olmadan genel bir performans göstermiştir.

**Gelecek Çalışmalar:**

- **MR Görüntüleri için Otomatik Ön İşleme:** Gürültü giderme, normalize etme ve segmentasyon gibi işlemler otomatik hâle getirilebilir.  
- **Çoklu Görüntü Analizi:** Tek bir hasta için farklı açılardan alınmış MR görüntülerinin birlikte değerlendirilmesi sağlanabilir.    
- **Tümör Büyüme Tahmini:** Gelecek çalışmalar, aynı hastanın farklı zamanlardaki MR görüntülerini kullanarak tümör büyümesini tahmin etmeyi hedefleyebilir.  
- **Klinik Önceliklendirme:** Model, kritik veya acil tümör türlerini tespit ederek klinik karar destek sistemlerine entegre edilebilir.  


## Link 
https://www.kaggle.com/code/yamurnder/brain-tumor-detection-son1 

