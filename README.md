# Emotion Detection with CNN

Bu proje, insan yüz ifadelerini kullanarak çeşitli duyguları sınıflandırmayı amaçlayan bir derin öğrenme çalışmasıdır. Kullanılan veri seti, 48x48 boyutundaki gri tonlamalı görüntülerden oluşmakta ve her bir görüntü farklı bir duyguyu temsil etmektedir.

## Proje Özeti
Bu çalışmada, yüz ifadelerinden şu yedi farklı duygunun sınıflandırılması hedeflenmiştir:
- **Öfke (Angry)**
- **Tiksinti (Disgust)**
- **Korku (Fear)**
- **Mutluluk (Happy)**
- **Üzgünlük (Sad)**
- **Nötr (Neutral)**
- **Şaşkınlık (Surprise)**

Veri seti, her bir duyguyu temsil eden 48x48 boyutundaki gri tonlamalı yüz görüntülerinden oluşmaktadır. Görüntüler, tek bir dizi olarak verildiği için veri ön işleme aşamasında bu diziler yeniden şekillendirilerek orijinal görüntü boyutuna dönüştürülmüştür.

## Veri Ön İşleme
- **Kolon İsimlerinin Temizlenmesi:** Veride yer alan bazı kolon isimlerinde gereksiz boşluk karakterleri mevcuttu ve bunlar temizlenmiştir.
- **Train-Test Ayrımı:** Verinin eğitim ve test kümelerine manuel olarak ayrımı yapılmıştır.
- **Görüntü Dönüşümü:** Verisetindeki piksel verileri, 48x48 matrislere dönüştürülmüştür.
- **Etiketleme:** Duyguların her biri için etiketler oluşturularak kategorik hale getirilmiştir.

## Model Mimarisi
Duyguları sınıflandırmak için basit bir **Convolutional Neural Network (CNN)** modeli oluşturulmuştur:
- **3 Konvolüsyon Katmanı** ve her biri sonrası **MaxPooling** katmanı kullanılmıştır.
- **Fully Connected** (Tam Bağlantılı) katmanlardan oluşan bir yapı ile çıktı katmanında **Softmax** aktivasyon fonksiyonu kullanılarak duygular sınıflandırılmıştır.
- Model, **Adam** optimizasyon algoritması ve **categorical cross-entropy** kayıp fonksiyonu ile derlenmiştir.

## Model Eğitimi
- Model, 20 epoch boyunca, 128 batch boyutunda eğitim verisi ile eğitilmiştir.
- Eğitim süreci sırasında doğrulama (validation) verisi kullanılarak modelin başarımı izlenmiştir.

## Performans Değerlendirmesi
Model, her bir duygu için farklı başarımlar sergilemiştir:
- **Mutlu (Happy)** ve **Şaşkınlık (Surprise)** sınıflarında yüksek precision ve recall değerleri elde edilmiştir.
- **Tiksinti (Disgust)** ve **Korku (Fear)** sınıflarında performans düşük olup, özellikle bu sınıflar arasında ayrım yapmakta modelin zorlandığı gözlenmiştir.

### Genel Değerlendirme
- **Accuracy (Doğruluk):** %55 civarındadır.
- **F1-Skorları:** Sınıflar arasında ciddi farklar göstermektedir. En iyi performans "Mutlu" sınıfında gözlenmiştir.

Bu çalışmanın sonuçları, sınıf dengesizliğinin ve modelin bu dengesizlikle başa çıkma yeteneğinin geliştirilmesi gerektiğini göstermektedir. Özellikle düşük sayıda örneğe sahip sınıflar için veri artırımı ve model iyileştirmeleri gelecekte yapılacak çalışmalarda dikkate alınmalıdır.

