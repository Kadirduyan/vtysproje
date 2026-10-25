<div align="center">

# Hastane Yönetim ve Otomasyon Sistemi (VTYS)

**PostgreSQL İlişkisel Veritabanı Mimarisi ve C# (.NET Windows Forms) Tabanlı Kurumsal Hastane Otomasyonu**

[![C#](https://img.shields.io/badge/C%23-.NET_Framework_4.7.2-239120?style=for-the-badge&logo=csharp&logoColor=white)](https://learn.microsoft.com/en-us/dotnet/csharp/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Relational_DB-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Npgsql](https://img.shields.io/badge/Npgsql-ADO.NET_Driver-336791?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.npgsql.org/)
[![Windows Forms](https://img.shields.io/badge/Windows_Forms-Desktop_UI-0078D6?style=for-the-badge&logo=windows&logoColor=white)](https://learn.microsoft.com/en-us/dotnet/desktop/winforms/)

</div>

---

## 1. Proje Özeti ve Mühendislik Yaklaşımı

**Hastane Yönetim ve Otomasyon Sistemi**, sağlık kuruluşlarındaki hasta kabul, poliklinik, doktor, randevu, reçete ve tıbbi kayıt süreçlerini **normalleştirilmiş (3NF) ilişkisel veritabanı mimarisi** üzerinde yönetmek amacıyla geliştirilmiş bir masaüstü otomasyon yazılımıdır.

Proje kapsamında **PostgreSQL** üzerinde kurgulanan ilişkisel şema, yabancı anahtar kısıtlamaları (Foreign Key Constraints), saklı yordamlar (Stored Procedures / Functions) ve tetikleyiciler (Triggers); **C# Windows Forms** ve **Npgsql ADO.NET** veri erişim katmanı ile entegre edilmiştir.

---

## 2. Sistem Mimarisi ve Veritabanı Özellikleri

- **İlişkisel Veritabanı Tasarımı (PostgreSQL):** Veri bütünlüğünü (Data Integrity) garanti altına alan birincil/yabancı anahtar ilişkileri, kalıtım/alt-tür tabloları ve referans kısıtlamaları.
- **Tetikleyiciler (Triggers) & Fonksiyonlar:** Kayıt ekleme, güncelleme ve silme işlemlerinde otomatik denetim ve iş kurallarını veritabanı motoru seviyesinde yürüten PL/pgSQL yapıları.
- **Çoklu Form Masaüstü Arayüzü (`Form1` – `Form5`):**
  - Kullanıcı/Yönetici giriş ve yetkilendirme ekranı
  - Hasta kayıt, arama ve geçmiş muayene sorgulama modülü
  - Doktor, poliklinik ve randevu planlama ekranları
  - Dinamik CRUD (Ekleme, Listeleme, Güncelleme, Silme) veri ızgaraları (`DataGridView`)
- **Npgsql Veri Erişim Katmanı:** Parametreli SQL sorguları ile SQL Injection zafiyetlerine karşı güvenli ve hızlı PostgreSQL bağlantısı.

---

## 3. Klasör Mimarisi (Directory Tree)

```text
vtysproje/
└── VeriTabanıYönetimSistemleriÖdevi1/
    ├── hastaneOtomasyonu01.sql                 # PostgreSQL veritabanı şeması, tablolar, fonksiyonlar ve trigger'lar
    ├── hastaneOtomasyonu001                    # PostgreSQL veritabanı yedek (backup/dump) dosyası
    ├── veriTabanıYönetimSistemleriRaporu.pdf   # ER diyagramı, normalizasyon ve sistem tasarım raporu
    └── Hastane/                                # C# (.NET Framework 4.7.2) Windows Forms Uygulaması
        ├── Program.cs                          # Uygulama ana giriş noktası
        ├── Form1.cs / Form1.Designer.cs        # Ana giriş ve navigasyon formu
        ├── Form2.cs / Form2.Designer.cs        # Hasta ve randevu yönetim modülü
        ├── Form3.cs / Form3.Designer.cs        # Doktor ve poliklinik yönetim modülü
        ├── Form4.cs / Form4.Designer.cs        # Muayene, reçete ve tıbbi kayıt modülü
        ├── Form5.cs / Form5.Designer.cs        # Raporlama ve detaylı sorgulama ekranı
        ├── packages.config                     # Npgsql ve bağımlı NuGet paket yapılandırması
        └── Hastane.csproj                      # Visual Studio C# proje dosyası
```

---

## 4. Kurulum ve Çalıştırma

### 4.1. Ön Gereksinimler
- **PostgreSQL** (`12+`) ve **pgAdmin 4**
- **Visual Studio 2022** (.NET Masaüstü Geliştirme iş yükü)
- **.NET Framework 4.7.2**

### 4.2. Adım Adım Kurulum

1. **Veritabanının Oluşturulması:**
   - **pgAdmin 4** veya `psql` üzerinden yeni bir veritabanı oluşturun.
   - `VeriTabanıYönetimSistemleriÖdevi1/hastaneOtomasyonu01.sql` betiğini çalıştırarak tüm tabloları, ilişkileri ve trigger'ları içe aktarın.
2. **Uygulamanın Derlenmesi ve Çalıştırılması:**
   - `Hastane/Hastane.csproj` dosyasını Visual Studio ile açın.
   - Form sınıfları içerisindeki `NpgsqlConnection` bağlantı dizesini (`Host=localhost;Port=5432;Database=...;Username=postgres;Password=...`) kendi yerel PostgreSQL yapılandırmanıza göre güncelleyin.
   - NuGet paketlerini geri yükleyin ve `F5` tuşu ile projeyi başlatın.

---

## 5. Geliştirici (Author)

**Kadir Duyan** — *Sakarya Üniversitesi Bilgisayar Mühendisliği*  
- **GitHub:** [github.com/Kadirduyan](https://github.com/Kadirduyan)
- **LinkedIn:** [linkedin.com/in/kadir-duyan4](https://www.linkedin.com/in/kadir-duyan4)
- **E-posta:** [kadirduyan482@gmail.com](mailto:kadirduyan482@gmail.com)
