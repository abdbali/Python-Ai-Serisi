BÖLÜM 5: İlk Görsel Üret — QR Kod Makinesi
---
 Derse Giriş: QR Kod Nedir ve Neden Havalıdır?
Menülerde, ürünlerde, afişlerde o siyah-beyaz kareli deseni gördün mü? İşte bu QR kod! İçinde bir URL, bir metin, bir telefon numarası ya da ne istersen saklayabilirsin. Telefon kamerası ile tarandığında otomatik olarak içindeki bilgiye ulaşırsın.
Peki bunu Python ile kendin üretebilir misin? Tabii ki! Üstelik istersen sarı arka planlı, lacivert kareli özel renkli QR kodlar da yapabilirsin.
Bu derste aynı zamanda çok önemli bir şey öğreneceksin: Yeni bir kütüphane nasıl kurulur? Google Colab'de her bilgisayarda olmayan kütüphaneleri tek satır komutla kurabilirsin.
---
Bilgi Kutusu: Temel Kavramlar
`!pip install` — Kütüphane Kur
Google Colab'de `!pip install kütüphane_adı` yazarak herhangi bir Python kütüphanesini anında kurabilirsin. `!` işareti "bu Python kodu değil, terminal komutu" demek.
```python
!pip install qrcode[pil]
```
qrcode Kütüphanesi
QR kodlarını oluşturmak için özel geliştirilmiş bir kütüphane. İçindeki `QRCode` sınıfı QR kodun özelliklerini (boyut, hata düzeltme) ayarlaman için kullanılır.
QR Kod Parametreleri
Parametre	Ne İşe Yarar?
`version`	QR'nin boyutu ve veri kapasitesi (1-40, büyük = daha fazla veri)
`box_size`	Her küçük karenin piksel boyutu
`border`	QR'nin etrafındaki beyaz boşluk (min. 4 önerilir)
PIL (Pillow) — Görsel İşleme
QR kodu bir görsel dosya olarak kaydetmek için PIL kütüphanesini kullanırız. PIL (Pillow), Python'da görsellerle çalışmak için en yaygın kütüphane.
---
🛠️ Yapı İskelesi: 5 Adımda Kod
Adım 1 — Kütüphaneyi Kur
```python
# ! işareti = "bu Python değil, terminal komutu"
# pip = Python paket yöneticisi
# qrcode[pil] = qrcode kütüphanesi + Pillow görsel desteği

!pip install qrcode[pil]

# Kurulum tamamlandıktan sonra import edelim
import qrcode

print("qrcode kütüphanesi başarıyla kuruldu ve import edildi!")
print("Artık QR kod üretmeye hazırız 🎉")
```
> **Bu adımda ne değişti?** `!pip install` ile yeni bir kütüphane kurduk. Google Colab'de bu çok hızlı gerçekleşir — genellikle 5-10 saniye. Bir daha çalıştırırsan "zaten kurulu" diyecek.
---
Adım 2 — İlk QR Kod: Düz Metni QR'a Çevir
```python
import qrcode

# QR koda çevirmek istediğimiz metin
metin = "Merhaba! Bu benim ilk QR kodum!"

# En basit yol: qrcode.make() tek satırda QR üretir
qr_gorsel = qrcode.make(metin)

# Görseli kaydet
qr_gorsel.save("ilk_qr.png")
print("QR kod oluşturuldu ve 'ilk_qr.png' olarak kaydedildi!")

# Google Colab'de görseli ekranda göster
from IPython.display import Image
Image("ilk_qr.png")
```
> **Bu adımda ne değişti?** Tek satır `qrcode.make()` ile QR kodu oluşturduk! `save()` ile dosyaya kaydettik ve `Image()` ile Colab ekranında görüntüledik. Şimdi bunu telefonunla tarayabilirsin!
---
Adım 3 — Boyutu ve Kenar Boşluğunu Ayarla
```python
import qrcode
from IPython.display import Image as IPyImage

# QRCode sınıfı ile daha fazla kontrol
qr = qrcode.QRCode(
    version=1,              # 1 = en küçük QR boyutu (yeterli veri için)
    box_size=10,            # Her kare 10x10 piksel (büyütmek için artır)
    border=4                # Kenar boşluğu: 4 kare genişlik (standart minimum)
)

# QR'a veri ekle
qr.add_data("https://www.python.org")
qr.make(fit=True)  # fit=True: veriye göre otomatik boyut ayarla

# Görseli oluştur (henüz renk yok)
qr_gorsel = qr.make_image(fill_color="black", back_color="white")

# Kaydet ve göster
qr_gorsel.save("python_qr.png")
print("Python resmi sitesine yönlendiren QR kod hazır!")
IPyImage("python_qr.png")
```
> **Bu adımda ne değişti?** `qrcode.QRCode()` sınıfını kullanarak daha fazla kontrol kazandık. `box_size` değerini büyütürsen QR kod daha büyük olur. URL de eklemeyi öğrendik — artık tarandığında bir siteye götürüyor!
---
Adım 4 — Özel Renkler: Sarı Arka Plan, Lacivert Kod
```python
import qrcode
from IPython.display import Image as IPyImage

# QR kodunu yapılandır
qr = qrcode.QRCode(
    version=2,       # 2 = biraz daha büyük, daha fazla veri kapasitesi
    box_size=12,     # Her kare 12x12 piksel
    border=4
)

# İstediğin metni veya URL'yi buraya yaz
qr.add_data("Merhaba Ben Python QR Kodum!")
qr.make(fit=True)

# fill_color = QR karelerinin rengi
# back_color = arka plan rengi
# Renkleri İngilizce veya hex kodla yazabilirsin
qr_gorsel = qr.make_image(
    fill_color="#1a237e",   # Lacivert (koyu mavi hex kodu)
    back_color="#FFF176"    # Sarı (açık sarı hex kodu)
)

# Kaydet ve göster
qr_gorsel.save("renkli_qr.png")
print("Renkli QR kod hazır! ")
IPyImage("renkli_qr.png")
```
> **Bu adımda ne değişti?** `fill_color` ve `back_color` parametreleriyle QR koduna renk verdik! Hex renk kodlarını kullanmak istersen Google'a "color picker" yaz ve istediğin rengin hex kodunu kopyala.
---
Adım 5 — Dosyayı Kaydet ve Colab'den İndir
```python
import qrcode
import os
from IPython.display import Image as IPyImage, display

# --- KİŞİSELLEŞTİR! ---
kisi_adi = "Zeynep"
kisi_web = "https://github.com"  # Kendi profilin veya siten
# ----------------------

# QR kodunu ayarla
qr = qrcode.QRCode(
    version=3,
    box_size=15,        # Daha büyük kareler = daha büyük QR
    border=5
)

# Kişiselleştirilmiş metin oluştur
icerik = f"Ad: {kisi_adi} | Web: {kisi_web}"
qr.add_data(icerik)
qr.make(fit=True)

# Özel renk kombinasyonu
qr_gorsel = qr.make_image(
    fill_color="#4A148C",    # Mor
    back_color="#F3E5F5"     # Açık lila
)

# Dosya adı oluştur (kişinin adıyla)
dosya_adi = f"{kisi_adi.lower()}_qr_kodu.png"
qr_gorsel.save(dosya_adi)

# Dosya boyutunu kontrol et
dosya_boyutu = os.path.getsize(dosya_adi)
print(f" QR Kod oluşturuldu!")
print(f" Dosya adı: {dosya_adi}")
print(f" Dosya boyutu: {dosya_boyutu} byte")
print(f" İçerik: {icerik}")
print()

# Ekranda göster
display(IPyImage(dosya_adi))

print(" İndirmek için: Sol panelde  ikonuna tıkla, dosyayı sağ tıkla → İndir!")
```
> **Bu adımda ne değişti?** Tam bir uygulama yaptık! QR kod içeriği kişiselleştirilebilir, dosya adı dinamik, `os.path.getsize()` ile dosya boyutunu kontrol ediyoruz ve Colab'den nasıl indirileceğini de öğrendik.
---
 Dikkat: Hata Canavarı!
Hata 1 — Kütüphane Kurulmadan Kullanmaya Çalışmak
```python
#  YANLIŞ - pip install yapmadan import edersen hata alırsın
import qrcode

# DOĞRU - Önce kur, sonra import et
!pip install qrcode[pil]  # Kurulum hücresi
import qrcode              # Sonraki hücrede import
```
Hata mesajı ne diyor? `ModuleNotFoundError: No module named 'qrcode'`
Çözümü: `!pip install qrcode[pil]` satırını çalıştır. Colab her oturum açıldığında kurulumların tekrarlanması gerekebilir!
---
Hata 2 — QR Kodunun Taranmaması
Eğer QR kodun telefon tarafından tanınmıyorsa:
`box_size` çok küçük olabilir — 10 veya daha büyük yap
`border` çok küçük olabilir — en az 4 yap
Renk kontrastı çok düşük olabilir — koyu renk üzerine açık renk veya tam tersi
```python
# Taranmayan QR için bu ayarları dene
qr = qrcode.QRCode(
    version=1,
    box_size=15,    # Büyük kareler
    border=6        # Geniş kenar
)
qr_gorsel = qr.make_image(fill_color="black", back_color="white")  # Klasik siyah-beyaz
```
---
 Sen de Dene!
Görev: QR Kartvizit Üreteci
Şu bilgileri içeren kişisel bir QR kartvizit üret:
`input()` ile kullanıcıdan şu bilgileri al: Ad Soyad, E-posta, Favori sosyal medya linki
Bu bilgileri şu formatta birleştir:
```
   Ad: [ad]
   Email: [email]
   Sosyal: [link]
   ```
Bundan bir QR kod üret — rengi ve boyutu kendin seç!
Dosyayı `[isim]_kartvizit.png` olarak kaydet.
Bonus: Aynı kodu döngüyle 3 farklı kişi için çalıştır ve 3 ayrı QR kartvizit üret!
---
---
