---
sidebar_position: 2
---


# Meta Veri

`<title></title>` HTML etiketi gibi sayfanın meta verilerini değiştirmek istersek ne olur?

`<title>` bir HTML etiketidir, hadi Next.js de `<head></head>` etiketi içindeki bir metayı nasıl değiştireceğimize bakalım.


`pages/index.js` editörünüzde açın ve ağıdaki adımları takip edin.

```js
<Head>
  <title>Create Next App</title>
  <link rel="icon" href="/favicon.ico" />
</Head>
```


`<head></head>` küçük harf yerine `<Head></Head>` büyük harf kullanıldığına dikkat edin. Next.js'de yerleşik olarak bulunan bir React Bileşenidir.

`<Head></Head>`Bileşeni `next/head` modülden içe aktarabilirsiniz.

### `first-post.js` içine `Head` ekleme

`pages/posts/first-post.js` Dosyamızı açalım ve `<Head></Head>` şunun için dosyanın başına `next/head` ekleyelim.

```js
import Head from 'next/head';
```

Ardından, dışa aktarılan `FirstPost` bileşeni, `Head` bileşeni içerecek şekilde güncelleyin. Şimdilik sadece `title` etiketi ekleyeceğiz:

```js
export default function FirstPost() {
  return (
    <>
      <Head>
        <title>First Post</title>
      </Head>
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


`http://localhost:3000/posts/first-post` adresine erişmeyi deneyin. Tarayıcı sekmesi şimdi “First Post” yazmalıdır. Tarayıcınızın geliştirici araçlarını kullanarak `title` etiketin eklendiğini görmelisiniz.