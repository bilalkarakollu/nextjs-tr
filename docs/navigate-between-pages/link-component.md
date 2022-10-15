---
sidebar_position: 3
---

# Link Component

Web sitelerindeki sayfalar arasında bağlantı kurarken `<a>` HTML etiketini kullanırsınız.


Next.js'de, uygulamanızdaki sayfalar arasında bağlantı oluşturmak için `Link` Bileşeni `next/link` kullanabilirsiniz. istemci tarafında(client-side) gezinme yapmanıza olanak tanır ve gezinme davranışı üzerinde size daha iyi kontrol sağlayan aksesuarları kabul eder.

### Using `<Link>`

İlk önce, `pages/index.js` öğesini açın ve en üste `next/link`  bu satırı ekleyerek `Link` bileşeni içe aktarın: 

```js
import Link from 'next/link';
```

Ardından `h1` şuna benzeyen etiketi bulun:

```js
<h1 className="title">
  Learn <a href="https://nextjs.org">Next.js!</a>
</h1>
```

Ve şu şekilde değiştirin:

```js
<h1 className="title">
  Read <Link href="/posts/first-post">this page!</Link>
</h1>
```

Ardından, `pages/posts/first-post.js` içeriğini açın ve aşağıdakiyle değiştirin:

```js
import Link from 'next/link';

export default function FirstPost() {
  return (
    <>
      <h1>First Post</h1>
      <h2>
        <Link href="/">Back to home</Link>
      </h2>
    </>
  );
}
```

Gördüğünüz gibi `<a></a>`, bileşen etiketleri kullanmaya benzer, ancak bunun yerine `Link`.

Çalışıp çalışmadığını kontrol edelim. Artık her sayfada ileri geri gitmenize izin veren bir bağlantınız olmalıdır:

<img src="https://nextjs.org/static/images/learn/navigate-between-pages/links.gif"/>
