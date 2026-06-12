BÖLÜM 3: Grafik Çiz, Veriyi Görselleştir — Matplotlib ile Çizgi ve Bar Grafikler
---
Derse Giriş: Bir Grafik Bin Kelimeye Bedeldir
"League of Legends'in oyuncu sayısı son 5 yılda nasıl değişti?" Bu soruyu cevaplamak için bir tablo mu gösterirdin, yoksa bir grafik mi? Tabii ki grafik! Gözler sayıları okumakta yavaş, ama bir çizginin yukarı mı aşağı mı gittiğini saniyeler içinde algılar.
İşte bu yüzden her veri bilimcisi, her yapay zeka araştırmacısı, her teknoloji şirketinin analisti grafik çizmeyi biliyor. Ve bugün sen de öğreneceksin!
Kullanacağımız kütüphane: matplotlib. Adı biraz korkutucu ama kullanımı gerçekten eğlenceli. Bu derste oyun verilerini görselleştireceğiz — çizgi grafik, bar grafik, renkler, başlıklar...
---
Bilgi Kutusu: Temel Kavramlar
matplotlib.pyplot — Grafik Kağıdı
`matplotlib.pyplot`'u bir grafik kağıdı gibi düşün. `import matplotlib.pyplot as plt` diyerek bu kağıdı masana koyuyorsun.
X ve Y Ekseni — Koordinat Sistemi
Hani matematikte öğrendiğin o x-y ekseni? İşte aynısı. Grafikte:
X ekseni (yatay): Kategoriler ya da zaman (oyun isimleri, yıllar...)
Y ekseni (dikey): Sayısal değerler (oyuncu sayısı, puan, satış rakamı...)
plt.plot() vs plt.bar()
`plt.plot()` → Çizgi grafik — zaman içindeki değişimi göstermek için ideal
`plt.bar()` → Sütun (Bar) grafik — kategorileri karşılaştırmak için ideal
plt.show() — "Grafiği Göster!"
Grafiği oluşturduktan sonra `plt.show()` yazmazsan ekranda göremezsin. Google Colab'de bu satır olmasa da çalışır, ama alışkanlık edinmek iyi olur.
---
🛠️ Yapı İskelesi: 5 Adımda Kod
Adım 1 — İlk Çizgi Grafiği
```python
# matplotlib kütüphanesini import et
import matplotlib.pyplot as plt

# X ekseni: Yıllar
yillar = [2020, 2021, 2022, 2023, 2024]

# Y ekseni: Oyuncu sayısı (milyon cinsinden - tamamen hayali rakamlar!)
oyuncu_sayisi = [8, 12, 15, 11, 18]

# Basit çizgi grafik çiz
plt.plot(yillar, oyuncu_sayisi)

# Grafiği göster
plt.show()
```
> **Bu adımda ne değişti?** Sadece `plt.plot(x, y)` ve `plt.show()` ile ilk grafiğimizi çizdik! Henüz başlık yok, renk yok, etiket yok — ama çalışıyor!
---
Adım 2 — Renkler ve Nokta Stilleri Ekle
```python
import matplotlib.pyplot as plt

yillar = [2020, 2021, 2022, 2023, 2024]
oyuncu_sayisi = [8, 12, 15, 11, 18]

# color= ile renk seçimi (renk adı veya hex kod)
# marker= ile her noktaya şekil ekle
# linewidth= ile çizgi kalınlığı
# linestyle= ile çizgi stili ('--' kesik, ':' noktalı, '-' düz)

plt.plot(
    yillar,
    oyuncu_sayisi,
    color="crimson",      # Kırmızı çizgi
    marker="o",           # Her noktada yuvarlak
    linewidth=2.5,        # Çizgi kalınlığı
    linestyle="-"         # Düz çizgi
)

plt.show()
```
> **Bu adımda ne değişti?** Grafik artık çok daha şık! Renk, nokta işaretçisi ve çizgi kalınlığı ekledik. Kullanabileceğin bazı renkler: `"blue"`, `"red"`, `"green"`, `"orange"`, `"purple"`, `"#FF5733"` (hex renk kodu).
---
Adım 3 — Bar (Sütun) Grafiğine Dönüştür
```python
import matplotlib.pyplot as plt

# Bu sefer oyun isimlerini karşılaştıralım
oyunlar = ["Minecraft", "Fortnite", "Valorant", "CS:GO", "Roblox"]

# Aylık aktif oyuncu sayısı (milyon)
oyuncular = [173, 80, 26, 35, 200]

# Bar grafik çiz
plt.bar(
    oyunlar,          # X ekseni: oyun isimleri
    oyuncular,        # Y ekseni: oyuncu sayıları
    color="steelblue" # Sütun rengi
)

plt.show()
```
> **Bu adımda ne değişti?** `plt.plot()` yerine `plt.bar()` kullandık — ve anında sütun grafiğine geçtik! Bar grafik, kategorileri (oyun isimlerini) karşılaştırmak için çok daha uygun.
---
Adım 4 — Her Sütuna Farklı Renk Ver
```python
import matplotlib.pyplot as plt

oyunlar = ["Minecraft", "Fortnite", "Valorant", "CS:GO", "Roblox"]
oyuncular = [173, 80, 26, 35, 200]

# Her sütun için farklı renk listesi
renkler = ["#4CAF50", "#FF9800", "#F44336", "#2196F3", "#9C27B0"]
# Sırasıyla: yeşil, turuncu, kırmızı, mavi, mor

plt.bar(
    oyunlar,
    oyuncular,
    color=renkler,      # Tek renk yerine renk listesi
    edgecolor="black",  # Sütun kenar rengi
    linewidth=0.8       # Kenar çizgisi kalınlığı
)

plt.show()
```
> **Bu adımda ne değişti?** `color=` parametresine tek bir renk yerine renk listesi verdik. Artık her sütun farklı renkte! `edgecolor` ise sütunların etrafına ince siyah çizgi çiziyor — çok daha profesyonel görünüyor.
---
Adım 5 — Tam Profesyonel Grafik: Başlık, Eksen Etiketleri, Her Şey
```python
import matplotlib.pyplot as plt

# Veri
oyunlar = ["Minecraft", "Fortnite", "Valorant", "CS:GO", "Roblox"]
oyuncular = [173, 80, 26, 35, 200]
renkler = ["#4CAF50", "#FF9800", "#F44336", "#2196F3", "#9C27B0"]

# Grafik boyutunu ayarla (genişlik, yükseklik) inç cinsinden
plt.figure(figsize=(10, 6))

# Bar grafik
barlar = plt.bar(
    oyunlar,
    oyuncular,
    color=renkler,
    edgecolor="black",
    linewidth=0.8
)

# Her sütunun üstüne değerini yaz
for bar, deger in zip(barlar, oyuncular):
    plt.text(
        bar.get_x() + bar.get_width() / 2,  # Yatay konum: sütunun ortası
        bar.get_height() + 2,               # Dikey konum: sütunun biraz üstü
        f"{deger}M",                        # Yazan metin ("173M" gibi)
        ha="center",                        # Yatay hizalama: ortala
        fontweight="bold",                  # Kalın yazı
        fontsize=11
    )

# BAŞLIK ve EKSEN ETİKETLERİ
plt.title("En Popüler Oyunlar - Aylık Aktif Oyuncu (Milyon)",
          fontsize=16, fontweight="bold", pad=20)

plt.xlabel("Oyun Adı", fontsize=13)          # X ekseni etiketi
plt.ylabel("Oyuncu Sayısı (Milyon)", fontsize=13)  # Y ekseni etiketi

# Y ekseninin sınırlarını ayarla (en yüksek değerin biraz üstüne)
plt.ylim(0, 230)

# Izgara çizgileri (daha okunabilir grafik için)
plt.grid(axis="y", linestyle="--", alpha=0.5)  # Sadece yatay ızgara

# Grafiği göster
plt.tight_layout()  # Elemanların birbirine girmesini önler
plt.show()

print("Grafik başarıyla oluşturuldu!")
```
> **Bu adımda ne değişti?** Artık gerçekten profesyonel bir grafik var! Başlık, eksen etiketleri, her sütunun üstündeki değer, ızgara çizgileri, boyut ayarı... Bu grafik bir sunuma direkt girebilir!
---
Dikkat: Hata Canavarı!
Hata 1 — X ve Y Listelerinin Uzunluğu Farklı
```python
import matplotlib.pyplot as plt

#  YANLIŞ - 5 oyun adı ama 4 oyuncu sayısı
oyunlar = ["Minecraft", "Fortnite", "Valorant", "CS:GO", "Roblox"]
oyuncular = [173, 80, 26, 35]  # 4 eleman! Eksik!

plt.bar(oyunlar, oyuncular)  # HATA!
plt.show()

#  DOĞRU - Her iki liste de aynı uzunlukta olmalı
oyuncular_dogru = [173, 80, 26, 35, 200]  # 5 eleman
plt.bar(oyunlar, oyuncular_dogru)
plt.show()
```
Hata mesajı ne diyor? `ValueError: shape mismatch` veya buna benzer bir hata.
Çözümü: `len(oyunlar)` ve `len(oyuncular)` yazarak her iki listenin uzunluğunun eşit olduğunu kontrol et.
---
Hata 2 — plt.show() Sonra Yeni Şey Eklemeye Çalışmak
```python
import matplotlib.pyplot as plt

#  YANLIŞ - plt.show() grafiği kapatır, sonraki başlık eklenmez!
plt.bar(["A", "B", "C"], [1, 2, 3])
plt.show()
plt.title("Başlık")  # Bu eklenmez — grafik zaten kapandı!

#  DOĞRU - Önce her şeyi ekle, en son show() yaz
plt.bar(["A", "B", "C"], [1, 2, 3])
plt.title("Başlık")       # Önce başlık
plt.xlabel("Kategoriler") # Sonra etiket
plt.show()                # En SON göster
```
Çözümü: `plt.show()` çağrısını her zaman en sona bırak. Önce grafiğe eklemek istediğin her şeyi ekle, sonra göster.
---
 Sen de Dene!
Görev: Kendi Grafik Stüdyon
Aşağıdaki görevlerden birini (ya da hepsini!) tamamla:
Görev A — Çizgi Grafik: Son 5 ayda kaç dakika egzersiz yaptığını (ya da tamamen uydur!) bir listede sakla ve çizgi grafikle görselleştir. Rengi, çizgi stilini ve nokta işaretçilerini değiştir.
Görev B — Bar Grafik: 5 dersinin (Matematik, Türkçe, Fen, vb.) son sınav notlarını içeren bir bar grafik çiz. Her derse farklı renk ver, sütunların üstüne notları yaz.
Bonus: Her iki grafiği de aynı ekranda yan yana göster! İpucu: `plt.subplot(1, 2, 1)` ve `plt.subplot(1, 2, 2)` komutlarını araştır.
---
