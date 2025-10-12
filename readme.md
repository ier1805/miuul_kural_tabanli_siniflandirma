KURAL TABANLI SINIFLANDIRMA
===========================
Potansiyel Müşteri Getirisi Hesaplama

Bu proje, bir oyun şirketinin müşterilerinin demografik özelliklerine dayanarak kural tabanlı sınıflandırma (rule-based classification) yöntemiyle potansiyel müşteri segmentleri oluşturmasını ve her segmentin şirkete sağlayabileceği ortalama gelir tahminini amaçlamaktadır.

-------------------
İŞ PROBLEMİ
------------
Bir oyun şirketi, müşterilerinin bazı özelliklerini (ülke, cihaz türü, cinsiyet, yaş) kullanarak seviye tabanlı (level-based) yeni müşteri tanımları (persona) oluşturmak ve bu tanımlara göre segmentasyon yaparak yeni müşterilerin tahmini gelirini belirlemek istemektedir.

Örnek:
Türkiye’den IOS kullanan 25 yaşındaki bir erkek kullanıcının ortalama kazandırabileceği miktarın tahmin edilmesi.

-------------------
VERİ SETİ HİKAYESİ
-------------------
persona.csv dosyası, uluslararası bir oyun şirketinin satış verilerini içerir.
Her satış işlemi için bir kayıt oluşturulmuştur, bu nedenle tablo tekilleştirilmemiştir.
Yani belirli özelliklere sahip bir kullanıcı birden fazla alışveriş yapmış olabilir.

Değişkenler:
- PRICE: Müşterinin harcama tutarı
- SOURCE: Bağlanılan cihaz türü (Android / iOS)
- SEX: Cinsiyet (male / female)
- COUNTRY: Ülke (TUR, FRA, USA, DEU, BRA vb.)
- AGE: Müşterinin yaşı

-------------------
PROJE GÖREVLERİ
-------------------

GÖREV 1: Temel Analizler
-------------------------
1. persona.csv dosyasını okuyun ve genel bilgi özetini çıkarın.
2. Unique SOURCE sayısı ve frekansları.
3. Unique PRICE sayısı.
4. Her bir PRICE değerinden kaç satış gerçekleştiği.
5. Ülkelere göre satış sayıları.
6. Ülkelere göre toplam gelir.
7. SOURCE türlerine göre satış sayısı.
8. Ülkelere göre PRICE ortalamaları.
9. SOURCE’lara göre PRICE ortalamaları.
10. COUNTRY-SOURCE kırılımında PRICE ortalamaları.

GÖREV 2: Ortalama Kazanç Analizi
---------------------------------
- COUNTRY, SOURCE, SEX, AGE kırılımında ortalama kazançlar hesaplanır.

GÖREV 3: Sıralama
-----------------
- Çıktı, PRICE değerine göre azalan şekilde sıralanır ve agg_df olarak kaydedilir.

GÖREV 4: İndeks Dönüşümü
------------------------
- PRICE dışındaki tüm değişken adları index konumundadır.
- Bu değişken adları sütun ismine dönüştürülür.

GÖREV 5: Yaş Kategorileri
-------------------------
- AGE değişkeni kategorik hale getirilir.
- Önerilen aralıklar: 0_18, 19_23, 24_30, 31_40, 41_70
- Yeni sütun: AGE_CAT

GÖREV 6: Yeni Persona Oluşturma
-------------------------------
- Aşağıdaki formata göre yeni müşteri profilleri tanımlanır: COUNTRY_SOURCE_SEX_AGE_CAT
- Bu değerler birleştirilerek customers_level_based değişkeni oluşturulur.
- Oluşan değerler tekilleştirilir ve her persona için ortalama PRICE değeri alınır.

GÖREV 7: Segmentasyon
---------------------
- Yeni oluşturulan personelar, ortalama PRICE değerine göre 4 segmente ayrılır.
- Segment isimleri: A, B, C, D
- Her segment için price ortalaması, maksimumu ve toplamı hesaplanır.

GÖREV 8: Yeni Müşteri Tahmini
-----------------------------
Yeni bir müşteri geldiğinde, demografik bilgilerine göre ait olduğu segment belirlenir ve ortalama gelir tahmini yapılır.

Örnekler:
1. 33 yaşında, ANDROID kullanan Türk kadını → Hangi segmente ait? Beklenen ortalama gelir?
2. 35 yaşında, IOS kullanan Fransız kadını → Hangi segmente ait? Beklenen ortalama gelir?

-------------------
KULLANILAN KÜTÜPHANELER
------------------------
import pandas as pd

-------------------
ÖĞRENME HEDEFLERİ
------------------
- Segmentasyon mantığını kavrama
- Pandas ile grup bazlı ortalama hesaplama
- Yeni değişken türetme (categorical & combined features)
- Kural tabanlı müşteri sınıflandırması
- Veriden persona çıkarımı ve segment analizi

-------------------
PROJE AKIŞI
------------
1. Veri seti okuma ve keşif
2. Gruplama (groupby)
3. Kategorik dönüşüm (cut, apply)
4. Persona oluşturma (list comprehension)
5. Segmentleme (qcut)
6. Yeni müşteri tahmini

-------------------
KAYNAK
-------
Bu proje MIUUL tarafından hazırlanan “Kural Tabanlı Sınıflandırma” eğitim materyalinden uyarlanmıştır.
www.miuul.com
