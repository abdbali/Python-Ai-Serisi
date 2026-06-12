# Google Colab ile Adım Adım Python ve Yapay Zekaya Giriş

Ortaokul ve lise seviyesindeki öğrenciler için hazırlanmış Python programlama ve temel yapay zeka uygulamaları başlangıç rehberidir. Bu depo, sıfırdan başlayarak veri işlemeyi, grafik çizmeyi, sohbet botu geliştirmeyi ve görsel işlemeyi adım adım öğreten 6 derslik bir müfredat içermektedir.

Her ders yapı iskelesi (scaffolding) yöntemiyle kurgulanmıştır. Kodlar tek bir parça halinde verilmek yerine, her adımda üzerine yeni bir işlev eklenerek tam 5 farklı aşamada geliştirilir.

---

## Müfredat ve Ders İçerikleri

| Ders No | Ders Adı | Öğrenilecek Kavramlar | Elde Edilecek Çıktı / Ürün |
| :--- | :--- | :--- | :--- |
| **Ders 1** | Python'a Giriş ve Değişkenler | print(), input(), Değişkenler, Veri Tipleri | Dinamik Tanışma Programı |
| **Ders 2** | Pandas ile Veri Seti İşleme | import pandas, Sözlükler, DataFrame, Filtreleme | Film ve Not Tablosu Analizi |
| **Ders 3** | Matplotlib ile Veri Görselleştirme | plt.bar(), plt.show(), Grafik Özelleştirme | Oyun Popülerliği Sütun Grafiği |
| **Ders 4** | Hafızalı Sohbet Botu Yapımı | while True, if-elif-else, random.choice | İsim Hatırlayan Chatbot Uygulaması |
| **Ders 5** | Görsel Üretimi: Karekod | qrcode, save(), Kütüphane Kurulumu (!pip) | Özelleştirilmiş Renkli QR Kod |
| **Ders 6** | Görsel Karıştırma ve Kolaj | PIL (Pillow), resize(), paste(), Döngüler | 10 Resimden Oluşan 2x5 Mozaik |

---

## Çalıştırma Talimatları (Google Colab Rehberi)

Bu projedeki kodları bilgisayarınıza herhangi bir program indirmeden, tarayıcınız üzerinden ücretsiz olarak çalıştırabilirsiniz:

1. Google Colab (colab.research.google.com) adresine gidin ve Google hesabınızla giriş yapın.
2. Üst menüde yer alan "Yeni Not Defteri" (New Notebook) seçeneğine tıklayın.
3. Ders içeriklerinde paylaşılan kod bloklarını sırayla kopyalayın.
4. Colab üzerindeki kod hücrelerine yapıştırın ve hücrenin sol tarafında bulunan "Çalıştır" (Play) butonuna basın.

---

## Derslerin Özet Kod Yapıları

### Ders 4: Akıllı Chatbot Mantığı
Botun her seferinde farklı cevaplar vermesini sağlayan ve kullanıcının adını hafızasında tutan sistemin temel yapısı:

```python
import random

kullanici_adi = input("Bot: Adın nedir? \nSen: ")
hava_durumu_havuzu = [
    "Bugün bolca Python kodu yağışı bekleniyor.",
    "İnternet dünyasında hava güneşli ve bol pikselli."
]

while True:
    mesaj = input(f"{kullanici_adi}: ").lower()
    if "çıkış" in mesaj:
        print(f"Bot: Görüşürüz {kullanici_adi}!")
        break
    elif "hava" in mesaj:
        print("Bot:", random.choice(hava_durumu_havuzu))
Ders 6: Görsel Kolaj Motoru Koordinat Sistemi
İnternetten indirilen 10 adet resmi otomatik olarak 2 satır ve 5 sütun düzeninde birleştiren döngü algoritması:

Python
for i in range(10):
    x = (i % 5) * 100  # Sütun koordinat hesabı (0, 100, 200, 300, 400)
    y = (i // 5) * 100 # Satır koordinat hesabı (0 veya 100)
    tuval.paste(resimler[i], (x, y))
Sık Karşılaşılan Hatalar ve Çözümleri
Girinti Hatası (IndentationError): Python dilinde if, while veya for bloklarından sonra gelen satırların içe doğru (1 Tab veya 4 Boşluk) kaydırılması zorunludur. Blokların hizalamasına dikkat edilmelidir.

Küçük/Büyük Harf Duyarlılığı: Python büyük ve küçük harflere duyarlıdır. Kütüphane isimleri (pandas, qrcode) çağrılırken her zaman küçük harf kullanılmalıdır.

Tırnak İşaretleri: print() fonksiyonu içerisine yazılan metinsel ifadelerin tırnak işareti ile başlayıp yine tırnak işareti ile bittiğinden emin olunmalıdır.

Temel Hedef
Bu müfredat tamamlandığında öğrenciler; kodlama eğitiminin sadece metin tabanlı çıktılardan ibaret olmadığını; veri analitiği, yapay zeka mantığı, dijital tasarım ve görsel işleme gibi modern teknoloji alanlarının temel kurallarını uygulamalı olarak öğrenmiş olacaklardır.
