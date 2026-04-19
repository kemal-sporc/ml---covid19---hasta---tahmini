# Makine Öğrenmesi Dersi - Covid-19 Tahmin Projesi

Selamlar, bu proje makine öğrenmesi dersi ödevi için hazırlanmıştır. Temel amacım, hastaların gösterdiği semptomlara ve genel sağlık durumlarına bakarak Covid-19 testinin pozitif mi yoksa negatif mi çıkacağını tahmin eden bir yapı kurmaktı.

## Veri Seti
Projede Kaggle'da bulunan ve Meksika Hükümeti tarafından paylaşılan geniş bir Covid-19 veri setini kullandım. 
* Veri Seti Linki: [COVID-19 Dataset by Meir Nizri](https://www.kaggle.com/datasets/meirnizri/covid19-dataset)

## Veri Ön İşleme
Algoritmaları eğitmeden önce veriyi biraz toparlamam gerekti:
1. İlk olarak eksik (null) veri içeren satırları tablodan sildim.
2. Hastalığın sonucunu belirten 'CLASIFFICATION_FINAL' sütununda 1, 2 ve 3 yazanları Pozitif (1), geri kalanları Negatif (0) olarak güncelleyerek ikili (binary) bir sisteme geçtim.
3. Tablo çok büyüktü ve sistemi donduruyordu. Bu yüzden içinden rastgele bir örneklem çekerek veriyi küçülttüm (yaklaşık 38 bin kayıt ile çalıştım).
4. Ayırdığım bu verinin %75'ini modelleri eğitmek için, kalan %25'ini ise test etmek için kullandım.

## Kullanılan Modeller ve Sonuçlar
Ödevde bizden istenen 4 farklı sınıflandırma algoritmasını (Lojistik Regresyon, Karar Ağacı, Rastgele Orman ve KNN) çalıştırdım. Test verisi üzerinden aldığım başarı oranları şu şekilde:

| Model | Doğruluk (Accuracy) | Kesinlik (Precision) | Duyarlılık (Recall) |
| :--- | :--- | :--- | :--- |
| Lojistik Regresyon | % 62.57 | % 64.43 | % 63.82 |
| Rastgele Orman | % 59.63 | % 62.06 | % 59.12 |
| Karar Ağacı | % 57.78 | % 61.61 | % 51.59 |
| KNN | % 59.84 | % 61.09 | % 64.39 |

## Kısa Değerlendirme
Doğruluk oranları genel olarak normal seviyelerde çıktı çünkü gerçek sağlık verilerinde ateş, öksürük gibi belirtiler sadece Covid'e değil, gribe veya başka hastalıklara da ait olabiliyor. Bu yüzden modellerin kafasının biraz karışması normal. Duyarlılık oranlarının düşük çıkmasının ana sebebi ise veri setinin çok dengeli olmaması (pozitif ve negatif vaka sayılarının eşit olmaması). 

## Kodları Çalıştırma
Projeyi denemek isterseniz bu repodaki .ipynb dosyasını indirin. Kaggle linkindeki veri setini de indirip aynı klasöre koyarsanız kodları baştan sona hatasız çalıştırabilirsiniz.
