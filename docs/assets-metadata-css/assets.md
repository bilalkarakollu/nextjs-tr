---
sidebar_position: 1
---

# Varlıklar

Next.js , üst düzey dizin altında resimler gibi statik varlıklar sunabilir. `public` İçindeki dosyalara benzer uygulamanın kökünden referans alınabilir.

### Profil Resminizi İndirin

İlk önce profil resminizi alalım.

- Profil resminizi .jpg formatta indirin (veya <a href="https://github.com/vercel/next-learn/blob/master/basics/basics-final/public/images/profile.jpg">bu dosyayı kullanın</a>).
- `public` dizinin içinde `images` dizini oluşturun.
- Resimi `profile.jpg` isminde `public/images` dizinin içinde kaydedin.
- Görüntü boyutu yaklaşık 400 piksele 400 piksel olabilir.


### Optimize Edilmemiş Resim

Normal HTML ile profil resminizi aşağıdaki gibi eklersiniz:

```js
<img src="/images/profile.jpg" alt="Your Name" />
```

Ancak bu, manuel olarak işlemeniz gerektiği anlamına gelir:

- Resminizin farklı ekran boyutlarında duyarlı olmasını sağlamak
- Üçüncü taraf bir araç veya kitaplıkla resimlerinizi optimize etme
- Görüntüler yalnızca görünüm alanına girdiklerinde yükleniyor
  
Ve dahası. Bunun yerine, Next.js, `Image` bunu sizin için halletmek için kutudan çıkarılmış bir bileşen sağlar.


### Görüntü Bileşeni ve Görüntü Optimizasyonu

`next/image` modern web için geliştirilmiş `<img>` HTML öğesinin bir uzantısıdır.

Next.js ayrıca varsayılan olarak Görüntü Optimizasyonu desteğine sahiptir. Bu , tarayıcı desteklediğinde, görüntüleri WebP gibi modern biçimlerde yeniden boyutlandırmaya, optimize etmeye ve sunmaya olanak tanır . Bu, büyük görüntülerin daha küçük bir görünüme sahip cihazlara gönderilmesini önler. Ayrıca Next.js'nin gelecekteki görüntü biçimlerini otomatik olarak benimsemesine ve bunları bu biçimleri destekleyen tarayıcılara sunmasına olanak tanır.

Otomatik Görüntü Optimizasyonu, herhangi bir görüntü kaynağıyla çalışır. Görüntü, CMS gibi harici bir veri kaynağında barındırılsa bile optimize edilebilir.


### Görüntü Bileşenini Kullanma


Next.js, görselleri derleme sırasında optimize etmek yerine, görselleri talep üzerine, kullanıcıların istediği şekilde optimize eder. Statik site oluşturucuların ve yalnızca statik çözümlerin aksine, ister 10 görüntü ister 10 milyon görüntü gönderin, oluşturma süreniz artmaz.

Görüntüler varsayılan olarak tembel yüklenir. Bu, görünüm alanının dışındaki görüntüler için sayfa hızınızın cezalandırılmadığı anlamına gelir. Görüntüler, görünüm alanına kaydırıldıkça yüklenir.

Görüntüler her zaman, Google'ın arama sıralamasında kullanacağı bir <a href="https://web.dev/vitals/#core-web-vitals">Önemli Web Verisi</a> olan <a href="https://web.dev/cls/">Kümülatif Düzen Kayması(CLS)</a>'ndan kaçınacak şekilde oluşturulur.

İşte `next/image` profil resmimizi görüntülemek için kullanılan bir örnek. Sahne öğeleri `height`, `width` kaynak görüntüyle aynı en boy oranıyla istenen oluşturma boyutunda olmalıdır.

```js
import Image from 'next/image';

const YourComponent = () => (
  <Image
    src="/images/profile.jpg" // Route of the image file
    height={144} // Desired size with correct aspect ratio
    width={144} // Desired size with correct aspect ratio
    alt="Your Name"
  />
);
```


