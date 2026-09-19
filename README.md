# ☠ NO RESPECT BOT

NO RESPECT sunucusunu kurar; renk rolü butonlarını, özel destek taleplerini ve karşılama sistemini sürekli çalıştırır. Railway üzerinde ayrı bir bot olarak 7/24 kullanılabilir.

## v3 özellikleri

- Giriş/çıkış, davet eden kişi ve şüpheli yeni hesap logları
- Silinen/düzenlenen mesaj, rol, ses ve moderasyon logları
- Renk, kimlik, yaş, ilgi alanı, oyun ve bildirim rol panelleri
- Ticket oluşturma, üstlenme, kullanıcı ekleme/çıkarma ve kapanış konuşma kaydı
- Moderasyon komutları: uyarı, susturma, atma, yasaklama, temizleme ve kanal kilidi
- XP, seviye ödülleri, profil ve sıralama
- Spam, Discord davet bağlantısı, yeni hesap ve anti-nuke koruması
- Otomatik açılıp boşalınca silinen kişisel ses odaları

## Uyarı

`/kur` komutunu onayladığında çalıştırıldığı sunucudaki mevcut kanallar ve botun silebildiği roller kalıcı olarak silinir. Bot rolleri ve Discord entegrasyon rolleri silinemez.

## Kurulum

1. Bilgisayarında Node.js 20 veya daha yenisi kurulu olsun.
2. Discord Developer Portal'da yeni bir uygulama ve bot oluştur.
3. Bot ayarlarında **Server Members Intent** ve **Message Content Intent** seçeneklerini aç.
4. Botu sunucuya `Administrator` yetkisiyle ekle.
5. Sunucu Ayarları → Roller bölümünde kurucu botun rolünü, silinecek diğer bütün normal rollerin üstüne taşı. Discord'un yönettiği entegrasyon/bot rolleri silinmez.
6. `.env.example` dosyasını `.env` olarak yeniden adlandır.
7. `TOKEN`, `CLIENT_ID` ve `GUILD_ID` bilgilerini doldur.
8. Bu klasörde terminal açıp şunları çalıştır:

```bash
npm install
npm start
```

9. Sunucuda `/kur` yaz ve kırmızı onay düğmesine bas.

## Kurulan düzen

- Karşılama ve bilgi odaları
- Genel sohbet ve medya odaları
- Oyun ve ekip bulma odaları
- Müzik odaları
- AFK ve özel ses odaları
- Yetkiliye özel kategori, kayıt ve log odaları
- Kurucu, yönetim, moderasyon, üye ve renk rolleri

Kurulum bitince botu sunucudan çıkarma; rol, ticket ve karşılama sistemleri için Railway'de açık kalmalıdır.

## Railway'e yükleme

1. ZIP'i çıkart ve klasörü GitHub'da yeni, tercihen private bir repoya yükle. `.env` dosyasını GitHub'a yükleme.
2. Railway'de **New Project → Deploy from GitHub Repo** seç ve repoyu bağla.
3. Railway projesinde **Variables** bölümüne şunları ekle:

```env
TOKEN=Discord_Bot_Token
CLIENT_ID=Discord_Application_ID
GUILD_ID=Discord_Sunucu_ID
SETUP_ENABLED=true
INVITE_FILTER=true
SPAM_FILTER=true
ANTI_NUKE=true
```

4. Deploy tamamlanınca Railway loglarında botun aktif olduğu ve `/kur` komutunun yüklendiği görünür.
5. Sunucuyu kurmak için Discord'da `/kur` kullan.
6. Kurulum tamamlanınca yanlışlıkla sunucuyu tekrar sıfırlamamak için Railway Variables bölümünde `SETUP_ENABLED=false` yap. Railway yeniden deploy eder; rol ve ticket sistemleri çalışmaya devam eder fakat `/kur` kilitlenir.

Railway'de ayrıca bir port veya domain tanımlaman gerekmez; bu proje web sitesi değil, sürekli çalışan Discord worker botudur.

### Kalıcı XP ve uyarılar

Railway projesine **New → Database → PostgreSQL** ile bir veritabanı ekle. `DATABASE_URL` otomatik oluşur. PostgreSQL eklenmezse bot yine çalışır fakat XP ve uyarılar yeniden başlatmada sıfırlanır.
