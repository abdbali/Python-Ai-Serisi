BÖLÜM 6: Görsel Sihirbazlığı — Pillow ile Kolaj Makinesi
---
 Derse Giriş: Instagram Filtreleri Nasıl Çalışır?
Instagram'daki collage özelliği, fotoğraf uygulamalarındaki 9'lu grid, oyunlardaki karakter seçim ekranı... Bunların hepsinin arkasında şu soru var: "Bu görseli nasıl doğru koordinata yapıştırırım?"
Cevap: Pillow (PIL) kütüphanesi. Python'da görselleri açmak, yeniden boyutlandırmak, kesmek, birleştirmek — her şey için Pillow kullanılır.
Bu dersin sonunda internet'ten 10 resim indirecek, onları 100x100 piksel yapacak ve 2 satır × 5 sütunluk muhteşem bir mozaik kolaj oluşturacaksın. Bu kolaj Instagram'a bile atılabilir. Hazır mısın?
---
 Bilgi Kutusu: Temel Kavramlar
PIL / Pillow — Görsel Manipülasyon Kütüphanesi
Pillow, PIL'in (Python Imaging Library) modern ve devam ettirilen sürümüdür. `pip install Pillow` ile kurulur, ama Google Colab'de zaten yüklü gelir.
```python
from PIL import Image  # Pillow'dan Image modülünü al
```
Image.open() — Görseli Aç
```python
img = Image.open("resim.png")  # Dosyadan aç
```
resize() — Boyutu Değiştir
```python
kucuk = img.resize((100, 100))  # 100x100 piksel yap
```
Image.new() — Boş Tuval Oluştur
```python
tuval = Image.new("RGB", (500, 200), "white")  # 500x200 beyaz tuval
```
paste() — Görseli Yapıştır
```python
tuval.paste(img, (x, y))  # img'yi (x,y) koordinatına yapıştır
```
Koordinat Sistemi
Görselde (0, 0) sol üst köşe. X sağa, Y aşağı gider.
```
(0,0) ──────► X
  |
  |
  ▼
  Y
```
---
 Yapı İskelesi: 5 Adımda Kod
Adım 1 — Klasör Oluştur ve Görselleri İndir
```python
# Gerekli kütüphaneleri import et
import os          # Klasör işlemleri
import requests    # İnternetten dosya indirme

# "resimler" klasörü yoksa oluştur
klasor = "resimler"
if not os.path.exists(klasor):
    os.makedirs(klasor)
    print(f"'{klasor}' klasörü oluşturuldu!")
else:
    print(f"'{klasor}' klasörü zaten var.")

# İnternetten indirilecek resim URL'leri
# Picsum.photos = test resimleri için ideal, her seferinde farklı resim veriyor
# seed= parametresi aynı resmi garantilemek için
resim_urls = [
    "https://picsum.photos/seed/1/300/300",
    "https://picsum.photos/seed/2/300/300",
    "https://picsum.photos/seed/3/300/300",
    "https://picsum.photos/seed/4/300/300",
    "https://picsum.photos/seed/5/300/300",
    "https://picsum.photos/seed/6/300/300",
    "https://picsum.photos/seed/7/300/300",
    "https://picsum.photos/seed/8/300/300",
    "https://picsum.photos/seed/9/300/300",
    "https://picsum.photos/seed/10/300/300",
]

# Döngüyle tüm resimleri indir
print("\nResimler indiriliyor...")
for i, url in enumerate(resim_urls):
    # enumerate() hem indeks numarasını hem de değeri verir
    dosya_yolu = f"{klasor}/resim_{i+1}.jpg"

    # requests ile URL'den veri çek, dosyaya kaydet
    yanit = requests.get(url)
    with open(dosya_yolu, "wb") as f:    # "wb" = binary yazma modu
        f.write(yanit.content)

    print(f"  ✓ resim_{i+1}.jpg indirildi")

print(f"\n10 resim '{klasor}/' klasörüne kaydedildi!")
print(f"Klasördeki dosyalar: {os.listdir(klasor)}")
```
> **Bu adımda ne değişti?** `os.makedirs()` ile klasör oluşturduk, `requests.get()` ile internetten resim indirdik. `enumerate()` hem sayacı hem değeri birlikte veriyor — çok kullanışlı!
---
Adım 2 — Tek Resmi Aç ve 100x100 Yap
```python
from PIL import Image

# Birinci resmi açalım
resim_yolu = "resimler/resim_1.jpg"
img = Image.open(resim_yolu)

# Açılan resmin bilgileri
print(f"Orijinal boyut: {img.size}")     # (genişlik, yükseklik) piksel
print(f"Renk modu: {img.mode}")          # RGB = renkli, L = gri tonlamalı

# Resmi 100x100 piksel yap
kucuk = img.resize((100, 100))

print(f"Yeni boyut: {kucuk.size}")

# Küçültülmüş resmi kaydet ve göster
kucuk.save("kucuk_resim.png")

# Colab'de göster
from IPython.display import Image as IPyImage
IPyImage("kucuk_resim.png")
```
> **Bu adımda ne değişti?** `Image.open()` ile dosyayı açtık, `.resize()` ile boyutu değiştirdik. `.size` özelliği bize (genişlik, yükseklik) döndürüyor.
---
Adım 3 — Büyük Beyaz Tuval Aç
```python
from PIL import Image

# Kolaj için boyut hesapla:
# 5 sütun × 100 piksel = 500 piksel genişlik
# 2 satır × 100 piksel = 200 piksel yükseklik

genislik = 5 * 100    # 500
yukseklik = 2 * 100   # 200

# Image.new() ile boş tuval oluştur
# "RGB" = renkli mod (Red, Green, Blue)
# (genislik, yukseklik) = tuval boyutu
# "white" = arka plan rengi (beyaz)
tuval = Image.new("RGB", (genislik, yukseklik), "white")

print(f"Tuval oluşturuldu! Boyut: {tuval.size}")

# Tuval şu an tamamen beyaz
tuval.save("bos_tuval.png")

from IPython.display import Image as IPyImage
IPyImage("bos_tuval.png")
```
> **Bu adımda ne değişti?** `Image.new()` ile boş bir kanvas (tuval) oluşturduk. Resim karıştırma, kolaj yapma, görsel tasarım — hep bu boş tuvalden başlar.
---
Adım 4 — Döngüyle Resimleri Yan Yana Diz
```python
from PIL import Image
import os

# Kolaj parametreleri
KARE_BOYUT = 100    # Her resmin boyutu (piksel)
SUTUN_SAYISI = 5    # Yan yana kaç resim?
SATIR_SAYISI = 2    # Üst üste kaç satır?

# Tuval oluştur
tuval_genislik = SUTUN_SAYISI * KARE_BOYUT   # 500
tuval_yukseklik = SATIR_SAYISI * KARE_BOYUT  # 200
tuval = Image.new("RGB", (tuval_genislik, tuval_yukseklik), "white")

# Klasördeki tüm jpg dosyalarını al
klasor = "resimler"
dosyalar = sorted([f for f in os.listdir(klasor) if f.endswith(".jpg")])
print(f"Bulunan resim sayısı: {len(dosyalar)}")

# Resimleri döngüyle yapıştır
for indeks, dosya_adi in enumerate(dosyalar[:10]):  # En fazla 10 resim
    # Kaçıncı satır ve sütunda olduğumuzu hesapla
    # % (modulo) = bölümden kalan → sütun numarası
    # // (tam bölme) → satır numarası
    sutun = indeks % SUTUN_SAYISI      # 0, 1, 2, 3, 4, 0, 1, 2, 3, 4
    satir = indeks // SUTUN_SAYISI     # 0, 0, 0, 0, 0, 1, 1, 1, 1, 1

    # Yapıştırma koordinatını hesapla
    x = sutun * KARE_BOYUT  # Yatay konum
    y = satir * KARE_BOYUT  # Dikey konum

    # Resmi aç ve küçült
    resim_yolu = os.path.join(klasor, dosya_adi)
    img = Image.open(resim_yolu).resize((KARE_BOYUT, KARE_BOYUT))

    # Tuval üzerine yapıştır
    tuval.paste(img, (x, y))
    print(f"  {dosya_adi} → konum: ({x}, {y}) [Satır {satir+1}, Sütun {sutun+1}]")

# Kaydet
tuval.save("ara_kolaj.png")
print("\nKolaj kaydedildi!")

from IPython.display import Image as IPyImage
IPyImage("ara_kolaj.png")
```
> **Bu adımda ne değişti?** Koordinat hesabının sırrı: `%` (modulo) ve `//` (tam bölme). `indeks % 5` sütun numarasını (0-4), `indeks // 5` satır numarasını (0 veya 1) veriyor. Bu formülle 10 resmi otomatik olarak 2×5 grid'e yerleştirdik!
---
Adım 5 — Kusursuz Mozaik Kolaj: Boşluk + Çerçeve + Kayıt
```python
from PIL import Image, ImageDraw
import os

# === KOLAj AYARLARI ===
KARE_BOYUT = 120        # Her resim karesi (piksel)
BOSLUK = 8              # Resimler arası boşluk (piksel)
SUTUN_SAYISI = 5
SATIR_SAYISI = 2
ARKAPLAN_RENGI = "#2C2C2C"   # Koyu gri arka plan
CERCEVE_RENGI = "#FFFFFF"    # Beyaz çerçeve
# ======================

# Tuval boyutunu hesapla (boşluklar dahil)
tuval_genislik = (SUTUN_SAYISI * KARE_BOYUT) + ((SUTUN_SAYISI + 1) * BOSLUK)
tuval_yukseklik = (SATIR_SAYISI * KARE_BOYUT) + ((SATIR_SAYISI + 1) * BOSLUK)

# Koyu arka planlı tuval
tuval = Image.new("RGB", (tuval_genislik, tuval_yukseklik), ARKAPLAN_RENGI)

# Çizim nesnesi (çerçeve çizmek için)
cizim = ImageDraw.Draw(tuval)

# Resimleri al
klasor = "resimler"
dosyalar = sorted([f for f in os.listdir(klasor) if f.endswith(".jpg")])

print(f"Kolaj yapılıyor... {len(dosyalar[:10])} resim kullanılacak")
print(f"Tuval boyutu: {tuval_genislik}x{tuval_yukseklik} piksel\n")

for indeks, dosya_adi in enumerate(dosyalar[:10]):
    sutun = indeks % SUTUN_SAYISI
    satir = indeks // SUTUN_SAYISI

    # Boşluklu koordinat hesabı
    x = BOSLUK + sutun * (KARE_BOYUT + BOSLUK)
    y = BOSLUK + satir * (KARE_BOYUT + BOSLUK)

    # Resmi aç, yeniden boyutlandır
    resim_yolu = os.path.join(klasor, dosya_adi)
    img = Image.open(resim_yolu).resize((KARE_BOYUT, KARE_BOYUT))

    # Çerçeve çiz (resmin etrafına 2 piksel beyaz çizgi)
    cizim.rectangle(
        [x - 2, y - 2, x + KARE_BOYUT + 1, y + KARE_BOYUT + 1],
        outline=CERCEVE_RENGI,
        width=2
    )

    # Resmi yapıştır
    tuval.paste(img, (x, y))
    print(f"  ✓ {dosya_adi} yerleştirildi → ({x}, {y})")

# Kolajı kaydet
cikti_dosyasi = "mozaik_kolaj.png"
tuval.save(cikti_dosyasi, quality=95)

# Bilgi ver
dosya_boyutu = os.path.getsize(cikti_dosyasi)
print(f"\n Kolaj tamamlandı!")
print(f" Dosya: {cikti_dosyasi}")
print(f" Boyut: {tuval_genislik}x{tuval_yukseklik} piksel")
print(f" Dosya boyutu: {round(dosya_boyutu/1024, 1)} KB")

# Ekranda göster
from IPython.display import Image as IPyImage
IPyImage(cikti_dosyasi)
```
> **Bu adımda ne değişti?** Kolaj artık gerçekten profesyonel! Koyu arka plan, resimler arası boşluklar, her kareye beyaz çerçeve... `ImageDraw.Draw()` çizim araçlarını kullanmaya başladık. Bu son versiyonu Instagram'a atabilirsin!
---
Dikkat: Hata Canavarı!
Hata 1 — Pillow Yüklü Değil
```python
#  ImportError alıyorsan Pillow kurmak gerekiyor
from PIL import Image  # ModuleNotFoundError!

#  Önce kur (Colab'de genellikle yüklü gelir, ama kontrol et)
!pip install Pillow
from PIL import Image
```
---
Hata 2 — Yanlış Renk Modu ile Yapıştırma
```python
from PIL import Image

#  YANLIŞ - RGBA (şeffaflıklı) resmi RGB tuval'e paste etmek hata verir
tuval = Image.new("RGB", (200, 200), "white")
img_rgba = Image.open("seffaf_resim.png")  # RGBA modunda
tuval.paste(img_rgba, (0, 0))  # Hata!

# DOĞRU - Önce resmi RGB'ye çevir
img_rgb = img_rgba.convert("RGB")
tuval.paste(img_rgb, (0, 0))

# VEYA: RGBA görsel için mask parametresini kullan
tuval.paste(img_rgba, (0, 0), mask=img_rgba.split()[3])  # Alpha kanalı mask olarak
```
Hata mesajı ne diyor? `ValueError: images do not match` veya `Paste requires same mode`
Çözümü: `.convert("RGB")` ile resmin renk modunu tuvalle eşitle.
---
Sen de Dene!
Görev: Kendi Temalı Kolajın
Picsum.photos yerine gerçekten sevdiğin 10 resmi kullan (Colab'e yükle!).
Kolajın arka planını kendi favori renginle değiştir.
Kolajın boyutunu değiştir: 3 satır × 4 sütun (12 resim).
`KARE_BOYUT` değişkenini 150 yaparak daha büyük kareler dene.
Bonus Meydan Okuma: Kolajın ortasına büyük bir boşluk bırak (ortadaki kareler boş kalsın), oraya başlık metni yaz. İpucu: `ImageDraw.text()` fonksiyonunu araştır!
---
---
 Kitabın Sonu: Ama Yolculuk Yeni Başlıyor!
Tebrikler! 6 bölümü tamamladın. Şimdi bir adım geri çekil ve ne öğrendiğine bak:
Bölüm	Ne Öğrendim?	Gerçek Dünya Karşılığı
1	print(), değişkenler, input()	Her programın çekirdeği
2	Pandas, DataFrame, filtreleme	Veri analisti araçları
3	Matplotlib, bar/çizgi grafik	Veri görselleştirme
4	Chatbot, while, if-elif, random	Yapay zeka öncülü
5	QR kod üretme, kütüphane kurma	Gerçek ürün geliştirme
6	Pillow, görsel işleme, kolaj	Görsel yapay zeka temeli
Sırada ne var?
Eğer bu kitap seni heyecanlandırdıysa, şu konulara bakabilirsin:
Makine Öğrenmesi: scikit-learn kütüphanesiyle kendi tahmin modelini yap
Derin Öğrenme: TensorFlow veya PyTorch ile sinir ağları
Web Uygulamaları: Flask veya FastAPI ile Python web sunucusu
Oyun Geliştirme: Pygame ile 2D oyunlar
Veri Bilimi: Kaggle platformunda gerçek veri yarışmalarına katıl
Unutma: Dünyanın en iyi programcıları da bir zamanlar `print("Merhaba Dünya!")` yazarak başladı. Sen de bu adımı attın. Bundan sonrası sana kalmış!
> *"Herkes kodlamayı öğrenmeli. Çünkü kodlama, düşünmeyi öğretir."*
> — Steve Jobs
Bol hata, bol öğrenme, bol kod! 
