# Desktop Music Player
> Yerel müzik kütüphanesi, çalma listeleri ve kullanıcı hesapları sunan PyQt5 masaüstü müzik oynatıcı.

## Açıklama

Python ve PyQt5 ile geliştirilen masaüstü müzik çalar uygulaması. Belirlenen yerel müzik dizinini tarar; şarkıları, sanatçıları, oynatma listelerini ve dinleme geçmişini tek bir arayüz üzerinden yönetir. FastAPI tabanlı servis ise kayıt, giriş, e-posta doğrulama ve parola sıfırlama işlemlerini sağlar.

Müzik dosyaları sunucuya yüklenmez. Oynatma işlemleri doğrudan kullanıcının cihazındaki dosyalar üzerinden gerçekleştirilir.

## Özellikler

- Yerel dizin ve alt dizinlerde müzik dosyalarını otomatik tarama
- MP3, WAV ve OGG gibi yapılandırılabilir dosya uzantıları
- Tüm şarkılar, son eklenenler ve sanatçıya göre gruplama
- Beğenilen şarkılar, son oynatılanlar ve en çok dinlenenler
- Oynatma listesi oluşturma ve şarkı ekleme/çıkarma
- Karışık oynatma
- Kapalı, tek şarkı ve liste döngüsü modları
- Misafir kullanımı
- Kayıt, giriş ve beni hatırla desteği
- E-posta doğrulama ve parola sıfırlama
- Açık ve koyu tema

## Kurulum

Proje Python 3.10 ile çalışacak şekilde hazırlanmıştır.

Gerekli yazılımlar:

- Python 3.10 veya üzeri
- Docker ve Docker Compose

> 💡 **Not:** Docker ve Docker Compose yalnızca backend'i çalıştırmak için gereklidir.

> 💡 **Not:** Backend çalıştırılmadan da uygulama misafir olarak kullanılabilir.

Projeyi klonlayın:

```bash
git clone https://github.com/seymenkonuk/desktop-music-player.git
cd desktop-music-player
```

## Yapılandırma

### Masaüstü Uygulaması

Örnek yapılandırma dosyasını kopyalayın:

```bash
cp frontends/desktop-app/env/.env.example frontends/desktop-app/env/.env
```

`frontends/desktop-app/env/.env` dosyasını düzenleyin:

```env
API_BASE_URL="http://localhost:8000"

MUSIC_ROOT_PATH="/home/kullanici/Music"
MUSIC_FILE_EXTENSIONS=".mp3;.wav;.ogg"

THEME="dark"
```

- `MUSIC_ROOT_PATH`: Taranacak ana müzik dizini
- `MUSIC_FILE_EXTENSIONS`: Noktalı virgülle ayrılmış dosya uzantıları
- `THEME`: `light` veya `dark`

> 💡 **Not:** Desteklenen ses dosyası biçimleri, işletim sisteminizdeki Qt Multimedia codec desteğine bağlıdır. Bu nedenle bazı dosya biçimleri bir platformda çalışırken başka bir platformda desteklenmeyebilir.

### Backend

Örnek yapılandırma dosyasını kopyalayın:

```bash
cp backends/client-api/env/.env.example backends/client-api/env/.env
```

Kayıt doğrulama ve parola sıfırlama e-postaları için `backends/client-api/env/.env` dosyasını düzenleyin:

```env
EMAIL="example@example.com"
PASSWORD="example-password"
DISPLAY_NAME="Music Player"
SMTP_HOST="smtp.example.com"
SMTP_PORT="587"
```

## Müzik Dosyalarının Adlandırılması

Sanatçıya göre gruplama, dosya adı üzerinden yapılır. Önerilen adlandırma biçimi:

```text
Sanatçı Adı - Şarkı Adı.mp3
```

> 💡 **Not:** Dosya adında `-` ayıracı bulunmazsa sanatçı adı `Bilinmeyen Sanatçı` olarak gösterilir.

## Çalıştırma

Backend servisini çalıştırmak için:

```bash
cd backends/client-api
docker compose up -d
```

Masaüstü uygulamasını çalıştırmak için:

```bash
python frontends/desktop-app/main.py
```

> 💡 **Not:** Backend çalıştırılmadan uygulama misafir olarak kullanılabilir; kayıt ve giriş işlemleri kullanılamaz.

Backend servisini durdurmak için:

```bash
cd backends/client-api
docker compose down
```

## Galeri

### Fotoğraflar

| ![Açık Tema](docs/images/0.png) | ![Koyu Tema](docs/images/1.png) |
|---------------------------------|---------------------------------|

### Demo

https://github.com/user-attachments/assets/cdc8cc91-1753-4b2b-9fbb-d580bb72f57b

### Kayıt ve Giriş Sistemi

https://github.com/user-attachments/assets/023b9493-3673-431f-b055-5e5652faabca

## Atıflar

Projede kullanılan ikonlar [Freepik](https://www.freepik.com) tarafından tasarlanmıştır.

## Lisans

Bu proje [MIT Lisansı](https://github.com/seymenkonuk/desktop-music-player/blob/main/LICENSE) ile lisanslanmıştır.
