# Ben Kimim · Dijital Kartvizit

> Basılı kartvizitlerin yerini alan, tek linkte tüm iletişim bilgilerini paylaşabileceğin sunucusuz dijital kartvizit uygulaması.

<p>
  <img alt="HTML" src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white">
  <img alt="CSS" src="https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white">
  <img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black">
  <img alt="Backend yok" src="https://img.shields.io/badge/Backend-Yok-success">
  <img alt="Bağımlılık" src="https://img.shields.io/badge/Bağımlılık-Tek%20dosya-blue">
</p>

🔗 **Canlı demo:** [whoami.cnklc.me](https://whoami.cnklc.me)

---

## 📌 Proje Hakkında

**Ben Kimim**, klasik basılı kartvizitlerin yerini almak için geliştirdiğim bir web uygulaması. Kişi formu doldurur; uygulama ona özel bir bağlantı ve QR kod üretir. Bu QR'ı okutan herkes; e-posta, telefon, WhatsApp, Instagram, LinkedIn ve dilediği diğer bağlantılara tek sayfadan ulaşır.

Proje kendi ihtiyacımdan doğdu: tanıştığım kişilere bilgilerimi tek tek yazmak yerine, telefonumdaki QR'ı okutarak saniyeler içinde tüm iletişim kanallarımı paylaşabilmek istedim. Aynı ihtiyacı duyan herkesin de kullanabilmesi için **çok kullanıcılı** ve **hesap gerektirmeyen** bir yapıda tasarladım.

## ✨ Özellikler

- **Hesapsız kullanım** — Kayıt yok, giriş yok. Formu doldur, linkin hazır.
- **Sınırsız ve özel bağlantı** — E-posta, telefon, WhatsApp, Instagram, LinkedIn, web sitesi, GitHub, X ve kullanıcının kendi tanımladığı özel linkler.
- **QR kod** — Her kartvizit için otomatik üretilen, okutulduğunda sayfayı açan QR.
- **Kişilere kaydet (vCard)** — Tek tıkla `.vcf` dosyası indirip telefon rehberine ekleme.
- **Yerel paylaşım** — Native paylaşım menüsü ve "linki kopyala" desteği.
- **Tema seçenekleri** — 8 farklı vurgu rengiyle kişiselleştirme.
- **Mobil öncelikli, responsive** — Her ekran boyutunda akıcı çalışır.
- **Gizlilik dostu** — Hiçbir veri sunucuda saklanmaz (aşağıya bakın).

## 🧠 Nasıl Çalışıyor? (Mimari)

Projenin en kritik tasarım kararı: **backend ve veritabanı kullanmamak.**

Kullanıcı formu doldurduğunda tüm bilgiler bir JSON nesnesine dönüştürülür, UTF-8 güvenli biçimde **Base64 (URL-uyumlu)** olarak kodlanır ve doğrudan bağlantının içine (`#c=...`) gömülür:

```
https://whoami.cnklc.me/#c=eyJuIjoiQ2FuIiwidCI6Ii4uLiJ9
```

Sayfa açıldığında bu veri çözülür ve kartvizit istemci tarafında oluşturulur. Bu yaklaşımın getirdikleri:

- **Sıfır altyapı maliyeti** — Statik dosya barındırmadan (GitHub Pages) fazlası gerekmez.
- **Gizlilik** — Kişisel veriler hiçbir sunucuya gönderilmez; tamamen kullanıcının linkinde durur.
- **Anında ölçeklenir** — Kullanıcı sayısı arttıkça değişen bir sunucu yükü yoktur.
- **Kalıcılık** — Link çalıştığı sürece kartvizit yaşar; ayrı bir servise bağımlı değildir.

## 🛠️ Teknolojiler

| Katman | Kullanılan |
|--------|------------|
| Arayüz | Saf HTML, CSS (custom properties ile tema), Vanilla JavaScript |
| QR üretimi | [qrcodejs](https://github.com/davidshimjs/qrcodejs) |
| Veri kodlama | `TextEncoder` + Base64 (URL-safe) |
| Kişi kartı | vCard 3.0 (`.vcf`) |
| Barındırma | GitHub Pages + özel alan adı |

> Tüm uygulama **tek bir `index.html` dosyasında**, harici bir derleme adımı veya çatı (framework) olmadan çalışır.

## 🚀 Yerel Çalıştırma

Herhangi bir kurulum gerektirmez:

```bash
git clone https://github.com/KULLANICI/whoami.git
cd whoami
# index.html dosyasını tarayıcıda açmanız yeterli
open index.html
```

## 🌐 Yayınlama (GitHub Pages)

1. Depoyu GitHub'a push et.
2. **Settings → Pages** → Source: `main` / root.
3. `CNAME` dosyası özel alan adını (`whoami.cnklc.me`) otomatik tanımlar.
4. Alan adı sağlayıcında bir **CNAME kaydı** ekle: `whoami → KULLANICI.github.io`.
5. DNS yayıldıktan sonra **Enforce HTTPS**'i aç.

## 🗺️ Yol Haritası

- [ ] Kısa, okunabilir linkler (`whoami.cnklc.me/can`)
- [ ] Hesap sistemi ve tıklanma istatistikleri (opsiyonel backend)
- [ ] Ek tasarım temaları ve kart şablonları
- [ ] Apple Wallet / Google Wallet kartı olarak ekleme
- [ ] Çoklu dil desteği (TR / EN)

## 👤 Geliştirici

**Can Köklüçınar**
Bu proje kişisel bir ihtiyaçtan doğdu ve aynı ihtiyacı duyan herkesin kullanabilmesi için açık biçimde geliştiriliyor.

---

<sub>Katkı ve geri bildirimler memnuniyetle karşılanır. Bir sorun bulursan issue açabilir, fikir önerebilirsin.</sub>
