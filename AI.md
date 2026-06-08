# 🤖 Yapay Zeka (AI) Prompt ve Yanıt Log Kayıtları

Bu projede yapay zeka (Google Gemini), mimari kararlar almak, kod hatalarını ayıklamak ve sektör standartlarına uygun geliştirme yapmak için bir danışman olarak kullanılmıştır. Aşağıda projeyi geliştirirken AI'a sorulan temel promptlar ve alınan yanıtların/çözümlerin özetleri listelenmiştir.

GÖREV 1: Veritabanı Veri Bütünlüğü
Prompt: Araç ekleme formundaki yakıt, vites gibi seçenekleri veritabanı seviyesinde nasıl kısıtlayabilirim? Kullanıcıların yanlış veri girmesini istemiyorum, ENUM kullansam nasıl bir SQL yazmam gerekir?

Cevap: Veri bütünlüğü için ENUM kullanımı doğru bir tercihtir. Mevcut veritabanı yapını değiştirmek için ALTER TABLE komutunu kullanmalısın. Sana araç durumu, yakıt tipi ve vites türlerini sınırlandıran SQL sorgusunu hazırladım. Bu sayede veritabanı, tanımladığın seçenekler dışındaki veriyi reddedecektir.

GÖREV 2: Veri Tipleri Kararı
Prompt: Kullanıcılar tablosuna telefon numarası ekleyeceğim. Rakamlardan oluştuğu için veri tipini INT (Integer) olarak mı ayarlamalıyım?

Cevap: Bu yaklaşım hatalı olur. Telefon numaralarıyla matematiksel işlem yapmayacaksın. Ayrıca INT veri tipi numaraların başındaki sıfır rakamını siler ve kapasite olarak yetersiz kalabilir. En güvenli ve standart yol, numarayı VARCHAR(11) tipinde tutmandır. Bu sayede hem başındaki sıfırı korursun hem de veri kaybı yaşamazsın.

GÖREV 3: İlişkisel Veritabanı (Şehirler)
Prompt: Kullanıcılara ve araçlara 81 ili eklemek istiyorum. Bunu her iki tabloya da (users ve vehicles) ayrı ayrı ENUM olarak yazıp 81 ili kopyalayayım mı?

Cevap: Bu yöntemi kullanırsan veritabanında gereksiz veri tekrarı oluşur. Bunun yerine şehirleri tek bir 'cities' tablosunda tutmalısın. Kullanıcılar ve araçlar tablolarına sadece bu şehirlerin ID'sini tutan bir 'city_id' alanı ekleyip bu iki tabloyu birbirine Foreign Key ile bağlaman daha profesyonel ve esnek bir mimari olacaktır.

GÖREV 4: Kod Tekrarını Önleme
Prompt: Tüm sayfalara aynı navigasyon (navbar) HTML kodunu kopyalayıp yapıştırıyorum. Bunu düzeltmenin daha kolay bir yolu var mı?

Cevap: Her sayfaya aynı kodu kopyalamak spagetti kod üretir ve yönetimini imkansız hale getirir. Bunun yerine 'navbar.php' adında bir dosya oluşturup ortak menü kodunu oraya almalısın. Ardından diğer sayfalarda PHP'nin 'include' fonksiyonunu kullanarak bu dosyayı çağırmalısın. Ayrıca hangi sayfada olduğunu belirlemek için '$_SERVER['PHP_SELF']'  komutunu kullanarak aktif linki vurgulayan dinamik bir yapı kurabilirsin.

GÖREV 5: Güvenlik ve Şifre Yönetimi
Prompt: Profil ekranına şifre değiştirme bölümü ekledim. Güvenlik için kullanıcıdan eski şifresini istemem ve doğrulamam gerekiyor. Bunu nasıl kurgularım?

Cevap: Bu çok yerinde bir güvenlik refleksi. Veritabanında şifreleri zaten password_hash() ile kriptolayarak tutuyoruz. Şifre doğrulama işlemi için de PHP'nin 'password_verify()' fonksiyonunu kullanmalısın. Kullanıcının girdiği mevcut şifreyi, veritabanındaki hash ile karşılaştırıp eşleşirse yeni şifreyi kaydetmen en güvenli yöntemdir.
