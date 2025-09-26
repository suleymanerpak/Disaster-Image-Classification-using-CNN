# Disaster Images Classification with CNN

Bu repo, Akbank Derin Öğrenmeye Giriş bootcampi için hazırlanmıştır. Bu proje kapsamında, doğal afet ve normal durumları ayırt etmek için bir **CNN (Convolutional Neural Network)** modeli geliştirilmiştir.

## Giriş
Projede kullanılan veri seti: Disaster Images Dataset (CNN Model)  
- Dataset, `train`, `validation`, `test` olmak üzere üç klasöre ayrılmıştır.  
- Her klasörde farklı sınıflardan görüntüler yer almaktadır (örn: doğal afet türleri ve normal durumlar).  

Model
Modelin yapısı ve parametreleri:

- Temel model: CNN (Convolutional Neural Network)  
- Katmanlar:  
  - Conv2D (32 filtre, 3x3 kernel, ReLU) + MaxPooling2D  
  - Conv2D (64 filtre, 3x3 kernel, ReLU) + MaxPooling2D  
  - Conv2D (128 filtre, 3x3 kernel, ReLU) + MaxPooling2D  
  - Flatten  
  - Dense (128, ReLU)  
  - Dropout (0.5)  
  - Dense (sınıf sayısı, softmax)  
- Optimizasyon: Adam (learning_rate=0.001)  
- Kayıp Fonksiyonu: Sparse Categorical Crossentropy  
- Epoch: 20  
- Callbacks: EarlyStopping (val_loss), ModelCheckpoint (best_model.h5)  

Veri artırma (data augmentation) uygulanmıştır:  
- Rescale (1./225), rotation, width/height shift, shear, zoom, horizontal flip  

Eğitim ve Değerlendirme
- Eğitim sırasında Loss ve Accuracy grafikleri oluşturulmuştur.  

Test Sonuçları
- Test Loss: 1.3917  
- Test Accuracy: 0.2500  

## Metrikler
Model, üç katmanlı CNN mimarisi ile oluşturulmuştur: Conv2D + MaxPooling2D + Flatten + Dense.  
Aktivasyon fonksiyonları olarak ReLU ve softmax kullanılmıştır.  
Optimizasyon için Adam, kayıp fonksiyonu olarak Sparse Categorical Crossentropy seçilmiştir.  
Model 20 epoch boyunca EarlyStopping ve ModelCheckpoint callbackleri ile eğitilmiştir.

## Ekler
- Notebook: `bootcamp-cnn.ipynb`  
- Dataset bağlantısı: `https://www.kaggle.com/datasets/mikolajbabula/disaster-images-dataset-cnn-model`  
- Çalışma GPU üzerinde yapılmıştır, böylece model eğitimi hızlandırılmıştır.  

## Sonuç ve Gelecek Çalışmalar
- Bu çalışma ile doğal afet görüntülerinin sınıflandırılması mümkün hale gelmiştir.  
- Gelecek geliştirmeler:  
  - Daha gelişmiş CNN mimarileri veya transfer learning (MobileNet, EfficientNet) kullanmak.  
  - Daha büyük veri setleri ile modelin doğruluk oranını artırmak.  
  - Modelin web veya mobil uygulama üzerinden gerçek zamanlı çalışmasını sağlamak.  

## Linkler
- [Kaggle Notebook – CNN ile Disaster Images Classification](https://www.kaggle.com/datasets/mikolajbabula/disaster-images-dataset-cnn-model) 
- [Kaggle GPU Çalışması](https://www.kaggle.com/code/suleymanerpak/bootcamp-cnn?scriptVersionId=264132866)
