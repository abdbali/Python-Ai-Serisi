Google Colab ile Adım Adım Python ve Yapay Zekaya Giriş
Ortaokul ve Lise Öğrencileri için El Kitabı
---
> **Bu kitap hakkında:** Elindeki bu rehber, sana "programlama nasıl öğrenilir?" sorusunun cevabını vermek için tasarlandı. Burada sıkıcı formüller yok, ezber gerektiren teoriler yok. Bunun yerine: gerçek projeler, adım adım gelişen kodlar ve "bunu ben mi yaptım?" dedirten sonuçlar var. Hazırsan başlayalım!
---
BÖLÜM 1: Python'a Merhaba! — Veri Tipleri ve Temel Komutlar
---
 Derse Giriş: Neden Kodlama Öğreniyoruz?
Şunu hayal et: Sabah uyandın, telefona baktın, YouTube sana tam senin ilgi alanına göre videolar öneriyor. Spotify çalma listeni oluşturuyor. Instagram reels'lerin tam senin takıldığın türden. Sihir mi? Hayır — Python kodu.
Bugün öğreneceğin şeyler belki şu an çok küçük görünecek. Sadece ekrana yazı yazdırmak, sayı toplamak, kullanıcıdan bilgi almak... Ama bu adımlar olmadan o YouTube algoritması da, o öneri sistemi de, hiçbir şey olmaz. Bugün sıfırdan başlıyoruz — ama bu "sıfır" aslında her şeyin başlangıcı.
Bu derste şunları öğreneceksin:
Ekrana bir şey yazdırmak (`print()`)
Veri kutularına bilgi koymak (Değişkenler)
Farklı veri türlerini tanımak (String, Integer, Float)
Kullanıcıdan bilgi almak (`input()`)
---
 Bilgi Kutusu: Temel Kavramlar
`print()` — Ekrana Bağır!
`print()` komutu, Python'a "hey, bunu ekrana yaz!" demek için kullanılır. Parantezin içine ne yazarsan ekranda o görünür. Tıpkı bir hoparlöre bağlı mikrofon gibi — ne söylersen onu seslendirir.
Değişken — Etiketli Kutu
Değişkeni, üzerinde bir etiket olan bir kutu gibi düşün. Kutunun içine istediğin veriyi koyarsın, etiketi okuyarak da o veriye ulaşırsın.
```
[ isim = "Ahmet" ]
```
Kutunun etiketi `isim`, içindeki bilgi `"Ahmet"`. İstediğin zaman o kutuyu alıp kullanabilirsin.
Veri Tipleri — Kutunun Cinsi
Her kutunun bir cinsi vardır. Python'da 3 temel veri tipi var:
Tip	Ne İşe Yarar?	Örnek
String (str)	Metin/yazı	`"Merhaba Dünya"`
Integer (int)	Tam sayı	`42`, `2024`
Float	Ondalıklı sayı	`3.14`, `9.8`
String'lerde veriyi tırnak içine alman şart — `"böyle"` ya da `'böyle'`. Tırnak koymazsan Python "bu bir kelime mi, bir komut mu?" diye karışır.
`input()` — Kullanıcıdan Bilgi Al
`input()` komutu, program çalışırken kullanıcıdan bilgi almaya yarar. Parantezin içine bir soru yazarsın, kullanıcı cevaplar, sen de o cevabı bir değişkende saklarsın.
---
Yapı İskelesi: 5 Adımda Kod
Adım 1 — Sadece Ekrana Yaz
```python
# Ekrana bir şey yazdıralım
# print() komutu parantezin içindekini ekranda gösterir
# Metni tırnak içine almayı unutma!

print("Merhaba Dünya!")
print("Python öğreniyorum!")
print("Bu benim ilk kodum.")
```
> **Bu adımda ne değişti?** Hiçbir şey saklamıyoruz, sadece ekrana yazdırıyoruz. En temel Python komutu olan `print()`'i tanıştık.
---
Adım 2 — Veriyi Kutuya Koy (Değişken)
```python
# Değişken = etiketli kutu
# = işareti "kutunun içine bunu koy" demek

isim = "Zeynep"         # String (metin) değişken
yas = 14                # Integer (tam sayı) değişken
boy = 1.65              # Float (ondalıklı sayı) değişken

# Şimdi kutulardan veriyi çıkarıp ekrana yazdıralım
print(isim)
print(yas)
print(boy)
```
> **Bu adımda ne değişti?** Artık veriyi ekrana saçmıyoruz — önce kutulara koyuyoruz, sonra kullanıyoruz. Gerçek programlar hep böyle çalışır.
---
Adım 3 — Metinleri Birleştir
```python
# Metin birleştirme = "String Concatenation"
# + operatörü iki metni yan yana yapıştırır

isim = "Zeynep"
sehir = "İzmir"

# Yöntem 1: + ile birleştirme
print("Merhaba, " + isim + "! Hoş geldin.")

# Yöntem 2: f-string (daha modern ve kolay!)
# Süslü parantez içine değişken adını yazarsın
print(f"Merhaba, {isim}! {sehir}'de yaşıyorsun.")
print(f"Bugün harika bir gün!")
```
> **Bu adımda ne değişti?** Metinleri birleştirmeyi öğrendik. Özellikle f-string yöntemi çok kullanışlı — büyük projelerde hayat kurtarır!
---
Adım 4 — Sayısal İşlemler
```python
# Python bir hesap makinesi gibi çalışabilir
# +, -, *, / operatörlerini kullanabiliriz

not1 = 85       # 1. sınav notu
not2 = 92       # 2. sınav notu
not3 = 78       # 3. sınav notu

# Ortalama hesapla
ortalama = (not1 + not2 + not3) / 3

# Sonucu yazdır (round() ondalıkları yuvarlar)
print(f"1. Not: {not1}")
print(f"2. Not: {not2}")
print(f"3. Not: {not3}")
print(f"Notların ortalaması: {round(ortalama, 2)}")  # 2 ondalık basamak

# Bonus: Ekstra işlemler
print(f"En yüksek notun 2 katı: {not2 * 2}")
print(f"Notlar toplamı: {not1 + not2 + not3}")
```
> **Bu adımda ne değişti?** Artık sayılarla gerçek hesaplar yapabiliyoruz. `round()` fonksiyonu ondalıklı sonuçları düzenliyor.
---
Adım 5 — Kullanıcıdan Bilgi Al ve Kişiselleştir
```python
# input() komutu programı durdurur ve kullanıcıdan bilgi bekler
# Kullanıcının yazdığı her şey bir String olarak gelir

print("=== Kişisel Bilgi Kartı ===")

# Kullanıcıdan bilgi al
isim = input("Adın ne? ")
sehir = input("Hangi şehirde yaşıyorsun? ")
yas_str = input("Kaç yaşındasın? ")

# input() her şeyi String olarak getirir
# Sayısal işlem yapmak için int() veya float() ile dönüştür
yas = int(yas_str)

# Gelecekteki yaşı hesapla
gelecek_yas = yas + 10

# Kişiselleştirilmiş çıktı
print()  # Boş satır bırakmak için
print(f"=== Merhaba, {isim}! ===")
print(f" Şehir: {sehir}")
print(f" Yaşın: {yas}")
print(f" 10 yıl sonra {gelecek_yas} yaşında olacaksın!")
print(f" Python öğrendiğin için tebrikler!")
```
> **Bu adımda ne değişti?** Program artık robot gibi sabit çıktı vermiyor — kullanıcıya göre kişiselleşiyor! `int()` dönüşümünü ekledik çünkü `input()` her şeyi metin olarak alır.
---
 Dikkat: Hata Canavarı!
Hata 1 — Tırnak İşareti Unutmak
```python
#  YANLIŞ - Python "Merhaba" kelimesinin ne olduğunu bilmiyor
print(Merhaba)

#  DOĞRU - Metin tırnak içinde olmalı
print("Merhaba")
```
Hata mesajı ne diyor? `NameError: name 'Merhaba' is not defined`
Çözümü: Metin yazarken her zaman tırnak kullan — tek tırnak `'` veya çift tırnak `"`, ikisi de olur.
---
Hata 2 — String ile Sayı Toplamaya Çalışmak
```python
yas = input("Yaşın? ")   # input() bunu "14" stringi olarak getiriyor

#  YANLIŞ - "14" metni ile 5 sayısını toplayamazsın
print(yas + 5)

#  DOĞRU - Önce int() ile sayıya çevir
yas_sayi = int(yas)
print(yas_sayi + 5)
```
Hata mesajı ne diyor? `TypeError: can only concatenate str (not "int") to str`
Çözümü: `input()`'tan gelen veriyi sayısal işleme sokacaksan `int()` veya `float()` ile dönüştür.
---
Sen de Dene!
Görev: Vücut Kitle İndeksi (VKİ) Hesaplayıcı
Kullanıcıdan adını, boyunu (metre cinsinden, örn: 1.75) ve kilosunu alarak VKİ'sini hesaplayan bir program yaz.
Formül: `VKİ = kilo / (boy * boy)`
Örnek çıktı:
```
Adın? Emre
Boyun (metre)? 1.75
Kilonuz (kg)? 68
---
Merhaba Emre!
VKİ'n: 22.2
Bu değer normal aralıkta!
```
Bonus: VKİ 18.5'ten küçükse "Zayıf", 18.5-24.9 arasındaysa "Normal", 25'ten büyükse "Kilolu" yazdırmayı dene (if-elif-else'i ilerleyen derslerde öğreneceksin, ama merak ediyorsan şimdiden deneyebilirsin!).
---
---
