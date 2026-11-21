# Dunnhumby Kupon Analizi

Bir market zincirinde kuponların çoğu boşa gidiyor. Bu projede **doğru haneyi**, **doğru kuponu** ve **kuponun gerçekten işe yarayıp yaramadığını** veriyle bulmaya çalıştık.

> Workintech veri analisti bootcamp'i (DATA0826.2) ekip projesi

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tansuuludag/dunnhumby-kupon-analizi/blob/main/notebooks/dunnhumby_kupon_analizi.ipynb)

## Veri
[Dunnhumby – The Complete Journey](https://www.dunnhumby.com/source-files/): 2.500 hanenin iki yıllık alışverişi, 8 tablo (işlemler, ürünler, kampanyalar, kuponlar, demografi).
Ham veri bu repoda yok; kaynağından indirilir.

## Mimari
BigQuery → dbt (temizlik ve modelleme) → Colab (istatistik ve ML) → Power BI (sunum)

dbt modelleri ekip reposunda: [UmitKargaci/Dunnhumby-Complete-Journey](https://github.com/UmitKargaci/Dunnhumby-Complete-Journey)

## Yaptıklarımız
1. **Hane profili ve segmentasyon:** k-means ile 4 segment. k = 4, sadık müşterileri iki farklı davranışa ayırdığı için seçildi (büyük sepetli kuponcular ve sık gelen fiyat duyarlılar).
2. **Birliktelik analizi:** Makarna ve sos tesadüfen beklenenden 9,8 kat daha sık birlikte alınıyor (destek %2,6, güven %55). Kupon içeriği buna göre önerildi.
3. **Hipotez testleri:** Segmentler arası harcama ve kampanya yanıtı farkları.
4. **Kupon yanıt modeli:** Hangi hanenin kuponu kullanacağı tahmin edildi.
5. **Geri dönüş takibi:** Ziyaretleri düşen hanelerden kupon kullananların %29,9'u, kullanmayanların %23,0'ı eski düzenine döndü.

## Sonuç ve sınırlar
Kupon kullananlarda geri dönüş daha yüksek, ancak fark istatistiksel olarak anlamlı değil (iki oran z testi, z = 1,36, p ≈ 0,17). Bu yüzden öneri, rastgele kontrol gruplu bir deneme: seçilen haneler ikiye bölünür, yarısına kupon gönderilir, sonuç ölçülür.

