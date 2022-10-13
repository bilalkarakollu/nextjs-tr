---
sidebar_position: 1
---

# Next.js'ye Başlarken

Next.js'yi projenize eklemek için artık `react` ve `react-dom` komut dosyalarını unpkg.com'dan yüklemeniz gerekmeyecek. Bunun yerine, Node Paket Yöneticisi'ni kullanarak bu paketleri yerel olarak kurabilirsiniz: `npm`.

Bunu yapmak için boş bir nesne `{}` ile `package.json` adlandırılan yeni bir dosya oluşturun.

```js
// package.json
{
}
```

Terminalinizde `npm install react react-dom next` çalıştırın. Kurulum tamamlandıktan sonra, `package.json` dosyanızın içinde listelenen proje bağımlılıklarınızı görebilmeniz gerekir:

```js
// package.json
{
  "dependencies": {
    "next": "^12.1.0",
    "react": "^17.0.2",
    "react-dom": "^17.0.2"
  }
}
```

Ayrıca `node_modules`, bağımlılıklarımızın gerçek dosyalarını içeren yeni bir klasör göreceksiniz.

Dosyaya geri dönerek `index.html` nizi temizleyin.

`import { useState } from "react"` dosyanızın başına ekleyin. Kodunuz şöyle görünmelidir:

```js
// index.html
import { useState } from 'react';
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}

function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  const [likes, setLikes] = useState(0);

  function handleClick() {
    setLikes(likes + 1);
  }

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>

      <button onClick={handleClick}>Like ({likes})</button>
    </div>
  );
}
```

HTML dosyasında kalan tek kod JSX'tir, böylece dosya türünü `.js` veya `.jsx`. Olarak değiştirebilirsiniz.

Şimdi, bir Next.js uygulamasına tam olarak geçiş yapmak için yapmanız gereken üç şey daha var:


1. `index.js` Dosyayı `pages` adı verilen yeni bir klasöre taşıyın(bununla ilgili daha fazla bilgi daha sonra).
2. Next.js'nin bu sayfanın ana bileşeni olarak hangi bileşeni oluşturacağını ayırt etmesine yardımcı olmak için ana React bileşeninize varsayılan dışa aktarma ekleyin.

```js
// ...
   export default function HomePage() {
   //  ...
```
3. Geliştirme sırasında Next.js geliştirme sunucusunu çalıştırmak için `package.json` dosyanıza bir komut dosyası ekleyin.

```js
 // package.json
   {
    "scripts": {
        "dev": "next dev"
    },
     // "dependencies": {
     //   "next": "^11.1.0",
     //   "react": "^17.0.2",
     //   "react-dom": "^17.0.2"
     // }
   }
```

### Geliştirme sunucusunu çalıştırma


Her şeyin çalıştığını doğrulamak için, uygulamanızı `npm run dev` terminalinizin içinde çalıştırarak ve tarayıcıda localhost:3000'e giderek görüntüleyebilirsiniz. Ardından, kodda küçük bir değişiklik yapın ve kaydedin.

Dosyayı kaydettikten sonra, değişikliği yansıtmak için tarayıcının otomatik olarak güncellendiğini fark etmelisiniz.

Bu özelliğe Hızlı Yenileme adı verilir . Yaptığınız tüm düzenlemeler hakkında size anında geri bildirim sağlar ve Next.js ile önceden yapılandırılmış olarak gelir.

Özetlemek gerekirse, kodunuz bundan...

```js
<html>
  <body>
    <div id="app"></div>

    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <script type="text/jsx">
      const app = document.getElementById("app")

      function Header({ title }) {
        return <h1>{title ? title : "Default title"}</h1>
      }

      function HomePage() {
        const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"]
        const [likes, setLikes] = React.useState(0)

        function handleClick() {
          setLikes(likes + 1)
        }

        return (
          <div>
            <Header title="Develop. Preview. Ship. 🚀" />
            <ul>
              {names.map((name) => (
                <li key={name}>{name}</li>
              ))}
            </ul>

            <button onClick={handleClick}>Like ({likes})</button>
          </div>
        )
      }

      ReactDOM.render(<HomePage />, app)
    </script>
  </body>
</html>
```

buna

```js
import { useState } from 'react';

function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}

export default function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];
  const [likes, setLikes] = useState(0);

  function handleClick() {
    setLikes(likes + 1);
  }

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>

      <button onClick={handleClick}>Like ({likes})</button>
    </div>
  );
}
```

Yüzeyde, bu kod satırlarında küçük bir azalmadır, ancak bir şeyi vurgulamaya yardımcı olur: React, modern etkileşimli kullanıcı arayüzü oluşturmak için temel ilkelleri sağlayan bir kitaplıktır. Ancak, oluşturduğunuz kullanıcı arayüzünü bir uygulamada birleştirmek için hala bazı çalışmalar var.

Geçişe baktığınızda, Next.js kullanmanın yararları hakkında bir fikir ediniyor olabilirsiniz. Artık düşünmek zorunda olmadığınız karmaşık takım konfigürasyonunun bir tadı olan babel komut dosyasını kaldırdınız. Ayrıca, Next.js ile bekleyebileceğiniz birçok geliştirici deneyimi özelliğinden sadece biri olan Hızlı Yenilemeyi çalışırken gördünüz.