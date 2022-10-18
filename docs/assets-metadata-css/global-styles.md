---
sidebar_position: 7
---

# Global Styles

CSS Modülleri, bileşen düzeyinde stiller için kullanışlıdır. Ancak, her sayfada biraz CSS yüklenmesini istiyorsanız, Next.js'nin bunu da desteği vardır.

Global CSS dosyalarını yüklemek için aşağıdaki içeriğe sahip bir `pages/_app.js` dosyası oluşturun:

```js
export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
```
Bu bileşen `App`, tüm farklı sayfalarda ortak olacak olan en üst düzey bileşendir. Örneğin, sayfalar arasında gezinirken durumu korumak için bu bileşeni kullanabilirsiniz.

### Geliştirme Sunucusunu Yeniden Başlatın

```js
npm run dev
```

### Genel CSS Ekleme

Next.js'de, global CSS dosyalarını `pages/_app.js` dan aktarabilirsiniz. Global CSS'yi başka hiçbir yere aktaramazsınız.

Global CSS'nin dışına aktarılamamasının nedeni, global CSS'nin `pages/_app.js` sayfadaki tüm öğeleri etkilemesidir.

Global CSS dosyasını herhangi bir yere yerleştirebilir ve herhangi bir ad kullanabilirsiniz. Öyleyse aşağıdakileri yapalım:

- Bir üst düzey `styles` dizin ve bir `global.css` dosya oluşturun.
- `styles/global.css` içine aşağıdaki CSS'yi ekleyin. Bu kod, bazı stilleri sıfırlar ve `a` etiketin rengini değiştirir:

```css
html,
body {
  padding: 0;
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen, Ubuntu,
    Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
  line-height: 1.6;
  font-size: 18px;
}

* {
  box-sizing: border-box;
}

a {
  color: #0070f3;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

img {
  max-width: 100%;
  display: block;
}
```

Son olarak, daha önce oluşturduğunuz `pages/_app.js` dosyanın içindeki CSS dosyasını içe aktarın:

```js
// `pages/_app.js`
import '../styles/global.css';

export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
```

 stillerin uygulandığını göreceksiniz. İçe aktarılan tüm stiller, uygulamanın tüm sayfalarına genel olarak uygulanacaktır.

 <img src="https://nextjs.org/static/images/learn/assets-metadata-css/global-styles.png"/>