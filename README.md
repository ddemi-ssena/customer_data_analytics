# 🛍️ Customer Shopping Behavior Analysis

**Proje:** Müşteri Alışveriş Davranışı Analizi (SQL, Python & Power BI)

**Kısa Açıklama**
Bu depo, 3.900 kayıtlı perakende işlem verisi kullanılarak müşteri satın alma eğilimleri, segmentasyonu ve ürün performansını analiz eden tam bir veri analitiği projesini içerir. Analizler PostgreSQL üzerinde gelişmiş SQL sorguları ile hazırlanmış; veri temizleme/işleme Python (Pandas) ile yapılmış ve sonuçlar etkileşimli bir Power BI dashboard'u ile sunulmuştur.

---

## 🎯 Hedefler

* Müşteri segmentasyonu: Yeni, Geri Dönen, Sadık.
* Harcama eğilimleri: Yaş grupları ve abonelik durumuna göre ort. harcama & toplam gelir.
* Ürün performansı: Kategori bazında en çok satan ürünler ve en yüksek indirimle satılan ilk 5 ürün.
* Karar vericiler için etkileşimli Power BI panosu.

---

## ⚙️ Kullanılan Teknolojiler

* **Veritabanı:** PostgreSQL
* **Veri işleme:** Python (Pandas)
* **Analiz:** SQL (PostgreSQL, CTE, window functions)
* **Rapor/Görselleştirme:** Microsoft Power BI
* **Araçlar / Notlar:** Jupyter Notebook / .ipynb dosyaları repo'da bulunmaktadır.

---

## 📁 Depo Yapısı (Önerilen)

```
/ (repo root)
├─ data/                      # (Opsiyonel) ham veya örnek veri dosyaları (küçük örnekler)
├─ notebooks/
│  └─ customer_shopping_behavior_analysis.ipynb
├─ sql/
│  └─ analysis_queries.sql
├─ powerbi/
│  └─ Shopping_Behavior_Report.pbix   # (isteğe bağlı, büyük dosyaysa LFS önerilir)
├─ scripts/
│  └─ load_to_postgres.py
├─ requirements.txt
├─ .gitignore
├─ README.md
└─ LICENSE
```

> Not: Gerçek (ve büyük) veri dosyalarını GitHub'a koyacaksanız **Git LFS** kullanmanızı veya veri setini paylaşmak istemiyorsanız örnek/örneklenmiş bir CSV koymanızı öneririm.

---

## 🔁 Kurulum & Çalıştırma (Local)

Aşağıdaki adımlar, projenin yerel makinede çalıştırılması içindir.

1. Depoyu klonlayın veya indirin.

```bash
git clone https://github.com/<kullaniciadi>/<repo>.git
cd <repo>
```

2. Sanal ortam oluşturun ve bağımlılıkları yükleyin.

```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. PostgreSQL veritabanı oluşturun (örnek):

```sql
-- psql içinde
CREATE DATABASE customer_behavior;
-- veya terminalde: createdb customer_behavior
```

4. `config` veya `.env` dosyanıza PostgreSQL bağlantı bilgilerini ekleyin (örneğin: `DB_HOST`, `DB_PORT`, `DB_NAME`, `DB_USER`, `DB_PASS`).

5. Veriyi veritabanına yükleyin:

```bash
python scripts/load_to_postgres.py --config config.yml
```

*Not:* `load_to_postgres.py` Jupyter dışı otomasyon için örnek bir betiktir. Aynı işlemi notebook içinde interaktif olarak da çalıştırabilirsiniz (`customer_shopping_behavior_analysis.ipynb`).

6. `sql/analysis_queries.sql` dosyasındaki sorguları PostgreSQL üzerinde çalıştırarak sonuçları doğrulayın.

7. Power BI Desktop ile veritabanına bağlanın: `Get Data -> PostgreSQL database` ve bağlantı bilgilerinizi girin. Ardından raporu açın veya kendi görselleştirmelerinizi oluşturun.

---

## 🧩 Önemli Notlar / İpuçları

* **Eksik veriler:** `Review Rating` sütunundaki eksik değerler median ile dolduruldu (notebook içinde gösterilmiştir).
* **Sütun formatı:** Tüm sütun adları `snake_case` formatına çevrildi.
* **Feature engineering:** `age_group`, `is_subscriber`, `loyalty_segment` gibi yeni sütunlar üretildi; bunlar analiz sorgularında kullanıldı.
* **SQL teknikleri:** CTE, window functions, CASE ifadeleri, aggregations, partitioning.
* **Power BI:** Dashboard'da dinamik filtreleme (cinsiyet, kategori) ve KPI kartları yer alıyor. Büyük `.pbix` dosyalarını repo'ya koyarken dikkatli olun (LFS veya alternatif paylaşım).

---

## 📌 Sık Kullanılan Komutlar & Örnek SQL

* Jupyter notebook açma:

```bash
jupyter lab
# veya
jupyter notebook
```

* PostgreSQL'e sorgu çalıştırma (psql):

```bash
psql -h localhost -U <user> -d customer_behavior -f sql/analysis_queries.sql
```

> `sql/analysis_queries.sql` içindeki sorgular örnek olarak 10 iş sorusunu cevaplar (abonelik etkisi, sadakat sınıflandırması, kategori liderleri, indirim bağımlılığı vb.).

---

## 📷 Power BI Dashboard Notları

* Önerilen görselleştirmeler: KPI kartları, stacked bar (yaş grubu gelir dağılımı), line chart (zamanla satış), matrix (kategori -> ürün sıralaması), slicer (cinsiyet, kategori).
* Dashboard açıklamaları ve kullanım kılavuzu README içinde veya `powerbi/README.md` içinde kısa not olarak eklenebilir.

---

## Lisans & Atıf

* **Atıf:** Proje yapı ve metodolojisi Amlan Mohanty'nin "Complete Data Analytics Portfolio Project" serisinden esinlenerek hazırlanmıştır.
* **License:** (Öneri) MIT License — ihtiyaçınıza göre değiştirin. `LICENSE` dosyası ekleyin.

---

## İletişim

Herhangi bir sorun ya da katkı için PR/Issue açabilirsiniz. (İletişim bilgisi veya e-posta adresi ekleyin.)

---

**Hazırlayan:** [Adınız]

*Son güncelleme: YYYY-MM-DD*
