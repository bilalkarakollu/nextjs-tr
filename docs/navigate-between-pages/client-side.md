---
sidebar_position: 4
---

# İstemci Tarafı Gezinme

`Link` Bileşeni, aynı Next.js uygulamasındaki iki sayfa arasında istemci tarafında gezinmeyi sağlar.

İstemci tarafında gezinme, sayfa geçişinin, tarayıcı tarafından yapılan varsayılan gezinmeden daha hızlı olan JavaScript kullanılarak gerçekleştiği anlamına gelir.

Bunu doğrulamanın basit bir yolu:

- `<html>` background CSS özelliğini tarayıcının geliştirici araçlarını kullanarak olarak `yellow` değiştirin.
- İki sayfa arasında ileri geri gitmek için bağlantılara tıklayın.
- Sayfa geçişleri arasında sarı arka planın devam ettiğini göreceksiniz.

Bu, tarayıcının tam sayfayı yüklemediğini ve istemci tarafında gezinmenin çalıştığını gösterir.

<img src="https://nextjs.org/static/images/learn/navigate-between-pages/client-side.gif"/>

### Kod bölme ve önceden getirme

Next.js otomatik olarak kod bölme yapar, böylece her sayfa yalnızca o sayfa için gerekli olanı yükler. Bu, ana sayfa oluşturulduğunda, diğer sayfaların kodunun başlangıçta sunulmadığı anlamına gelir.

Bu, yüzlerce sayfanız olsa bile ana sayfanın hızlı bir şekilde yüklenmesini sağlar.

Yalnızca istediğiniz sayfanın kodunu yüklemek, sayfaların izole olması anlamına da gelir. Belirli bir sayfa hata verirse, uygulamanın geri kalanı çalışmaya devam eder.

Ayrıca, Next.js'nin üretim yapısında, `Link` bileşenler tarayıcının görünüm alanında göründüğünde, Next.js arka planda bağlantılı sayfanın kodunu otomatik olarak önceden getirir. Bağlantıyı tıkladığınızda, hedef sayfanın kodu arka planda zaten yüklenmiş olacak ve sayfa geçişi neredeyse anında gerçekleşecek!

### Özet

Next.js, kod bölme, istemci tarafında gezinme ve önceden getirme (üretimde) yoluyla uygulamanızı en iyi performans için otomatik olarak optimize eder.

`pages` altında dosyalar olarak rotalar oluşturursunuz ve yerleşik `Link` bileşeni kullanırsınız. Yönlendirme kitaplıkları gerekmez.