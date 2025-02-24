---
sidebar_position: 5
---

# Bileşenlerle Kullanıcı Arayüzü Oluşturma

Kullanıcı arayüzleri, bileşen(component) adı verilen daha küçük yapı taşlarına bölünebilir.

Bileşenler, bağımsız, yeniden kullanılabilir kod parçacıkları oluşturmanıza olanak tanır. Bileşenleri LEGO tuğlaları olarak düşünüyorsanız, bu ayrı tuğlaları alıp daha büyük yapılar oluşturmak için bir araya getirebilirsiniz. Kullanıcı arayüzünün bir parçasını güncellemeniz gerekiyorsa, belirli bileşeni veya tuğlayı güncelleyebilirsiniz.

<img src="/img/learn/learn-components.jpeg"/>

Bu modülerlik, uygulamamızın geri kalanına dokunmadan bileşenleri kolayca ekleyebildiğiniz, güncelleyebildiğiniz ve silebildiğiniz için kodunuzun büyüdükçe daha sürdürülebilir olmasını sağlar.

React bileşenleriyle ilgili güzel olan şey, onların yalnızca JavaScript olmalarıdır. JavaScript perspektifinden bir React bileşenini nasıl yazabileceğinizi görelim:

### Bileşen oluşturma

Reactta componentler function dur, `script` etiketinin içerisine `header` functionu yazın:

```html
<script type="text/jsx">
  const app = document.getElementById("app")


  function header() {
  }

  ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app)
</script>
```
Bileşen, UI öğelerini döndüren bir işlevdir . Fonksiyonun return ifadesinin içine JSX yazabilirsiniz:

```html
<script type="text/jsx">
  const app = document.getElementById("app")

  function header() {
     return (<h1>Develop. Preview. Ship. 🚀</h1>)
   }

  ReactDOM.render(, app)
</script>
```

Bu bileşeni DOM'a işlemek için, onu ReactDOM.render()yöntemde ilk argüman olarak iletebilirsiniz:

```html
<script type="text/jsx">

  const app = document.getElementById("app")

  function header() {
     return (<h1>Develop. Preview. Ship. 🚀</h1>)
   }


   ReactDOM.render(header, app)
</script>
```

Ama bir saniye bekle. Yukarıdaki kodu tarayıcınızda çalıştırmayı denerseniz, bir hata alırsınız. Bunun işe yaraması için yapmanız gereken iki şey var:

İlk olarak, onları düz HTML ve JavaScript'ten ayırt etmek için React bileşenleri büyük harfle yazılmalıdır.

```javascript
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

// Capitalize the React Component
ReactDOM.render(Header, app);
```

İkinci olarak, React bileşenlerini normal HTML etiketlerini kullandığınız şekilde, açılı ayraçlarla kullanırsınız ``<>``.

```javascript
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

ReactDOM.render(<Header />, app);
```

### Yuvalama Bileşenleri (Nesting Component)

Uygulamalar genellikle tek bir bileşenden daha fazla içerik içerir. Normal HTML öğelerinde yaptığınız gibi React bileşenlerini iç içe yerleştirebilirsiniz .

Örneğinizde, `HomePage` adında yeni bir bileşen oluşturun:

```js
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}
function HomePage() {
  return <div></div>;
}

ReactDOM.render(<Header />, app);
```

Ardından `<Header>` bileşeni yeni `<HomePage>` bileşenin içine yerleştirin:

```js
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

function HomePage() {
  return (
    <div>
      {/* Nesting the Header component */}
      <Header />
    </div>
  );
}

ReactDOM.render(<Header />, app);
```

### Bileşen Ağaçları(Component Trees)

Bileşen ağaçları oluşturmak için React bileşenlerini bu şekilde iç içe yerleştirmeye devam edebilirsiniz.

<img src="/img/learn/learn-component-tree.jpeg"/>

Örneğin, üst düzey HomePagebileşeniniz bir Header, bir Articleve bir FooterBileşen içerebilir. Ve bu bileşenlerin her birinin sırayla kendi alt bileşenleri olabilir. Örneğin, `Header` bileşeni, `Logo`, `Title`, `Navigation` bileşeni içerebilir.

Bu modüler biçim, bileşenleri uygulamanızın içinde farklı yerlerde yeniden kullanmanıza olanak tanır.

Projenizde, artık en üst düzey bileşeniniz `<HomePage>` olduğundan, onu `ReactDOM.render()` ile yönteme geçirebilirsiniz:

```js
function Header() {
    return <h1>Develop. Preview. Ship. 🚀</h1>;
}

function HomePage() {
    return (
        <div>
            <Header />
        </div>
    );
}

ReactDOM.render(<HomePage />, app);
```

Bir sonraki bölümde, sahne donanımlarını ve bunları bileşenleriniz arasında veri aktarmak için nasıl kullanabileceğinizi tartışacağız.