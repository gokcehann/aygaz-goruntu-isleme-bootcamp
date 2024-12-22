# aygaz-goruntu-isleme-bootcamp
## Proje Açıklaması
Bu proje ile belirli hayvan türlerini tanımak için derin öğrenme ve görüntü işleme yöntemlerini kullanarak bir model geliştirmeyi amaçlamaktadır. Belirli hayvan sınıflarını tanıyabilen bir model oluşturur ve ardından bu modelin doğruluğunu değerlendirir. Ayrıca, veriyi manipüle ederek modelin dayanıklılığını test eder.

## Kullanılan Veri Seti
Proje, Kaggle'dan alınan **Animals with Attributes 2** veri setini kullanmaktadır. Veri seti, çeşitli hayvan türlerine ait resimler içerir. Bu projede yalnızca 10 farklı sınıf seçilmiştir:
- Collie, Dolphin, Elephant, Fox, Moose, Rabbit, Sheep, Squirrel, Giant Panda, Polar Bear

Her bir sınıftan 650 adet resim seçilmiş ve veri kümesi dengeye getirilmiştir.

## Kullanılan Kütüphaneler
- **NumPy**: Sayısal hesaplamalar için.
- **OpenCV**: Görüntü işleme için.
- **scikit-learn**: Veriyi eğitim ve test setlerine ayırmak için ve etiketleri sayısal formata dönüştürmek için.
- **TensorFlow / Keras**: Derin öğrenme modelini oluşturmak ve eğitmek için.
- **Matplotlib**: Eğitim süreci ve sonuçların görselleştirilmesi için.

## Proje Adımları
1. **Veri Kümesi Hazırlığı**: 
   - Seçilen sınıfların her birinden 650 adet görüntü alınıp hedef klasöre kopyalanmıştır.
   - Veriler, model için uygun hale getirilmek üzere yeniden boyutlandırılıp (128,128) normalleştirilmiştir.

2. **Veri İşleme**: 
   - Görseller yeniden boyutlandırılmış ve 255'e bölünerek normalleştirilmiştir.
   - Etiketler sayısal formata dönüştürülüp kategorik hale getirilmiştir.

3. **Model Oluşturulması**:
   - Basit bir Convolutional Neural Network (CNN) modeli oluşturulmuştur.
   - Modelde Conv2D, MaxPooling2D ve Dense katmanları kullanılmıştır.

4. **Veri Artırma**:
   - Eğitim verisi, rotasyon, genişlik ve yükseklik kaydırma, parlaklık değişimi, yatay flip gibi veri artırma yöntemleri ile zenginleştirilmiştir.

5. **Eğitim**:
   - Model, 45 epoch boyunca eğitim verilmiştir. Eğitim sürecinde doğruluk ve kayıp değerleri izlenmiştir.

6. **Manipülasyon ve Renk Sabitliği**:
   - Test verisi üzerinde manipülasyon (görüntü parlaklık ayarı, döndürme) ve renk sabitliği uygulamaları yapılmıştır. Manipüle edilmiş verilerle modelin doğruluğu karşılaştırılmıştır.

## Sonuçlar
Proje sonunda elde edilen doğruluk oranları aşağıdaki gibidir:
- **Orijinal Test Seti Doğruluğu**: `%65-%71`
- **Manipüle Edilmiş Test Seti Doğruluğu**: `%20-%30`
- **Renk Sabitliği Uygulanmış Test Seti Doğruluğu**: `%45-%55`

Sonuçlar, manipülasyon ve renk sabitliği uygulamalarının modelin doğruluğu üzerinde nasıl bir etki yarattığını göstermektedir.

## Model Mimarisi
Model, aşağıdaki katmanları içerir:
- **Conv2D (32, 3x3)**: Görüntüdeki temel özellikleri öğrenmek için.
- **MaxPooling2D (3x3)**: Görüntüdeki en belirgin özellikleri çıkararak boyutları küçültmek için.
- **Flatten**: Katmanlar arasında veri formatını düzleştirmek için.
- **Dense (128)**: Orta seviyeli öğrenme için.
- **Dense (10)**: Sonuçları 10 sınıfa dönüştürmek için, softmax aktivasyonu ile.

## Eğitim Parametreleri
- **Optimizasyon Yöntemi**: Adam
- **Kayıp Fonksiyonu**: Categorical Crossentropy
- **Metrik**: Accuracy
- **Epoch Sayısı**: 45

## Görselleştirmeler
Eğitim ve doğrulama doğruluğu ve kaybı süreç boyunca izlenmiş ve görselleştirilmiştir. Ayrıca, orijinal ve manipüle edilmiş test verileri ile karşılaştırmalar yapılmıştır.
