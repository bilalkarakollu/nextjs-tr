---
sidebar_position: 8
---

# Polishing Layout

Şimdiye kadar, yalnızca CSS Modülleri gibi kavramları göstermek için minimum React ve CSS kodu ekledik. Veri alma ile ilgili bir sonraki dersimize geçmeden önce, sayfa stilimizi ve kodumuzu düzeltelim.


### Güncellemecomponents/layout.module.css

İlk olarak, `components/layout.module.css` düzen ve profil resmi için içeriğini açın ve aşağıdaki daha gösterişli stiller ile değiştirin:

```css
.container {
  max-width: 36rem;
  padding: 0 1rem;
  margin: 3rem auto 6rem;
}

.header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.backToHome {
  margin: 3rem 0 0;
}
```

### `styles/utils.module.css` Oluşturmak

İkinci olarak, tipografi ve birden çok bileşende faydalı olacak diğerleri için bir dizi yardımcı CSS sınıfı oluşturalım.

Aşağıdaki içeriğe sahip yeni bir CSS dosyası ekleyelim `styles/utils.module.css`:

```css
.heading2Xl {
  font-size: 2.5rem;
  line-height: 1.2;
  font-weight: 800;
  letter-spacing: -0.05rem;
  margin: 1rem 0;
}

.headingXl {
  font-size: 2rem;
  line-height: 1.3;
  font-weight: 800;
  letter-spacing: -0.05rem;
  margin: 1rem 0;
}

.headingLg {
  font-size: 1.5rem;
  line-height: 1.4;
  margin: 1rem 0;
}

.headingMd {
  font-size: 1.2rem;
  line-height: 1.5;
}

.borderCircle {
  border-radius: 9999px;
}

.colorInherit {
  color: inherit;
}

.padding1px {
  padding-top: 1px;
}

.list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.listItem {
  margin: 0 0 1.25rem;
}

.lightText {
  color: #666;
}
```

### Güncelleme `components/layout.js`

Üçüncüsü, `components/layout.js` açın ve içeriğini aşağıdaki kodla değiştirin `Your Name`, gerçek bir adla değiştirin:

```js
import Head from 'next/head';
import Image from 'next/image';
import styles from './layout.module.css';
import utilStyles from '../styles/utils.module.css';
import Link from 'next/link';

const name = 'Your Name';
export const siteTitle = 'Next.js Sample Website';

export default function Layout({ children, home }) {
  return (
    <div className={styles.container}>
      <Head>
        <link rel="icon" href="/favicon.ico" />
        <meta
          name="description"
          content="Learn how to build a personal website using Next.js"
        />
        <meta
          property="og:image"
          content={`https://og-image.vercel.app/${encodeURI(
            siteTitle,
          )}.png?theme=light&md=0&fontSize=75px&images=https%3A%2F%2Fassets.vercel.com%2Fimage%2Fupload%2Ffront%2Fassets%2Fdesign%2Fnextjs-black-logo.svg`}
        />
        <meta name="og:title" content={siteTitle} />
        <meta name="twitter:card" content="summary_large_image" />
      </Head>
      <header className={styles.header}>
        {home ? (
          <>
            <Image
              priority
              src="/images/profile.jpg"
              className={utilStyles.borderCircle}
              height={144}
              width={144}
              alt=""
            />
            <h1 className={utilStyles.heading2Xl}>{name}</h1>
          </>
        ) : (
          <>
            <Link href="/">
              <a>
                <Image
                  priority
                  src="/images/profile.jpg"
                  className={utilStyles.borderCircle}
                  height={108}
                  width={108}
                  alt=""
                />
              </a>
            </Link>
            <h2 className={utilStyles.headingLg}>
              <Link href="/">
                <a className={utilStyles.colorInherit}>{name}</a>
              </Link>
            </h2>
          </>
        )}
      </header>
      <main>{children}</main>
      {!home && (
        <div className={styles.backToHome}>
          <Link href="/">
            <a>← Back to home</a>
          </Link>
        </div>
      )}
    </div>
  );
}

```

İşte yenilikler:

- `meta` `og:image` bir sayfanın içeriğini tanımlamak için kullanılan etiketler (gibi)
- `home` Başlığın ve görüntünün boyutunu ayarlayacak Boolean prop
- `home` false ise `Back to home` bağlantısı

### Güncelleme `pages/index.js`

Son olarak ana sayfayı güncelleyelim.

`pages/index.js` İçeriğini açın ve şununla değiştirin:

```js
import Head from 'next/head';
import Layout, { siteTitle } from '../components/layout';
import utilStyles from '../styles/utils.module.css';

export default function Home() {
  return (
    <Layout home>
      <Head>
        <title>{siteTitle}</title>
      </Head>
      <section className={utilStyles.headingMd}>
        <p>[Your Self Introduction]</p>
        <p>
          (This is a sample website - you’ll be building a site like this on{' '}
          <a href="https://nextjs.org/learn">our Next.js tutorial</a>.)
        </p>
      </section>
    </Layout>
  );
}
```

Ardından `[Your Self Introduction]`, kendinizi tanıtmanızla değiştirin. İşte yazarın profiliyle bir örnek:

<img src="https://nextjs.org/static/images/learn/assets-metadata-css/example.png"/>

Bu kadar! Artık veri alma derslerimize geçmek için cilalı düzen koduna sahibiz.

Bu dersi tamamlamadan önce, bir sonraki sayfada Next.js'nin CSS desteği ile ilgili bazı yararlı tekniklerden bahsedelim.



