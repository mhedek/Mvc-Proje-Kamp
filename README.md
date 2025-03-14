# 🚀 C# Eğitim Serisi - Katmanlı Mimari & EF Core 🚀

Bu repo, **[C# Eğitim Serisi](https://youtube.com/playlist?list=PLKnjBHu2xXNNQJehhCg--CzQQMHXTsFAb&si=Q1RfFTwDF4NOB64N)** kapsamında **Katmanlı Mimari (Layered Architecture), Entity Framework Core (EF Core) ve Migration işlemleri** ile ilgili derslerde ele alınan konuları içermektedir. 

✅ **Bu projede neler öğreneceksiniz?**  
✔️ Katmanlı Mimari Yapısı (Entity, Data Access, Business)  
✔️ Entity Framework Core ile Veritabanı İşlemleri  
✔️ Migration Yönetimi ve Veritabanı Güncellemeleri  
✔️ Tabloların Oluşturulması ve İlişkisel Yapılar  

---

## 📌 **Proje Yapısı ve Katmanlar**

Bu proje, **4 ana katmandan** oluşmaktadır:

📂 **1. Entity Layer (Varlık Katmanı)**  
- Veritabanındaki tabloları temsil eden sınıfları içerir.  
- **Örnek:** `About`, `Context`, `Category` gibi entity'ler burada yer alır.  

📂 **2. Data Access Layer (Veri Erişim Katmanı - DAL)**  
- Entity Framework Core kullanarak CRUD işlemlerini gerçekleştirir.  
- **Repository Design Pattern** uygulanmıştır.  
- **Örnek:** `GenericRepository`
- Context classı içinde tanımladığımız tablolarımız
  
          public class Context : DbContext
        {
            public DbSet<About> Abouts { get; set; }
            public DbSet<Category> Categories { get; set; }
            public DbSet<Contact> Contacts { get; set; }
            public DbSet<Content> Contents { get; set; }
            public DbSet<Heading> Headings { get; set; }
            public DbSet<Writer> Writers { get; set; }
        }

📂 **3. Business Layer (İş Katmanı - BLL)**  
- Veri erişim işlemleri ile iş kurallarını birbirinden ayırır.  
- İş kurallarını yönetir ve doğrulamalar içerir.  
- **Örnek:** , `CategoryManager`  

📂 **4. Presentation Layer (Sunum Katmanı - UI)**  
- Kullanıcıya arayüz sağlar.  
- ASP.NET Core MVC veya .NET MAUI gibi UI teknolojileri ile entegre edilebilir.  

---

## 🔗 **Entity Layer (Varlık Katmanı)**
Entity katmanı, **veritabanı tablolarını temsil eden** sınıflardan oluşur.  
Örnek bir **Category** (Kategori) entity’si:

    public class Category
    {
        [Key]
        public int CategoryID { get; set; }

        [StringLength(50)]
        public string CategoryName { get; set; }

        [StringLength(200)]
        public string CategoryDescription { get; set; }

        public bool CategoryStatus { get; set; }
        public ICollection<Heading> Headings { get; set; }

    }
