BÖLÜM 2: Verinin Gücü — Pandas ile Tablo ve Veri Seti İşleme
---
Derse Giriş: Veriler Olmadan Yapay Zeka Kör Olurdu
Şunu düşün: Netflix sana "şunu izle" diyor, Spotify "bu şarkıyı sev" diyor, TikTok "bu videoyu izle" diyor. Peki bunlar nasıl biliyor? Cevap: veri. Milyonlarca kullanıcının ne izlediği, ne dinlediği, ne beğendiği — hepsi tablolarda saklı.
İşte bu tablolara veri bilimi dünyasında Dataset (Veri Seti) deniyor. Ve Python'da bu tabloları yönetmek için en popüler araç: Pandas.
Bu derste kendi mini veri setini oluşturacak, ona yeni sütunlar ekleyecek ve istediğin koşula göre filtreleyeceksin. Hazırsan haydi tablolara dalalım!
---
Bilgi Kutusu: Temel Kavramlar
Kütüphane — Hazır Araç Kutusu
Bir kütüphane, başkaları tarafından yazılmış ve senin kullanımına sunulmuş hazır kod koleksiyonudur. Pandas'ı sen yazmak zorunda değilsin — binlerce geliştirici senin için yazmış, sen sadece kullanıyorsun.
`import pandas as pd` → "pandas kütüphanesini al ve ona kısaca `pd` de"
Neden `pd`? Uzun yazmamak için. `pandas.DataFrame()` yerine `pd.DataFrame()` yazıyoruz — daha kısa.
Liste — Sıralı Bilgi Dizisi
```python
# Köşeli parantez içine virgülle ayrılmış veriler
isimler = ["Ali", "Ayşe", "Can", "Derin"]
notlar = [85, 92, 78, 95]
```
Sözlük (Dictionary) — Anahtar-Değer Çifti
```python
# Süslü parantez, "anahtar": değer formatında
ogrenci = {
    "isim": "Ali",
    "not": 85,
    "sehir": "Ankara"
}
```
Sözlük, gerçek hayattaki bir sözlük gibi çalışır — "isim" kelimesini arar, karşısındaki "Ali" değerini bulursun.
DataFrame — Python'daki Excel Tablosu
DataFrame, satırlardan ve sütunlardan oluşan iki boyutlu bir veri yapısıdır. Excel tablosunu Python'da açtığını düşünebilirsin — ama çok daha güçlü!
isim	not	sehir
Ali	85	Ankara
Ayşe	92	İzmir
Can	78	İstanbul
---
🛠️ Yapı İskelesi: 5 Adımda Kod
Adım 1 — Basit Bir Liste
```python
# En basit hali: sadece bir liste
# Liste = köşeli parantez içinde virgülle ayrılmış veriler

ogrenci_isimleri = ["Ali", "Ayşe", "Can", "Derin", "Elif"]

# Listeyi ekrana yazdır
print("Öğrenci listesi:")
print(ogrenci_isimleri)

# Listedeki belirli bir elemana erişim (0'dan sayılır!)
print(f"İlk öğrenci: {ogrenci_isimleri[0]}")
print(f"Son öğrenci: {ogrenci_isimleri[-1]}")
print(f"Kaç öğrenci var? {len(ogrenci_isimleri)}")
```
> **Bu adımda ne değişti?** Liste veri yapısını tanıdık. Köşeli parantez, virgülle ayırma ve 0'dan başlayan indeks numaraları — temel liste kuralları bunlar.
---
Adım 2 — Sözlük ile Yapılandırılmış Veri
```python
# Sözlük = anahtar-değer çiftleri
# Birden fazla özelliği tek yapıda tut

# Birden fazla öğrencinin bilgilerini listede saklayalım
ogrenciler = [
    {"isim": "Ali",   "not": 85, "sehir": "Ankara"},
    {"isim": "Ayşe",  "not": 92, "sehir": "İzmir"},
    {"isim": "Can",   "not": 78, "sehir": "İstanbul"},
    {"isim": "Derin", "not": 95, "sehir": "Bursa"},
    {"isim": "Elif",  "not": 88, "sehir": "Antalya"}
]

# İlk öğrencinin bilgilerine erişim
print(ogrenciler[0])                    # Tüm sözlük
print(ogrenciler[0]["isim"])            # Sadece isim
print(ogrenciler[2]["not"])             # Can'ın notu
```
> **Bu adımda ne değişti?** Her öğrenciye ait birden fazla bilgiyi (isim, not, şehir) tek bir sözlükte bir araya getirdik. Bu yapı gerçek veri setlerine çok daha yakın.
---
Adım 3 — DataFrame ile Gerçek Tablo Yap
```python
# pandas kütüphanesini import et (ilk önce kütüphaneyi çağırıyoruz)
import pandas as pd

# Veriyi bir sözlük olarak hazırla
# Her sütun bir liste, her liste bir sütun oluyor
veri = {
    "isim":  ["Ali", "Ayşe", "Can", "Derin", "Elif"],
    "not":   [85, 92, 78, 95, 88],
    "sehir": ["Ankara", "İzmir", "İstanbul", "Bursa", "Antalya"]
}

# Sözlükten DataFrame (tablo) oluştur
df = pd.DataFrame(veri)

# Tabloyu ekrana yazdır — Excel gibi görünecek!
print(df)

# Tablo hakkında bilgi al
print(f"\nSatır ve sütun sayısı: {df.shape}")   # (5, 3) demek: 5 satır, 3 sütun
print(f"\nSütun isimleri: {list(df.columns)}")
```
> **Bu adımda ne değişti?** Artık gerçek bir tablomuz var! `pd.DataFrame()` ile veriyi düzgün bir tabloya dönüştürdük. `.shape` özelliği tablonun boyutunu söylüyor.
---
Adım 4 — Yeni Sütun Ekle
```python
import pandas as pd

veri = {
    "isim":  ["Ali", "Ayşe", "Can", "Derin", "Elif"],
    "not":   [85, 92, 78, 95, 88],
    "sehir": ["Ankara", "İzmir", "İstanbul", "Bursa", "Antalya"]
}

df = pd.DataFrame(veri)

# Yeni sütun ekleme: df["yeni_sutun"] = değer
# Her nota 5 bonus puan ekleyelim!
df["bonus_not"] = df["not"] + 5

# Başarı durumu sütunu ekle (bunu Bölüm 4'te daha detaylı öğreneceğiz)
# Şimdilik şunu bil: 90 üstü ise "Başarılı", değilse "Geçti" yazıyor
df["durum"] = ["Başarılı" if n >= 90 else "Geçti" for n in df["not"]]

# Güncellenmiş tabloyu göster
print("Güncellenmiş Tablo:")
print(df)
print(f"\nToplam sütun sayısı: {len(df.columns)}")
```
> **Bu adımda ne değişti?** Tabloya 2 yeni sütun ekledik: bonus notu ve başarı durumunu. Bu gerçek veri analizinde çok kullanılan bir işlem — var olan veriden yeni bilgiler üretmek!
---
Adım 5 — Tabloyu Filtrele
```python
import pandas as pd

veri = {
    "isim":  ["Ali", "Ayşe", "Can", "Derin", "Elif"],
    "not":   [85, 92, 78, 95, 88],
    "sehir": ["Ankara", "İzmir", "İstanbul", "Bursa", "Antalya"]
}

df = pd.DataFrame(veri)
df["bonus_not"] = df["not"] + 5
df["durum"] = ["Başarılı" if n >= 90 else "Geçti" for n in df["not"]]

print("=== TÜM TABLO ===")
print(df)
print()

# FİLTRELEME: Koşula uyan satırları seç
# df[ koşul ] formatını kullanıyoruz

# 90 üstü notlar
basarilar = df[df["not"] >= 90]
print("=== 90 VE ÜZERİ NOT ALANLAR ===")
print(basarilar)
print()

# Belirli şehirden olanlar
ankaralilar = df[df["sehir"] == "Ankara"]
print("=== ANKARALI ÖĞRENCİLER ===")
print(ankaralilar)
print()

# Ortalama ve istatistikler
print("=== İSTATİSTİKLER ===")
print(f"Not ortalaması: {df['not'].mean():.1f}")   # .1f = 1 ondalık basamak
print(f"En yüksek not: {df['not'].max()}")
print(f"En düşük not:  {df['not'].min()}")
```
> **Bu adımda ne değişti?** `df[koşul]` yazımıyla tabloyu filtrelemeyi öğrendik. Bu Pandas'ın en güçlü özelliği! Milyonlarca satırlık tablodan istediğin satırları anında çekebilirsin.
---
Dikkat: Hata Canavarı!
Hata 1 — Sütun Adında Yazım Hatası
```python
import pandas as pd
veri = {"isim": ["Ali", "Ayşe"], "not": [85, 92]}
df = pd.DataFrame(veri)

#  YANLIŞ - "Not" büyük N ile — Pandas büyük-küçük harfe duyarlıdır!
print(df["Not"])

# DOĞRU - Sütun adını tam olarak doğru yaz
print(df["not"])
```
Hata mesajı ne diyor? `KeyError: 'Not'`
Çözümü: `print(df.columns)` ile sütun adlarını kontrol et — tam olarak nasıl yazıldıklarını gör.
---
Hata 2 — Kütüphaneyi Import Etmemek
```python
#  YANLIŞ - pandas'ı import etmeden kullanmaya çalışmak
df = pd.DataFrame({"a": [1, 2, 3]})

# DOĞRU - Her zaman başa import yaz
import pandas as pd
df = pd.DataFrame({"a": [1, 2, 3]})
print(df)
```
Hata mesajı ne diyor? `NameError: name 'pd' is not defined`
Çözümü: Kütüphanenin import satırını kod bloğunun EN BAŞINA ekle. Google Colab'de her yeni hücreyi çalıştırdığında import satırlarının da çalışmış olması lazım!
---
 Sen de Dene!
Görev: Favori Oyunlar Veri Seti
Aşağıdaki görevleri sırayla gerçekleştir:
En az 5 favori oyununu içeren bir DataFrame oluştur. Sütunlar: `oyun_adi`, `tür` (aksiyon/macera/spor vb.), `puan` (100 üzerinden kendin ver), `platform` (PC/PS5/Mobile)
Tabloya bir `must_play` sütunu ekle: Puanı 85 ve üzeri olan oyunlara `"Kesinlikle Oyna!"`, diğerlerine `"Fena Değil"` yaz.
Sadece PC oyunlarını filtrele ve ekrana yazdır.
Oyunlarının ortalama puanını hesapla.
Bonus: Puanlara göre sırala (`df.sort_values("puan", ascending=False)` komutunu araştır!).
---
---
