---
sidebar_position: 9
---

# Stil İpuçları

İşte size yardımcı olabilecek bazı stil ipuçları.

### Sınıfları değiştirmek için `classnames` kitaplığı kullanma

`classnames` sınıf adları arasında kolayca geçiş yapmanızı sağlayan basit bir kitaplıktır.

`npm install classnames` veya kullanarak yükleyebilirsiniz `yarn add classnames`.


Lütfen daha fazla ayrıntı için <a href="https://github.com/JedWatson/classnames">belgelerine</a> bakın, ancak işte temel kullanım:

- '`type`' '`success`' '`error`' Kabul eden, veya olabilen bir Alertbileşen oluşturmak istediğinizi varsayalım.
- '`success`' ise, metin renginin yeşil olmasını istersiniz. '`error`' ise, metin renginin kırmızı olmasını istersiniz.

Önce şöyle bir CSS modülü (örn. alert.module.css) yazabilirsiniz:

```css
.success {
  color: green;
}
.error {
  color: red;
}
```
Ve `classnames` bu şekilde kullanın:

```js
import styles from './alert.module.css';
import cn from 'classnames';

export default function Alert({ children, type }) {
  return (
    <div
      className={cn({
        [styles.success]: type === 'success',
        [styles.error]: type === 'error',
      })}
    >
      {children}
    </div>
  );
}
```

### PostCSS Yapılandırmasını Özelleştirme

Next.js, kullanıma hazır, yapılandırma olmadan, PostCSS kullanarak CSS'yi derler.

PostCSS yapılandırmasını özelleştirmek için `postcss.config.js`. Bu, Tailwind CSS gibi kitaplıklar kullanıyorsanız kullanışlıdır.

İşte Tailwind CSS ekleme adımları. İlk önce paketleri kurun:

```
npm install -D tailwindcss autoprefixer postcss
```

Ardından, bir `postcss.config.js` oluşturun:

```js
// postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};
```

Ayrıca, şu seçeneği belirterek içerik kaynaklarını yapılandırmanızı öneririz `content` `tailwind.config.js`:

```js
// tailwind.config.js
module.exports = {
  content: [
    './pages/**/*.{js,ts,jsx,tsx}',
    './components/**/*.{js,ts,jsx,tsx}',
    // For the best performance and to avoid false positives,
    // be as specific as possible with your content configuration.
  ],
};
```

### Sass'ı kullanma

Kutunun dışında, Next.js, `.scss` hem uzantıları hem de `.sass` uzantıları kullanarak Sass'ı içe aktarmanıza olanak tanır. Bileşen düzeyinde Sass'ı CSS Modülleri `module.scss` veya `module.sass` uzantısı aracılığıyla kullanabilirsiniz.

Next.js'nin yerleşik Sass desteğini kullanmadan önce şunları yüklediğinizden emin olun sass:

```
npm install -D sass
```

<strong>Bu ders için bu kadar!</strong>

Next.js'nin yerleşik CSS Desteği ve CSS Modülleri hakkında daha fazla bilgi edinmek için CSS Belgelerine bakın.


