---
sidebar_position: 6
---

# Layout Component


İlk olarak, tüm sayfalarda paylaşılacak bir Layout bileşeni oluşturalım.

- `components` adlı bir üst düzey dizin oluşturun.
- `components` içinde , aşağıdaki içeriğe sahip bir dosya oluşturun `layout.js`:


```js
export default function Layout({ children }) {
  return <div>{children}</div>;
}
```
Ardından `pages/posts/first-post.js` açın, `Layout` bileşen için bir içe aktarma ekleyin ve onu en dıştaki bileşen yapın:

```js
import Head from 'next/head';
import Link from 'next/link';
import Layout from '../../components/layout';

export default function FirstPost() {
  return (
    <Layout>
      <Head>
        <title>First Post</title>
      </Head>
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </Layout>
  );
}
```

Şimdi `Layout` bileşene bazı stiller ekleyelim. Bunu yapmak için, CSS dosyalarını bir React bileşenine aktarmanıza izin veren <a href="https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css">CSS Modüllerini</a> kullanacağız.

Aşağıdaki içeriğe sahip bir dosya oluşturun `components/layout.module.css`:

```css
.container {
  max-width: 36rem;
  padding: 0 1rem;
  margin: 3rem auto 6rem;
}
```

Bu `container` sınıfı içeride kullanmak için `components/layout.js` de yapmanız gerekenler:

- CSS dosyasını içe aktarın ve ona bir ad atayın. `styles`
- `className` içerisinde `styles.container` olarak kullanın.

`components/layout.js` İçeriğini açın ve aşağıdakiyle değiştirin:

```js
import styles from './layout.module.css';

export default function Layout({ children }) {
  return <div className={styles.container}>{children}</div>;
}
```

Şimdi `http://localhost:3000/posts/first-post` adresine giderseniz, metnin şimdi ortalanmış bir kapsayıcının içinde olduğunu görmelisiniz:

<img src="https://nextjs.org/static/images/learn/assets-metadata-css/layout.png"/>

### Benzersiz Sınıf Adlarını Otomatik Olarak Oluşturur

Şimdi, tarayıcınızın geliştirme araçlarındaki HTML'ye bir göz atarsanız, bileşen tarafından oluşturulanın şuna benzeyen bir sınıf adına sahip olduğunu fark edeceksiniz `layout_container__...`:


<img src="https://nextjs.org/static/images/learn/assets-metadata-css/devtools.png"/>


CSS Modüllerinin yaptığı budur: Otomatik olarak benzersiz sınıf adları oluşturur. CSS Modüllerini kullandığınız sürece, sınıf adı çakışmaları konusunda endişelenmenize gerek yoktur.

Ayrıca Next.js'nin kod bölme özelliği CSS Modüllerinde de çalışır. Her sayfa için minimum miktarda CSS yüklenmesini sağlar. Bu, daha küçük paket boyutlarıyla sonuçlanır.

CSS Modülleri, derleme sırasında JavaScript paketlerinden çıkarılır ve `.css` Next.js tarafından otomatik olarak yüklenen dosyalar oluşturur.
