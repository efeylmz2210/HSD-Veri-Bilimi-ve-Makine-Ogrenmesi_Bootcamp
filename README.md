#  E-Ticaret Veri Bilimi Analiz Projesi

Bu proje, e-ticaret sektörüne ait **"e_ticaret_veri_seti.csv"** verisinin Python ve Pandas kütüphaneleri kullanılarak incelenmesi, temizlenmesi, önişlemden geçirilmesi ve temel istatistiksel/görsel analizlerinin yapılmasını kapsamaktadır[cite: 4].

---

##  Projede Neler Yapıldı? (Adım Adım Özet)

1. **Veri Yükleme ve İnceleme:** Veri seti Google Drive üzerinden Colab ortamına aktarıldı, ilk ve son 10'ar satırı ile genel boyutu (`1428 satır, 18 sütun`) incelendi.
2. **Keşifçi Veri Analizi (EDA):** `info()` ve `describe()` metotlarıyla veri tipleri ve sayısal sütunların istatistiksel özetleri çıkarıldı; veriler sayısal ve kategorik olarak ayrıldı.
3. **Eksik Veri Analizi ve Temizliği:** 
   * Her sütundaki eksik değer sayıları ve oranları hesaplandı (en yüksek eksik oranına sahip ilk 5 sütun tespit edildi).
   * Sayısal eksik değerler (`indirim_orani`, `musteri_puani`) **medyan**, kategorik eksik değerler (`odeme_turu`, `musteri_tipi`) ise **mod** ile dolduruldu.
4. **Özellik Mühendisliği (Feature Engineering):** `siparis_tarihi` sütunu `datetime` formatına dönüştürülerek; *yıl, ay, gün* ve *haftanın günü* olmak üzere 4 yeni zaman tabanlı sütun türetildi.
5. **Tekrarlayan (Duplicate) Kayıtlar:** Tamamen aynı olan 28 adet koprak kayıt veri setinden temizlendi (Satır sayısı 1400'e düştü).
6. **Metin ve Kategori Standardizasyonu:** 
   * `sehir` sütunundaki büyük/küçük harf tutarsızlıkları ve Türkçe karakter hataları giderildi (Benzersiz şehir sayısı 19'dan 14'e indi).
   * `kategori` sütunundaki yazım farklılıkları (`Ev Yaşam`, `ev&yaşam` vb.) tek bir standart formata (`Ev Ve Yaşam`) getirildi.
7. **Mantıksal Hatalı Verilerin Ayıklanması:** Birim fiyatı veya toplam tutarı sıfır/negatif olan, teslimat günü negatif veya müşteri puanı 5'ten büyük olan 2 hatalı kayıt veri setinden çıkarıldı.
8. **Aykırı Değer (Outlier) Analizi:** `birim_fiyat` sütunu için **IQR (Çeyrekler Arası Açıklık)** yöntemi uygulanarak alt/üst sınırlar belirlendi ve 92 adet aykırı değer tespit edildi.
9. **Veri Görselleştirme:** 
   * `toplam_tutar` sütunu için **Histogram** (dağılımın sağa çarpık olduğunu görmek için) ve **Box Plot** (kategorilere göre dağılım) grafikleri çizdirildi.
   * Ödeme türlerinin dağılımını incelemek için **Count Plot** oluşturuldu.
10. **İleri Düzey İstatistiksel Soruların Cevaplanması:**
    * *En yüksek ortalama toplam tutara sahip kategori:* **Elektronik** (Ortalama: 3178.38 TL)
    * *En yüksek ortalama müşteri puanına sahip müşteri tipi:* **VIP / vip** (Ortalama Puan: 4.50)

---

##  Kullanılan Teknolojiler ve Kütüphaneler
* **Python**
* **Pandas & NumPy**
* **Matplotlib & Seaborn**
* **Google Colab**
