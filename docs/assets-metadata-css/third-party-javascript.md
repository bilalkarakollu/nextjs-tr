---
sidebar_position: 3
---

# Üçüncü Taraf JavaScript

Üçüncü taraf JavaScript , üçüncü taraf bir kaynaktan eklenen tüm komut dosyalarını ifade eder. Genellikle, bir siteye analitik, reklamlar ve müşteri destek widget'ları gibi sıfırdan yazılması gerekmeyen daha yeni işlevler eklemek için üçüncü taraf komut dosyaları eklenir.

# Üçüncü Taraf JavaScript Ekleme


Bir Next.js sayfasına üçüncü taraf komut dosyasını nasıl ekleyebileceğimize bakalım.

Editörünüzde `pages/posts/first-post.js` açın ve aşağıdaki satırları bulun:

```html
<Head>
  <title>First Post</title>
</Head>
```

Meta verilere ek olarak, mümkün olan en kısa sürede yüklenmesi ve yürütülmesi gereken komut dosyaları genellikle `<head>` içine eklenir. Normal bir HTML `<script>` öğesi kullanarak, aşağıdaki gibi harici bir komut dosyası eklenir:


```html
<Head>
  <title>First Post</title>
  <script src="https://connect.facebook.net/en_US/sdk.js" />
</Head>
```

Bu komut dosyası, Facebook sosyal eklentilerini ve diğer işlevleri tanıtmak için yaygın olarak kullanılan Facebook SDK'sını içerir. Bu yaklaşım işe yarasa da, komut dosyalarını bu şekilde dahil etmek, aynı sayfaya getirilen diğer JavaScript koduna göre ne zaman yükleneceği konusunda net bir fikir vermez. Belirli bir komut dosyası oluşturmayı engelliyorsa ve sayfa içeriğinin yüklenmesini geciktirebiliyorsa, bu, performansı önemli ölçüde etkileyebilir.

### Komut Dosyası Bileşenini Kullanma

`next/script` HTML `<script>` öğesinin bir uzantısıdır ve ek komut dosyaları getirildiğinde ve yürütüldüğünde optimize eder.

Aynı dosyada, dosyanın başına `next/script` den bir `Script` ekleyin:

Şimdi `FirstPost` bileşeni içerecek şekilde `Script` bileşeni güncelleyin:

```js
export default function FirstPost() {
  return (
    <>
      <Head>
        <title>First Post</title>
      </Head>
      <Script
        src="https://connect.facebook.net/en_US/sdk.js"
        strategy="lazyOnload"
        onLoad={() =>
          console.log(`script loaded correctly, window.FB has been populated`)
        }
      />
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </>
  );
}

```


Komut Dosyası bileşeninde birkaç ek özelliğin tanımlandığına dikkat edin:

- `strategy` üçüncü taraf komut dosyasının ne zaman yükleneceğini kontrol eder. `lazyOnload` değeri, Next.js'ye tarayıcı boşta kalma süresi sırasında bu betiği tembelce yüklemesini söyler.
- `onLoad` komut dosyasının yüklenmesi tamamlandıktan hemen sonra herhangi bir JavaScript kodunu çalıştırmak için kullanılır. Bu örnekte, komut dosyasının doğru şekilde yüklendiğini belirten bir iletiyi konsola günlüğe kaydediyoruz.