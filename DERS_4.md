BÖLÜM 4: Kendi Chatbot'unu Yap — While, If-Elif ve Akıllı Hafıza
---
 Derse Giriş: ChatGPT'nin Dedesi
ChatGPT, Claude, Gemini... Bunların hepsini biliyorsun. Ama peki, ilk chatbot'lar nasıldı? 1966'da MIT'de yapılan "ELIZA" adlı program, sadece kalıp metinlere bakarak cevap veriyordu. "Annem beni üzüyor" yazınca "Annenden bahset." diyordu. Sihir yok, sadece `if-elif-else`!
Bugün sen de kendi chatbot'unu yapacaksın. Başta sadece "merhaba" diyecek, sonra farklı sorulara farklı cevaplar verecek, sonra seninle sürekli konuşacak ve en sonunda adını hatırlayacak. Hazır mısın?
---
Bilgi Kutusu: Temel Kavramlar
`if-elif-else` — Karar Ağacı
Bir kararlar zinciri. "Eğer şuysa şunu yap, yoksa şuysa bunu yap, hiçbirisi değilse onu yap."
```
Saat sabah mı?  → Günaydın!
Saat öğleden sonra mı? → İyi günler!
Değilse → İyi akşamlar!
```
`while True` — Sonsuz Döngü
`while True` bir şeyi "sonsuza kadar tekrarla" demek. Döngüden çıkmak için `break` komutu kullanılır. Chatbot'ların temel mekanizması budur — "çık" yazana kadar konuşmaya devam et.
`random.choice()` — Rastgele Seçim
`random` kütüphanesinin `choice()` fonksiyonu, bir listeden rastgele bir eleman seçer. Bunu kullanarak chatbot'un hep aynı cevabı vermesini önleyebilirsin — tıpkı gerçek bir konuşmada gibi!
---
Yapı İskelesi: 5 Adımda Kod
Adım 1 — Robot Sadece Selam Versin
```python
# En basit chatbot: sadece bir şey söyleyen robot
# print() ile konuşan, ama dinlemeyen bir varlık...

print("=== BotPy v0.1 ===")
print("BotPy: Merhaba! Ben bir robot.")
print("BotPy: Programlanmış şeyler söyleyebilirim.")
print("BotPy: Ama seni dinleyemiyorum henüz.")
print("BotPy: Görüşmek üzere!")
```
> **Bu adımda ne değişti?** Henüz gerçek bir chatbot değil — sadece ekrana sabit metinler yazdırıyor. Ama başlangıç böyle olur!
---
Adım 2 — Tek if ile Tek Kelime Kontrol
```python
# input() ile kullanıcı yazar, if ile kontrol ederiz
# Ama henüz sadece TEK bir cevap verebiliyoruz

print("=== BotPy v0.2 ===")

mesaj = input("Sen: ")

# Basit if kontrolü
if mesaj == "merhaba":
    print("BotPy: Merhaba! Nasılsın?")
else:
    print("BotPy: Bunu anlayamadım.")
```
> **Bu adımda ne değişti?** Robot artık dinliyor! `input()` kullanıcıyı bekliyor, `if` ile ne yazıldığını kontrol ediyor. Ama sadece "merhaba"yı anlıyor — çok kısıtlı.
---
Adım 3 — elif ile Seçenek Artır
```python
# elif = "else if" kısaltması
# Birden fazla koşulu art arda kontrol eder

print("=== BotPy v0.3 ===")
print("(Dene: merhaba, nasılsın, güle güle, yardım)")

mesaj = input("Sen: ").lower()  # .lower() büyük harfi küçüğe çevirir

if mesaj == "merhaba":
    print("BotPy: Merhaba! Hoş geldin!")

elif mesaj == "nasılsın":
    print("BotPy: İyiyim, teşekkürler! Sen nasılsın?")

elif mesaj == "güle güle":
    print("BotPy: Güle güle! Tekrar görüşmek üzere!")

elif mesaj == "yardım":
    print("BotPy: Sana şu komutlarda yardımcı olabilirim:")
    print("       - merhaba, nasılsın, güle güle, yardım")

else:
    print(f"BotPy: '{mesaj}' yazısını anlayamadım. 'yardım' yaz!")
```
> **Bu adımda ne değişti?** `elif` ile birden fazla koşul ekledik! `.lower()` önemli: Kullanıcı "Merhaba" veya "MERHABA" yazsa bile, küçük harfe çevirip doğru karşılaştırma yapıyoruz.
---
Adım 4 — while ile Sürekli Konuşan Bot
```python
# while True = "sonsuza kadar tekrarla"
# break = döngüden çık

print("=== BotPy v0.4 - Sonsuz Konuşma Modu ===")
print("('çık' yazarak sohbeti bitirebilirsin)")
print()

# Bu döngü break yazılana kadar dönmeye devam eder
while True:
    mesaj = input("Sen: ").lower().strip()  # .strip() baştaki/sondaki boşlukları siler

    if mesaj == "çık" or mesaj == "exit" or mesaj == "bye":
        print("BotPy: Görüşmek üzere! ")
        break  # Döngüden çık

    elif mesaj == "merhaba" or mesaj == "hey" or mesaj == "selam":
        print("BotPy: Merhaba! Seninle konuşmak güzel!")

    elif mesaj == "nasılsın":
        print("BotPy: Harika hissediyorum! Python kodu yazmak beni mutlu eder.")

    elif mesaj == "kaç yaşındasın":
        print("BotPy: Ben 2024 yılında doğdum, yani 1 yaşındayım!")

    elif mesaj == "güle güle":
        print("BotPy: Güle güle! Umarım yakında tekrar konuşuruz!")
        break

    else:
        print(f"BotPy: '{mesaj}' dedin, ama ne demek istediğini anlayamadım ")

print("Sohbet sona erdi.")
```
> **Bu adımda ne değişti?** Dev adım! `while True` döngüsüyle bot artık sürekli dinliyor. `break` komutu "çık" yazıldığında döngüyü sonlandırıyor. Bot artık gerçek bir chatbot gibi davranıyor!
---
Adım 5 — Rastgele Cevaplar + İsim Hafızası
```python
# random kütüphanesi rastgele seçim yapmamızı sağlar
import random

print("=== BotPy v1.0 - AKILLI MOD ===")
print("(İlk önce adını soracağım!)")
print()

# Kullanıcının adını başta al ve HATIRLA
kullanici_adi = input("BotPy: Merhaba! Ben BotPy. Senin adın ne? ").strip()
print(f"BotPy: Harika isim, {kullanici_adi}! Şimdi konuşabiliriz.")
print(f"BotPy: ('çık' yazarak ayrılabilirsin)\n")

# Rastgele cevap listeleri — aynı soruya her seferinde farklı cevap!
merhaba_cevaplari = [
    f"Merhaba {kullanici_adi}! Ne güzel görüşüyoruz!",
    f"Hey {kullanici_adi}! Bugün nasıl gidiyor?",
    f"Selam {kullanici_adi}! Seni görünce mutlu oldum!",
    f"Merhaba! Umarım günün iyi geçiyordur, {kullanici_adi}!"
]

nasil_cevaplari = [
    "Harika hissediyorum, teşekkürler!",
    "Süper! Python kodu yazınca hep iyi hissediyorum.",
    "Eh, fena sayılmam. Sen nasılsın?",
    "Gayet iyi! Bugün çok şey öğrendim."
]

bilmiyorum_cevaplari = [
    "Hmm, bunu bilmiyorum... Ama öğrenmeye çalışırım!",
    "İlginç soru! Maalesef cevabını bilmiyorum.",
    "Bu konuda bilgim yok. Google'a sormayı dene!",
    "Bunu anlayamadım, başka türlü sormalısın belki?"
]

# Ana sohbet döngüsü
while True:
    mesaj = input(f"{kullanici_adi}: ").lower().strip()

    if mesaj in ["çık", "exit", "bye", "güle güle"]:
        print(f"BotPy: Görüşmek üzere, {kullanici_adi}!  İyi günler!")
        break

    elif any(kelime in mesaj for kelime in ["merhaba", "selam", "hey", "hi"]):
        # random.choice() listeden rastgele bir eleman seçer
        print(f"BotPy: {random.choice(merhaba_cevaplari)}")

    elif any(kelime in mesaj for kelime in ["nasılsın", "ne haber", "iyi misin"]):
        print(f"BotPy: {random.choice(nasil_cevaplari)}")

    elif "adın ne" in mesaj or "ismin ne" in mesaj:
        print("BotPy: Benim adım BotPy! Python ile yazıldım.")

    elif "kaç yaşında" in mesaj:
        print("BotPy: Python kodu olarak yaşım yok ama bu yıl doğdum sayılırım!")

    elif "python" in mesaj:
        print("BotPy: Python harika bir dil! Ben de Python ile yazıldım 🐍")

    elif mesaj == "":
        print("BotPy: Bir şeyler yazmadan konuşamayız! ")

    else:
        print(f"BotPy: {random.choice(bilmiyorum_cevaplari)}")
```
> **Bu adımda ne değişti?** İki büyük özellik eklendi: 1) `random.choice()` ile her soruya farklı cevap — artık robot gibi değil, daha insan gibi! 2) Kullanıcının adı hatırlanıyor ve konuşma boyunca kullanılıyor. Bu basit ama etkili bir "hafıza" sistemi!
---
 Dikkat: Hata Canavarı!
Hata 1 — Sonsuz Döngüden Çıkamamak
```python
#  YANLIŞ - break komutu yok, program sonsuza kadar döner!
while True:
    mesaj = input("Yaz: ")
    print(f"Yazdın: {mesaj}")
    # break yok! Ctrl+C ile durdurmak zorundasın

#  DOĞRU - çıkış koşulu ve break ekle
while True:
    mesaj = input("Yaz (çık için 'dur' yaz): ")
    if mesaj == "dur":
        break  # Döngüden çık!
    print(f"Yazdın: {mesaj}")
```
Çözümü: Google Colab'de sonsuz döngüye girersen çalışma hücresinin yanındaki ■ (stop) butonuna tıkla!
---
Hata 2 — İndentasyon (Girinti) Hatası
```python
# YANLIŞ - if bloğunun içi girintisiz!
if mesaj == "merhaba":
print("Merhaba!")   # IndentationError!

#  DOĞRU - if'in içi 4 boşluk (veya 1 Tab) girintili olmalı
if mesaj == "merhaba":
    print("Merhaba!")  # 4 boşluk girinti
```
Hata mesajı ne diyor? `IndentationError: expected an indented block`
Çözümü: Python'da blokları girinti ile belirtirsin. `if`, `while`, `for` gibi komutların altındaki satırlar 4 boşluk ya da 1 Tab içeriden başlamalı. Google Colab bunu otomatik yapıyor — Tab tuşuna basabilirsin.
---
 Sen de Dene!
Görev: Kişilik Testli Bot
Chatbot'unu şu özelliklerle geliştir:
Kullanıcıya adının yanı sıra bir de favori rengi sor ve hatırla.
"Favori rengin ne?" diye sorulunca hatırladığı rengi söylesin.
"Şaka yap" yazınca aşağıdaki listeden rastgele bir şaka söylesin:
```python
   sakalar = [
       "Programcı neden güneşi sevmez? Çünkü Windows açık!",
       "Python neden yavaş mı? Çünkü çok uyuyor!",
       "Neden bilgisayarlar hiç hasta olmaz? Çünkü Windows'ları var!"
   ]
   ```
"Skor" yazınca kullanıcının kaç kez mesaj yazdığını söylesin (bir sayaç değişkeni tut!).
---
---
