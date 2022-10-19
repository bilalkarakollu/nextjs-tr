---
sidebar_position: 3
---

# Ön işleme ve Veri Alma

### Verili ve Verisiz Statik Üretim

Statik Üretim, verili ve verisiz yapılabilir.

Şimdiye kadar oluşturduğumuz tüm sayfalar harici veri alınmasını gerektirmiyor. Uygulama üretim için oluşturulduğunda bu sayfalar otomatik olarak statik olarak oluşturulur.

<img src="https://nextjs.org/static/images/learn/data-fetching/static-generation-without-data.png"/>

Ancak, bazı sayfalar için, önce bazı harici verileri getirmeden HTML'yi oluşturamayabilirsiniz. Belki dosya sistemine erişmeniz, harici API getirmeniz veya derleme zamanında veritabanınızı sorgulamanız gerekir. Next.js, kullanıma hazır bu durumu destekler: Verilerle Statik Oluşturma.


<img src="https://nextjs.org/static/images/learn/data-fetching/static-generation-with-data.png"/>

### `getStaticProps` Kullanarak Verilerle Statik Oluşturma

O nasıl çalışır? Pekala, Next.js'de bir sayfa bileşenini dışa aktardığınızda, `async` adlı bir işlevi de dışa aktarabilirsiniz `getStaticProps`. Bunu yaparsanız, o zaman:

- `getStaticProps` üretimde yapım zamanında çalışır ve…
- İşlevin içinde, harici verileri alabilir ve sayfaya sahne olarak gönderebilirsiniz.

```js
export default function Home(props) { ... }

export async function getStaticProps() {
  // Get external data from the file system, API, DB, etc.
  const data = ...

  // The value of the `props` key will be
  //  passed to the `Home` component
  return {
    props: ...
  }
}
```

Esasen, `getStaticProps` Next.js'ye şunu söylemenizi sağlar: "Hey, bu sayfanın bazı veri bağımlılıkları var - bu yüzden bu sayfayı derleme zamanında önceden oluşturduğunuzda, önce bunları çözdüğünüzden emin olun!"


### hadi `getStaticProps` kullanalım 

Yaparak öğrenmek daha kolaydır, bu nedenle bir sonraki sayfadan başlayarak `getStaticProps` blogumuzu uygulamak için kullanacağız.


