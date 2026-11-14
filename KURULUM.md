# Kurulum Kılavuzu — Göreme Cave Suites Web Sitesi

Bu klasör hazır, statik bir web sitesidir. **Veritabanı, PHP, WordPress veya özel bir
sunucu gerekmez.** Klasörün içindeki her şey (gizli `.htaccess` dosyası dahil) sunucuya
olduğu gibi yüklenir. Online rezervasyon, otelin mevcut **Reseliva** sayfası üzerinden
çalışmaya devam eder; sitede ayrıca rezervasyon sistemi kurmanız gerekmez.

---

## 1. Hangi yolu seçmeliyim?

| Yol | Kimler için | Ücret | Güvenlik başlıkları |
| --- | --- | --- | --- |
| **A. Mevcut hosting (cPanel / FTP)** | Alan adı ve hosting zaten varsa | Mevcut paket | `.htaccess` ile tam |
| **B. Cloudflare Pages veya Netlify** | Hosting yoksa ya da yenilemek isteniyorsa | Ücretsiz | `_headers` ile tam |
| **C. GitHub Pages** (şu anki önizleme) | Geçici yayın / önizleme | Ücretsiz | Kısmi (sayfa içi politika) |

Önerimiz: Hosting yenilenecekse **B (Cloudflare Pages)**: ücretsiz, hızlı, otomatik
HTTPS ve DDoS koruması. Mevcut hosting korunacaksa **A** da tamamen uygundur.

---

## A. Mevcut hosting'e yükleme (cPanel / FTP)

1. **Eski sitenin yedeğini alın** (cPanel → Yedekleme veya `public_html` klasörünü indirin).
2. `public_html` içindeki eski site dosyalarını bir alt klasöre taşıyın (ör. `eski-site/`).
3. Bu klasörün **tüm içeriğini** `public_html` içine yükleyin. Gizli `.htaccess` dosyası
   da yüklenmeli (FileZilla: *Sunucu → Gizli dosyaları göstermeye zorla*).
4. cPanel → **SSL/TLS Status** → AutoSSL ile ücretsiz sertifikayı açın. `.htaccess`
   tüm ziyaretçileri otomatik olarak `https://` adresine yönlendirir.
5. Tarayıcıda `https://alanadiniz.com` adresini açıp kontrol edin.

## B. Cloudflare Pages (veya Netlify)

1. [pages.cloudflare.com](https://pages.cloudflare.com) → *Create project → Direct upload*.
   Bu klasörü sürükleyip bırakın. (Netlify: [app.netlify.com/drop](https://app.netlify.com/drop))
2. *Custom domains* → `goremecavesuites.com` ve `www.goremecavesuites.com` ekleyin.
3. Ekranda gösterilen DNS kayıtlarını alan adının yönetim panelinde tanımlayın
   (alan adı Cloudflare'e taşınırsa bu adım otomatik olur).
4. HTTPS sertifikası birkaç dakika içinde kendiliğinden gelir.

## C. GitHub Pages'te özel alan adı

1. Depo → *Settings → Pages → Custom domain*: `www.goremecavesuites.com`.
2. DNS: `www` için **CNAME** → `serdarkafali.github.io`; kök alan adı için **A** kayıtları
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
3. *Enforce HTTPS* kutusunu işaretleyin.

---

## 2. Alan adı belli olunca güncellenecekler

Site şu an önizleme adresine göre ayarlı. Aşağıdaki dosyalarda
`https://serdarkafali.github.io/goreme-cave-suites/` metnini yeni adresle
(ör. `https://www.goremecavesuites.com/`) **bul-değiştir** yapın:

- `index.html` (paylaşım önizlemesi, Google bilgileri ve `MENU_QR_LINK`)
- `robots.txt`, `sitemap.xml`

Ardından `img/menu-qr.svg` QR kodunu yeni adrese göre yeniden üretin (masalarda
kullanılacaksa basmadan önce telefonla okutup test edin).

**Dikkat:** Eski sitedeki `.../privacy-policy` sayfası yeni sitede yoktur. Gizlilik ve KVKK
metinleri gelince bunları sitenin içine ekleyelim (`PRIVACY_URL`, `KVKK_URL`).

---

## 3. İçerik düzenleme

- Tüm metin, telefon, adres, saat, sosyal medya ve rezervasyon bağlantıları `index.html`
  dosyasının başındaki **`SITE_CONFIG`** bölümündedir. `[YER TUTUCU]` yazan değerler
  gerçek bilgilerle değiştirilmelidir.
- Fotoğraf değiştirmek için aynı isimle `img/foto/` klasörüne yeni dosyayı koyun
  (WebP önerilir, genişlik en fazla 1600 px).
- Tasarım dosyası `css/site.css` derlenmiş durumdadır. Sitede **daha önce kullanılmamış**
  bir Tailwind sınıfı eklenirse yeniden derlenmesi gerekir (geliştiriciye iletin).

---

## 4. Güvenlik notları

- Site statiktir: sunucuda çalışan kod, veritabanı veya yönetici girişi yoktur; bu yüzden
  WordPress tarzı saldırı yüzeyi bulunmaz.
- Tüm fotoğraf, yazı tipi ve tasarım dosyaları sitenin kendi sunucusundan gelir; yalnızca
  Google Haritalar ve Reseliva rezervasyon sayfası dış adreslerdir.
- `Content-Security-Policy`, HSTS, `X-Frame-Options`, `nosniff`, `Referrer-Policy` ve
  `Permissions-Policy` başlıkları `.htaccess` ve `_headers` içinde hazırdır.
- Yayından sonra [securityheaders.com](https://securityheaders.com) ve
  [pagespeed.web.dev](https://pagespeed.web.dev) ile kontrol önerilir.

## 5. Yayından sonra (önerilir)

- **Google Search Console**: siteyi ekleyin, `sitemap.xml` gönderin.
- **Google İşletme Profili**: otelin haritada adıyla ve doğru konumda göründüğünü kontrol edin.
- Rezervasyon butonlarının Reseliva'da doğru otele gittiğini bir test rezervasyonuyla deneyin.
