# C# Banka Uygulaması (2023‑2024 Güz Dönemi)

> Sakarya Üniversitesi Bilgisayar Mühendisliği – **Veri Tabanı Yönetim Sistemleri** dersi dönem projesi  
> **Geliştiriciler:** İbrahim Güldemir · Süleyman Samet Kaya  
> **Repo:** <https://github.com/ibrhmgldmr3/CSharp-Banka-Uygulamasi>

---

## İçerik

- [Proje Hakkında](#proje-hakkında)
- [Özellikler](#özellikler)
- [Teknolojiler](#teknolojiler)
- [Kurulum](#kurulum)
- [Çalıştırma](#çalıştırma)
- [Kullanım](#kullanım)
- [Dizin Yapısı](#dizin-yapısı)
- [İletişim](#iletişim)

---

## Proje Hakkında

Bu depo, **masaüstü** (WinForms) olarak geliştirilen bir *Banka Otomasyonu* uygulamasının tüm kaynak kodunu ve PostgreSQL veritabanı betiklerini içerir.  
Projenin amacı, **temel bankacılık işlemleri** (müşteri & hesap yönetimi, para yatırma/çekme, havale/EFT, işlem geçmişi vb.) ile **veritabanı‐uygulama entegrasyonu** konularını pratiğe dökmektir. citeturn2view0

---

## Özellikler

|  Modül / Ekran  | İşlevler |
| --------------- | -------- |
| **Müşteri Yönetimi** | Yeni müşteri ekleme, bilgileri güncelleme, silme |
| **Hesap Yönetimi**   | Aynı müşteriye birden fazla hesap açma, IBAN / hesap no üretimi |
| **İşlemler**         | Para yatırma · çekme · **hesaplar arası transfer** (Havale / EFT) |
| **Raporlama**        | Güncel bakiye görüntüleme, filtrelenebilir işlem geçmişi |
| **Yetkilendirme**    | “Görevli” ve “Müdür” rolleriyle farklı yetki seviyeleri |
| **Veritabanı Scriptleri** | `SQL Dosyaları/` klasöründe PostgreSQL **PL/pgSQL** fonksiyonları, trigger’lar, test verileri |

---

## Teknolojiler

| Katman | Yığın / Araçlar |
| ------ | --------------- |
| **Arayüz** | WinForms (.NET 6) + Guna.UI2 (modern kontroller) |
| **İş Mantığı** | Katmanlı mimari, OOP (SOLID), Data Transfer Objects |
| **Veri Erişimi** | `Npgsql` (ADO.NET) + parametreli sorgular |
| **Veritabanı** | **PostgreSQL 15** · PL/pgSQL procedure & trigger’lar |
| **Diğer** | Visual Studio 2022, Git & GitHub |

---

## Kurulum

### 1. Depoyu klonla

```bash
git clone https://github.com/ibrhmgldmr3/CSharp-Banka-Uygulamasi.git
cd CSharp-Banka-Uygulamasi
```

### 2. NuGet paketlerini geri yükle

```bash
dotnet restore        # veya Visual Studio ilk açılışta otomatik yapar
```

### 3. Veritabanını hazırla

1. PostgreSQL’de **bankadb** adlı boş bir veritabanı oluştur.  
2. `SQL Dosyaları/` klasöründeki dosyaları sırasıyla çalıştır:  
   1. `01_tables.sql` — Temel tablo yapıları  
   2. `02_functions.sql` — Saklı fonksiyonlar / trigger’lar  
   3. `03_seed_data.sql` — Örnek veriler (isteğe bağlı)

> **Bağlantı dizesi:** `App.config`/`appsettings.json` içindeki `Host`, `Port`, `Username`, `Password` ve `Database` alanlarını kendi PostgreSQL ayarlarınla güncelle.

---

## Çalıştırma

Terminalden:

```bash
dotnet run --project VTYSODEV2       # veya Visual Studio > Start
```

> İlk çalıştırmada uygulama veritabanına bağlanır, giriş ekranı (yetkili / müşteri) görünür.

---

## Kullanım

1. **Giriş Yap:**  
   - *Görevli* rolü → Müşteri ve hesap işlemleri  
   - *Müdür* rolü → Ek olarak raporlama & yetkilendirme  
2. **Müşteri / Hesap Ekle:** Formu doldur, “Kaydet”e bas.  
3. **Para İşlemleri:**  
   - *Para Yatır / Çek* sekmesinden tutar gir → Onayla.  
   - *Transfer* sekmesinde hedef IBAN’ı yaz, tutarı gir.  
4. **Geçmiş:** İstediğin tarih aralığı için filtrele, PDF/CSV dışa aktar.

---

## Dizin Yapısı

```text
CSharp-Banka-Uygulamasi/
├── VTYSODEV2/               # C# WinForms çözümü
│   ├── Forms/               # UI formları
│   ├── Data/                # DB bağlantısı & sorgular
│   ├── Services/            # İş mantığı
│   ├── Models/              # DTO / entity sınıfları
│   └── VTYSODEV2.csproj
├── SQL Dosyaları/           # PostgreSQL scriptleri
│   ├── 01_tables.sql
│   ├── 02_functions.sql
│   └── 03_seed_data.sql
├── .gitignore
└── README.md                # Bu dosya
```

---

## İletişim

| Kanal   | Bilgi |
| ------- | ----- |
| E‑posta | ibrahimguldemir123@gmail.com |
| LinkedIn| <https://www.linkedin.com/in/ibrhmgldmr/> |
| GitHub  | <https://github.com/ibrhmgldmr3> |

---

> **Katkılar & Hatalar:** PR veya Issue açmaktan çekinme!  
> Projeyi beğendiysen ⭐ vererek destek olabilirsin.
