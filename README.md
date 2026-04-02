# 🏢 GÖKDEMİR Mali Müşavirlik Ofis Programı

Modern bir web tabanlı **Mükellef ve Beyanname Takip Sistemi** için geliştirilmiş profesyonel yazılım.

## 📋 Özellikler

### ✅ Mükellef Yönetimi
- Mükellef bilgilerinin kaydedilmesi ve takibi
- Vergi numarası, firma adı, müşteri tipi (Bilançolı/Bilançosuz/Şirket)
- Durum yönetimi (Aktif/Pasif)
- Aylık ücret takibi
- Arama ve filtreleme

### ✅ Beyanname Yönetimi
- **4 Türde Beyanname Takibi:**
  - KDV (Katma Değer Vergisi)
  - Muhtasar
  - Gelir Vergisi
  - Kurumlar Vergisi
- Beyanname durumu (Hazırlanıyor/Hazır/Gönderildi/Kabul Edildi)
- Dönem ve tarih takibi
- Vergi miktarı kayıtları

### ✅ E-Defter Gönderileri
- E-Defter gönderim takibi
- Durum yönetimi (Hazırlanıyor/Gönderiye Hazır/Gönderildi/Onaylandı/Red)
- Dosya adı ve açıklama
- Tarih ve dönem bilgileri

### ✅ Mali Raporlar
- **Aylık Raporlar:** Seçilen ay ve yıl için detaylı raporlar
- **Yıllık Raporlar:** Tam yıl özeti
- Vergi miktarı, indirim, net tutar takibi
- Özet kartları (Toplam mükellef, vergi, net, beyanname sayısı)

## 🏗️ Teknik Yapı

### Frontend
- **React 18** + TypeScript
- **React Router** - Sayfa navigasyonu
- **Axios** - API iletişimi
- Modern CSS styling

### Backend
- **Node.js** + **Express.js**
- **PostgreSQL** - İlişkisel veritabanı
- RESTful API
- CORS desteği

### Database
- PostgreSQL 12+
- 4 Ana Tablo: mükellefler, beyannameler, e_defter, raporlar
- Optimize edilmiş indeksler
- İlişkisel bütünlük

## 🚀 Kurulum Rehberi

### Ön Gereksinimler
- Node.js 14+
- PostgreSQL 12+
- npm veya yarn

### 1️⃣ Backend Kurulumu

```bash
cd backend
npm install

# .env dosyasını kopyala ve düzenle
cp .env.example .env
```

**`.env` dosyasını düzenle:**
```env
DB_USER=postgres
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=5432
DB_NAME=gokdemir
PORT=5000
NODE_ENV=development
```

**PostgreSQL'de veritabanını oluştur:**
```bash
# PostgreSQL'e giriş yap
psql -U postgres

# Veritabanı oluştur
CREATE DATABASE gokdemir;

# Migration'ı çalıştır
psql -U postgres -d gokdemir < ../database/migrations/001_initial_schema.sql

# Çık
\q
```

**Backend'i başlat:**
```bash
npm run dev
```

Backend şu adresde çalışacak: `http://localhost:5000`

### 2️⃣ Frontend Kurulumu

```bash
cd frontend
npm install

# .env dosyasını kopyala
cp .env.example .env
```

**Frontend'i başlat:**
```bash
npm start
```

Frontend şu adresle açılacak: `http://localhost:3000`

## 📊 API Endpoints

### Mükellefler
```
GET    /api/mükellefler              - Tüm mükellefleri getir
GET    /api/mükellefler/ara/:terim   - Mükellef ara
POST   /api/mükellefler              - Yeni mükellef ekle
PUT    /api/mükellefler/:id          - Mükellef güncelle
```

### Beyannameler
```
GET    /api/beyannameler             - Tüm beyannameleri getir
GET    /api/beyannameler/tur/:tur    - Türe göre beyannameler
GET    /api/beyannameler/mükellef/:id - Mükellife ait beyannameler
POST   /api/beyannameler             - Yeni beyanname ekle
PUT    /api/beyannameler/:id         - Beyanname güncelle
```

### E-Defter
```
GET    /api/e-defter                 - Tüm e-defter gönderileri
GET    /api/e-defter/mükellef/:id    - Mükellife ait e-defter
POST   /api/e-defter                 - Yeni e-defter gönderimi
PUT    /api/e-defter/:id             - E-defter güncelle
```

### Raporlar
```
GET    /api/raporlar/aylik/:ay/:yil  - Aylık rapor
GET    /api/raporlar/yillik/:yil     - Yıllık rapor
GET    /api/raporlar/ozet/:ay/:yil   - Rapor özeti
POST   /api/raporlar                 - Yeni rapor oluştur
```

## 📁 Proje Yapısı

```
GOKDEMIR-SMMM-OFIS-PROGRAM/
├── backend/
│   ├── routes/
│   │   ├── mükellefler.js
│   │   ├── beyannameler.js
│   │   ├── eDefter.js
│   │   └── raporlar.js
│   ├── server.js
│   ├── package.json
│   └── .env.example
│
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── MükellefleriListesi.tsx
│   │   │   ├── BeyannamelerinYönetimi.tsx
│   │   │   ├── EDefterGönderileri.tsx
│   │   │   ├── Raporlar.tsx
│   │   │   └── Pages.css
│   │   ├── services/
│   │   │   └── api.ts
│   │   ├── App.tsx
│   │   ├── App.css
│   │   ├── index.tsx
│   │   └── index.css
│   ├── public/
│   │   └── index.html
│   ├── package.json
│   ├── tsconfig.json
│   └── .env.example
│
├── database/
│   └── migrations/
│       └── 001_initial_schema.sql
│
└── README.md
```

## 🎨 Arayüz Özellikleri

- **Modern Tasarım**: Temiz, profesyonel arayüz
- **Responsive Design**: Mobil, tablet, masaüstü uyumlu
- **Sidebar Navigation**: Kolay menü navigasyonu
- **Data Tables**: Organize edilmiş veri görünümü
- **Filter & Search**: Gelişmiş filtreleme ve arama
- **Status Badges**: Renk kodlu durum göstergeleri
- **Form Validation**: Girdi doğrulama

## 💡 Gelecek Özellikler

- [ ] Kullanıcı kimlik doğrulaması (Authentication)
- [ ] Rol ve yetki yönetimi (Authorization)
- [ ] Masaüstü uygulaması (Electron)
- [ ] PDF rapor dışa aktarma
- [ ] Excel entegrasyonu
- [ ] Bildirim sistemi
- [ ] Gelişmiş grafik raporlar
- [ ] Mobil uygulama (React Native)
- [ ] Veri backup ve recovery
- [ ] Kullanıcı aktivite logları

## ⚙️ Sistem Gereksinimleri

- **İşletim Sistemi**: Windows, macOS, Linux
- **RAM**: Minimum 4GB
- **Disk Alanı**: Minimum 500MB
- **Browser**: Chrome, Firefox, Safari, Edge (son sürümler)

## 🔒 Güvenlik

- CORS etkin
- Parametre doğrulama
- SQL injection koruması (parameterized queries)
- Error handling

## 📞 İletişim

**Geliştirici**: GÖKDEMİR Mali Müşavirlik Ofis

## 📄 Lisans

Bu proje özel kullanım için tasarlanmıştır.

---

**Son Güncelleme**: Nisan 2026
**Sürüm**: 1.0.0
