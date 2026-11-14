# Göreme Cave Suites — Web Sitesi

Göreme Cave Suites otelinin web sitesi (v5). Statik bir sitedir: veritabanı, PHP veya
yönetim paneli gerekmez; klasörün tamamı herhangi bir hosting'e yüklenerek çalışır.
Kurulum ve alan adı bağlama adımları: **[KURULUM.md](KURULUM.md)**.

| Dosya / klasör | İçerik |
| --- | --- |
| `index.html` | Sitenin tamamı (Ana sayfa, Odalar, Restoran, Hamam) ve tüm ayarlar (`SITE_CONFIG`) |
| `css/site.css` | Derlenmiş tasarım dosyası (Tailwind) |
| `fonts/` | Yazı tipleri (Playfair Display, Montserrat) |
| `img/foto/` | Otel, oda, hamam ve aktivite fotoğrafları |
| `img/menu/` | 37 yemek fotoğrafı (büyük + kare küçük resim) |
| `video/` | Ana sayfa ve restoran giriş videoları (yatay 1920x1080 + dikey 1080x1920) ve kapak görselleri |
| `404.html` | "Sayfa bulunamadı" sayfası |
| `_headers`, `.htaccess` | Güvenlik ve önbellek ayarları (Netlify/Cloudflare ve cPanel için) |
| `robots.txt`, `sitemap.xml`, `site.webmanifest` | Arama motorları ve telefon ana ekranı için |

## Video kaynakları

Videolar, ticari kullanıma ücretsiz açık stok çekimlerden kurgulanmıştır
([Pexels Lisansı](https://www.pexels.com/license/), [Pixabay İçerik Lisansı](https://pixabay.com/service/license-summary/));
atıf zorunlu değildir, yine de footer'daki "Görsel kaynakları" listesinde belirtilir.
Yemek sahneleri temsilidir (köz, mangal, kebap); otelin kendi mutfağında çekilecek
bir videoyla `video/` klasöründeki dosyalar aynı adla değiştirilebilir.

Yerelde görmek için klasörde `python -m http.server` çalıştırıp `http://localhost:8000`
adresini açın (dosyaya çift tıklamak videolar ve yazı tipleri için yeterli olmayabilir).
