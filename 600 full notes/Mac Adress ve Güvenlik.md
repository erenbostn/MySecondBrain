- **Class:**  
- **Date:** 2026-04-05  
- **Topics:** #hack #mac 
- Connects: [[Kali Linux]]

🤖[[610 chatcpt-note/_index|ChatGpt Notes Page]] || 🏠 [[Home Page]] || 📝 [[600 full notes/_index|Full Notes Page]] ||👨‍💻 [[620 programming language/_index|Programming Language Page]] 

## MAC Adresi ve Ağ Güvenliği Notları

### MAC Adresi Nedir?

- **Tanım:** Media Access Control. Bir cihazın ağ kartına üretici tarafından atanan, donanımsal ve (genelde) sabit "parmak izidir".
    
- **Yapısı:** 48 bitlik bir yapıya sahiptir. 6 grup onaltılık (hexadecimal) sayıdan oluşur (Örn: 00:1A:2B...).
    
- **Kapasite:** Matematiksel olarak yaklaşık **281 trilyon** farklı kombinasyon üretilebilir.
    
- **OUI ve Seri No:** İlk 3 grup üretici firmayı (Apple, Intel vb.) temsil eder, son 3 grup cihaza özel seri numarasıdır. Adreslerin tükenme ihtimali yoktur.
    

---

### MAC Adresi Ne İşe Yarar? (Kullanım Alanları)

- **Ağ Yönetimi:** Cihazlara statik IP atamak, veri tüketimini izlemek ve bant genişliğini sınırlandırmak için kullanılır.
    
- **Güvenlik (MAC Filtreleme):** Modemlerde sadece belirli MAC adreslerine izin verilebilir (Beyaz Liste) veya belirli adresler engellenebilir (Kara Liste).
    
- **Konum Belirleme:** Apple, Google gibi şirketlerin Wi-Fi veritabanları sayesinde GPS olmadan cihaz konumu tespit edilebilir.
    
- **Wake-on-LAN (WoL):** "Magic Packet" gönderilerek kapalı bir bilgisayarı uzaktan çalıştırmaya yarar.
    

---

### MAC Adresinin İfşa Olması (Örn: Videoda Görünmesi) Ne Kadar Riskli?

Tek başına MAC adresi ifşası bir cihazı hacklemek için yeterli değildir (kredi kartı sızması gibi acil bir kriz yaratmaz) ancak şu riskleri doğurur:

- **MAC Spoofing (Kimlik Taklidi):** Saldırgan, kendi MAC adresini sızan adresle değiştirerek ağ filtrelerini aşabilir ve kurbanın yetkileriyle internete bağlanabilir.
    
- **Hedefli Takip:** Halka açık ağlarda cihazın hangi ağlara bağlandığı takip edilerek profil oluşturulabilir.
    
- **Kurumsal Riskler:** VPN veya iç ağ doğrulamasında MAC adresi kullanılıyorsa, saldırgana bir açık kapı sunar.
    

---

### Konum + MAC Adresi Neden Tehlikeli Bir Kombinasyondur?

MAC adresi cihazın "kim" olduğunu, konum ise "nerede" olduğunu söyler. Bu iki bilginin birleşmesi asıl tehlikeyi yaratır.

- **Anahtar ve Kapı Mantığı:** MAC adresi bir anahtardır. Saldırgan konumu bilirse, bu anahtarı hangi kapıda (modemde) deneyeceğini bulmuş olur.
    
- **Yerel Ağ Saldırıları:** Saldırgan kurbanın konumuna fiziksel olarak yaklaşır, MAC Spoofing ile aynı ağa sızar ve "Man-in-the-Middle" (Aradaki Adam) saldırısı ile şifrelenmemiş verileri, girilen siteleri izleyebilir.
    
- **Rutin Takibi:** Wigle gibi küresel Wi-Fi veritabanları sayesinde, belirli bir MAC adresinin hangi konumda, hangi saatlerde bulunduğu analiz edilerek fiziksel bir takip haritası çıkarılabilir.
    

---

### Wi-Fi Otomatik Bağlanma ve Güvenlik Açığı

- Cihaz bir ağa ilk bağlandığında **SSID (İsim)** ve **Şifreyi** kaydeder.
    
- Şifre doğrulandıktan sonra modem, cihazın **MAC Adresini** "tanıdık cihazlar" tablosuna ekler ve IP ataması yapar.
    
- Yurt, otel veya kampüs gibi bazı ağlar, şifre girdikten sonra cihazı sadece MAC adresinden tanıyarak haftalarca şifresiz giriş izni verir.
    
- **Risk:** Saldırgan, kurbanın MAC adresini taklit (Spoofing) ettiğinde, modem kurbanın cihazı geldi sanarak saldırgana **şifre sormadan** ağa erişim verebilir.
    

---

### MAC Adresini Değiştirmek Mümkün mü?

Evet, mümkündür ve cihazı bozmaz. Çünkü yapılan işlem donanımsal değil, yazılımsaldır.

- **Gerçek MAC (BIA - Burned-In Address):** Fabrika çıkışlı, çipe kazınmış adrestir. Değişmez.
    
- **Yazılımsal MAC (Spoofing/Randomization):** İşletim sisteminin ağa sunduğu "maske" adrestir. Ayar sıfırlandığında cihaz orijinal MAC adresine geri döner.
    
- **Özel/Rastgele Wi-Fi Adresi:** Modern iOS ve Android cihazlar, izlenmeyi zorlaştırmak için her Wi-Fi ağına farklı bir sanal MAC adresi ile bağlanma (Random MAC) özelliğine sahiptir.
    

> **Özet Not:** MAC adresi cihazın dijital yüzüdür. Sabit kalması durumunda takip edilmeyi kolaylaştırır. Modern güvenlik için halka açık veya güvenilmeyen ağlarda cihazların "Rastgele MAC" (Private Address) özelliğinin açık tutulması kritik bir savunma yöntemidir.



🤖[[610 chatcpt-note/_index|ChatGpt Notes Page]] || 🏠 [[Home Page]] || 📝 [[600 full notes/_index|Full Notes Page]] ||👨‍💻 [[620 programming language/_index|Programming Language Page]] 