---
sidebar_position: 2
---
# React'e Başlarken

React'i projenizde kullanmak için, <a href="https://unpkg.com/">unpkg.com</a> adlı harici bir web sitesinden iki React betiği yükleyebilirsiniz:

- react, çekirdek React kitaplığıdır.
- react-dom, React'i DOM ile kullanmanızı sağlayan DOM'a özgü yöntemler sağlar.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>

    <script type="text/javascript">
      const app = document.getElementById('app');
    </script>
  </body>
</html>
```

DOM'yi doğrudan düz JavaScript ile değiştirmek yerine, `react-dom` dan `ReactDOM.render()` kullanıp `#app` elementinin içine `h1` elementi render edebilirsin.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>

    <script type="text/javascript">
      const app = document.getElementById('app');
      ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);
    </script>
  </body>
</html>
```

Ancak bu kodu tarayıcıda çalıştırmayı denerseniz, bir sözdizimi hatası alırsınız:

<img src="https://nextjs.org/static/images/learn/foundations/error.png"/>

Bunun nedeni `<h1>...</h1>` geçerli Javascript olmamasıdır. Bu kod parçası JSX'tir.

### JSX nedir?

JSX, UI'nizi tanıdık bir HTML benzeri sözdiziminde tanımlamanıza olanak tanıyan bir JavaScript sözdizimi uzantısıdır. JSX'in güzel yanı, <a href="https://beta.reactjs.org/learn/writing-markup-with-jsx#the-rules-of-jsx">üç JSX kuralına uymanın</a> dışında, HTML ve JavaScript dışında herhangi bir yeni sembol veya sözdizimi öğrenmenize gerek olmamasıdır.

Tarayıcıların kutudan çıktığı haliyle JSX'i anlamadığını unutmayın, bu nedenle JSX kodunuzu normal JavaScript'e dönüştürmek için <a href="https://babeljs.io/">Babel gibi bir JavaScript derleyicisine ihtiyacınız olacaktır.</a>

### Projenize Babel Eklemek

Babel'i projenize eklemek için aşağıdaki betiği kopyalayıp `index.html` dosyanıza yapıştırın:

```html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```


Ayrıca, komut dosyası türünü `type=text/jsx` ekleyin.

```html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <!-- Babel Script -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const app = document.getElementById('app');
      ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);
    </script>
  </body>
</html>
```

Ardından, düzgün çalıştığını doğrulamak için kodunuzu tarayıcıda çalıştırabilirsiniz.

Az önce yazdığınız bildirimsel React kodunu karşılaştırarak:

```html
<script type="text/jsx">
  const app = document.getElementById("app")
  ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app)
</script>
```

önceki bölümde yazdığınız zorunlu JavaScript koduna:

```html
<script type="text/javascript">
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const headerContent = document.createTextNode('Develop. Preview. Ship. 🚀');
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```

React'i kullanarak birçok tekrar eden kodu nasıl azaltabileceğinizi görmeye başlayabilirsiniz.

React'in yaptığı da tam olarak budur, sizin adınıza görevleri gerçekleştiren yeniden kullanılabilir kod parçacıkları içeren bir kitaplıktır - bu durumda kullanıcı arayüzünü günceller.