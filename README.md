# machine-learning-project
# Giriş
# İtalyan Deprem Veri Seti Analizi ve Büyüklük Sınıflandırması


Bu projede, İtalyan deprem kataloğundaki (1985-2020) veriler analiz edilerek deprem büyüklüklerini sınıflandırmak amacıyla bir makine öğrenmesi modeli geliştirilmiştir. Veri seti, sismik örüntüleri anlamak ve deprem özelliklerini tahmin etmek için çeşitli öznitelikler içermektedir.

Proje kapsamında aşağıdaki adımlar takip edilmiştir:
* Veri Ön İşleme ve Keşifsel Veri Analizi (EDA)
* Hedef Değişkenin (`MagnitudeClass`) Tanımlanması ve Oluşturulması (Veri sızıntısı tepsiti nedeniyle Magnitude olan hedef değişken çıkartıldı ve yeni hedef değişken oluşturuldu)
* Sınıfların Dengesizliğinin İncelenmesi ve Giderilmesi
* Korelasyon Matrisi ile Özellikler Arası İlişkilerin İncelenmesi
* Özellik Seçimi
* Karar Ağaçları (Decision Trees) Algoritması ile Model Geliştirme
* Model Performansının Kesinlik (Precision), Duyarlılık (Recall) ve F1 Skoru metrikleri ile Değerlendirilmesi

Notebook içerisinde (`Supervised.ipynb`) veri ön işleme adımları, hedef değişken oluşturma, sınıf dengesizliği problemi ve çözümü, korelasyon analizi ve özellik seçimi detaylı bir şekilde markdown hücrelerinde açıklanmıştır.

# Metrikler

Geliştirilen Karar Ağacı sınıflandırma modelinin performansı çeşitli metriklerle değerlendirilmiştir. Veri sızıntısı tespiti ve düzeltmesi yapıldıktan sonra elde edilen sonuçlar aşağıdaki gibidir:

**K-Katlamalı Çapraz Doğrulama (StratifiedKFold, k=5) Sonuçları:**
* Katlama 1 Doğruluk (Accuracy): 0.7600
* Katlama 2 Doğruluk (Accuracy): 0.7579
* Katlama 3 Doğruluk (Accuracy): 0.7600
* Katlama 4 Doğruluk (Accuracy): 0.7617
* Katlama 5 Doğruluk (Accuracy): 0.7598
* **Ortalama Doğruluk (Accuracy): 0.7599**
* Standart Sapma (Accuracy): 0.0012

**Tek Eğitim-Test Bölümü ile Sınıflandırma Raporu:**
* **Low Sınıfı (Düşük Şiddetli Depremler):**
    * Precision: 0.76
    * Recall: 0.77
    * F1-Score: 0.76
* **Medium Sınıfı (Orta Şiddetli Depremler):**
    * Precision: 0.75
    * Recall: 0.74
    * F1-Score: 0.74
* **Genel Doğruluk (Overall Accuracy): 0.76**

Karışıklık matrisi (Confusion Matrix) incelendiğinde, modelin düşük şiddetli depremleri (Low sınıfı) %77 oranında doğru bir şekilde hatırladığı (recall) görülmüştür (17544 düşük şiddetli depremden 13579 tanesini doğru tahmin etmiştir). Bu sonuçlar, modelin deprem büyüklüklerini belirli bir doğrulukla sınıflandırabildiğini göstermektedir. Kodun anlaşılması ve yorumlanması, sadece kod yazmaktan daha önemli olduğu için bu metriklerin analizi notebook içerisinde detaylandırılmıştır.

# Ekler

Proje kapsamında `Supervised.ipynb` notebook'unda veri sızıntısı tespiti yapılmış ve bu durumun önüne geçmek için `Magnitude` özelliği model eğitilirken çıkarılmıştır. Başlangıçta bu özellik kullanıldığında model %100 gibi mükemmel sonuçlar vermiş, bu da veri sızıntısının bir göstergesi olmuştur.

Karar ağacının ilk 3 seviyesinin görselleştirilmesi de notebook içerisinde bulunmaktadır.

*Not: Bu repo şablonunda UI klasörü altında Streamlit ile deployment için bir örnek script bulunmaktadır. Bu projede henüz bir deployment yapılmamıştır ancak gelecekte `Supervised.ipynb` notebook'undaki modelin deploy edilmesi planlanabilir.*

# Sonuç ve Gelecek Çalışmalar

Bu çalışmada, İtalyan deprem verileri kullanılarak deprem büyüklüklerini "Düşük" ve "Orta" olarak sınıflandıran bir Karar Ağacı modeli başarıyla geliştirilmiş ve yaklaşık %76 doğruluk oranı elde edilmiştir. Sınıf dengesizliği ve veri sızıntısı gibi potansiyel sorunlar ele alınmıştır.

Gelecek çalışmalar için düşünülebilecek bazı iyileştirmeler ve eklemeler şunlardır:
* Farklı sınıflandırma algoritmaları (Random Forest, Gradient Boosting, SVM vb.) denenerek model performansının karşılaştırılması.
* Hiperparametre optimizasyonu ile mevcut modelin daha da iyileştirilmesi.
* Özellik mühendisliği ile yeni ve daha anlamlı özellikler türetilmesi.
* Veri toplama aşamasının dinamik ve gerçek zamanlı verilerle güncellenmesi üzerine çalışılması.
* Modelin Streamlit veya Flask gibi araçlarla interaktif bir web arayüzü üzerinden deploy edilmesi.
* "High" sınıfını da dahil ederek üç sınıflı bir modelleme yapılması ve bu durumda sınıf dengesizliği için daha gelişmiş tekniklerin (SMOTE, ADASYN vb.) kullanılması.

Bu proje, bootcamp sonrası da geliştirilmeye açık bir çalışma olup, öğrenilecek yeni teknolojiler ve kariyer hedefleri doğrultusunda zenginleştirilebilir.

# Linkler

* **Kullanılan Veri Seti:** [Italian Earthquake Catalogue 1985-2020](https://www.kaggle.com/datasets/die9origephit/italian-earthquake-catalogue-1985-2020)
* **Proje Notebook'u:** `Supervised.ipynb` (Bu repoda bulunmaktadır)
