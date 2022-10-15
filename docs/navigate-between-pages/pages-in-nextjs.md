---
sidebar_position: 2
---

# Next.js'deki sayfalar

Sayfalar, dosya adlarına göre bir rota ile ilişkilendirilir. Örneğin, geliştirme aşamasında:

- `pages/index.js` rota ile ilişkilidir.
- `pages/posts/first-post.js`  rotası `/posts/first-post` rota ile ilişkilidir.

`pages/index.js` Dosya zaten elimizde, `pages/posts/first-post.js` nasıl çalıştığını görmek için oluşturalım.

### Yeni Sayfa Oluştur

`pages` altında `posts` dizini oluşturun.

`posts` dizininde `first-post.js` bir dosya oluşturun:

```js
export default function FirstPost() {
  return <h1>First Post</h1>;
}
```

Bileşen herhangi bir ada sahip olabilir, ancak onu dışa `default` olarak dışa aktarmanız gerekir.


Şimdi, geliştirme sunucusunun çalıştığından emin olun ve `http://localhost:3000/posts/first-post` adresini ziyaret edin. Sayfayı görmelisiniz:

<img src="https://nextjs.org/static/images/learn/navigate-between-pages/first-post.png"/>

Next.js'de bu şekilde farklı sayfalar oluşturabilirsiniz.

`pages` Dizin altında bir JS dosyası oluşturmanız yeterlidir; dosyanın yolu URL yolu olur.

Bu bir bakıma HTML veya PHP dosyalarını kullanarak web siteleri oluşturmaya benzer. HTML yazmak yerine JSX yazar ve React Components kullanırsınız.

Yeni eklenen sayfaya ana sayfadan gidebilmemiz için bir link ekleyelim.

