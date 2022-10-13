---
sidebar_position: 9
---

# Render nedir?

React'te yazdığınız kodu, kullanıcı arayüzünüzün HTML temsiline dönüştürmek için kaçınılmaz bir iş birimi vardır. Bu işleme `render` denir.

Oluşturma, sunucuda veya istemcide gerçekleşebilir. Derleme zamanında önceden veya çalışma zamanında her istekte olabilir.

Next.js ile üç tür işleme yöntemi mevcuttur: Sunucu Tarafı İşleme(Server-Side ), Statik Site(Static Site) Oluşturma ve İstemci Tarafı(Client-Side) İşleme.

### Ön İşleme (Pre-Rendering)

Sunucu Tarafı Oluşturma ve Statik Site Oluşturma, harici verilerin alınması ve React bileşenlerinin HTML'ye dönüştürülmesi, sonuç istemciye gönderilmeden önce gerçekleştiğinden, Ön Oluşturma(Pre-rendering) olarak da adlandırılır.

### İstemci Tarafı Oluşturma ve Ön Oluşturma(Client-Side Rendering vs. Pre-Rendering)

Standart bir React uygulamasında, tarayıcı, kullanıcı arayüzünü oluşturmak için JavaScript talimatlarıyla birlikte sunucudan boş bir HTML kabuğu alır. İlk işleme çalışması kullanıcının cihazında gerçekleştiği için buna istemci tarafı işleme denir.

<img src="https://nextjs.org/static/images/learn/foundations/client-side-rendering.png"/>

``
Not: React'le `useSWR` veya `useEffect()` gibi bir veri alma kancasıyla veri getirmeyi seçerek Next.js uygulamanızdaki belirli bileşenler için istemci tarafı oluşturmayı kullanmayı tercih edebilirsiniz.
``

Buna karşılık, Next.js varsayılan olarak her sayfayı önceden işler. Ön işleme(Pre-rendering), HTML'nin kullanıcının cihazında JavaScript tarafından yapılması yerine önceden bir sunucuda oluşturulduğu anlamına gelir.

Pratikte bu, tamamen istemci tarafında oluşturulmuş bir uygulama için, kullanıcının oluşturma işi yapılırken boş bir sayfa göreceği anlamına gelir. Kullanıcının oluşturulmuş HTML'yi göreceği önceden oluşturulmuş bir uygulamayla karşılaştırıldığında:

<img src="https://nextjs.org/static/images/learn/foundations/pre-rendering.png"/>

İki ön işleme türünü tartışalım:

### Sunucu Tarafı Oluşturma

Sunucu tarafı oluşturma ile, her istek için sayfanın HTML'si bir sunucuda(server) oluşturulur. Sayfayı etkileşimli hale getirmek için oluşturulan HTML, JSON verileri ve JavaScript talimatları daha sonra istemciye(client) gönderilir.

İstemcide HTML, etkileşimli olmayan hızlı bir sayfa göstermek için kullanılırken React, bileşenleri etkileşimli hale getirmek için JSON verilerini ve JavaScript talimatlarını kullanır (örneğin, bir düğmeye olay işleyicileri eklemek). Bu işleme hidrasyon denir.

Next.js'de `getServerSideProps` kullanarak sunucu tarafı oluşturma sayfalarını tercih edebilirsiniz.

### Statik Site Oluşturma

Statik Site Oluşturma ile, HTML sunucuda oluşturulur, ancak sunucu tarafı oluşturmadan farklı olarak, çalışma zamanında sunucu yoktur. Bunun yerine, uygulama dağıtıldığında içerik oluşturma zamanında bir kez oluşturulur ve HTML bir CDN'de depolanır ve her istek için yeniden kullanılır.

Next.js'de `getStaticProps` kullanarak statik olarak sayfalar oluşturmayı seçebilirsiniz.

Next.js'nin güzelliği, Statik Site Oluşturma, Sunucu Tarafı Oluşturma veya İstemci Tarafı Oluşturma olsun, sayfa sayfa bazında kullanım durumunuz için en uygun oluşturma yöntemini seçebilmenizdir. Özel kullanım durumunuz için hangi oluşturma yönteminin doğru olduğu hakkında daha fazla bilgi edinmek için veri alma belgelerine bakın .

Bir sonraki bölümde, dağıtıldıktan sonra kodunuzun nerede saklanabileceğini veya çalıştırılabileceğini tartışacağız.




