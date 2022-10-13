---
sidebar_position: 1
---

# UI JavaScript ile Güncelleme


Projenize bir `h1` etiketi ekleyerek JavaScript ve DOM yöntemlerini nasıl kullanabileceğinizi görelim.

Kod düzenleyicinizi açın ve yeni bir index.htmldosya oluşturun. HTML dosyasının içine aşağıdaki kodu ekleyin:

```html
<!-- index.html -->
<html>
  <body>
    <div></div>
  </body>
</html>
```

Ardından, daha sonra hedefleyebilmeniz için `div` benzersiz bir `id` verin.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>
  </body>
</html>

```

HTML dosyanızın içine JavaScript yazmak için bir ``script`` etiket ekleyin:

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript"></script>
  </body>
</html>
```

Şimdi script tagının içine `div` e `id` ile erişmek için `getElementById()` methodunu ekleyin

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script type="text/javascript">
      const app = document.getElementById('app');
    </script>
  </body>
</html>
```

Yeni bir h1 öğesi oluşturmak için DOM yöntemlerini kullanmaya devam edebilirsiniz:

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script type="text/javascript">
      // Select the div element with 'app' id
      const app = document.getElementById('app');

      // Create a new H1 element
      const header = document.createElement('h1');

      // Create a new text node for the H1 element
      const headerContent = document.createTextNode(
        'Develop. Preview. Ship. 🚀',
      );

      // Append the text to the H1 element
      header.appendChild(headerContent);

      // Place the H1 element inside the div
      app.appendChild(header);
    </script>
  </body>
</html>
```

Her şeyin çalıştığından emin olmak için HTML dosyanızı tercih ettiğiniz tarayıcıda açın. 'Develop. Preview. Ship. 🚀', yazan bir h1 etiketi görmelisiniz.

### HTML'ye karşı DOM

Tarayıcı geliştirici araçlarınızdaki DOM öğelerine bakarsanız, DOM'nin `<h1>` öğeyisini içerdiğini fark edeceksiniz. Sayfanın DOM'si kaynak koddan veya başka bir deyişle, oluşturduğunuz orijinal HTML dosyasından farklıdır.

<img src="https://nextjs.org/static/images/learn/foundations/source-code.png"/>

Bunun nedeni, HTML'nin ilk sayfa içeriğini temsil etmesi, DOM'nin ise yazdığınız JavaScript koduyla değiştirilen güncellenmiş sayfa içeriğini temsil etmesidir.

DOM'yi düz JavaScript ile güncellemek çok güçlü ancak ayrıntılıdır. Tüm bu kodu metin içeren bir `<h1>` öğesi eklemek için yazdınız:

```html
<!-- index.html -->
<script type="text/javascript">
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const headerContent = document.createTextNode('Develop. Preview. Ship. 🚀');
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```

Bir uygulamanın veya ekibin boyutu büyüdükçe, uygulamaları bu şekilde oluşturmak giderek daha zor hale gelebilir.

Bu yaklaşımla geliştiriciler, bilgisayara işleri nasıl yapması gerektiğini anlatmak için talimatlar yazmak için çok zaman harcarlar. Ama ne göstermek istediğinizi açıklamak ve bilgisayarın DOM'yi nasıl güncelleyeceğini bulmasına izin vermek güzel olmaz mıydı?

### Zorunlu ve Bildirimsel Programlama

Yukarıdaki kod, zorunlu programlamaya iyi bir örnektir. Kullanıcı arayüzünün nasıl güncellenmesi gerektiğine ilişkin adımları yazıyorsunuz. Ancak, kullanıcı arayüzleri oluşturmaya gelince, geliştirme sürecini hızlandırabileceği için genellikle bildirimsel bir yaklaşım tercih edilir. DOM yöntemleri yazmak yerine, geliştiricilerin göstermek istediklerini (bu durumda, bir h1metin içeren bir etiket) beyan edebilmeleri yararlı olacaktır.

Başka bir deyişle, zorunlu programlama, bir şefe nasıl pizza yapılacağı konusunda adım adım talimatlar vermek gibidir. Bildirime dayalı programlama, pizza yapmak için gereken adımlar hakkında endişelenmeden pizza sipariş etmek gibidir. 🍕

Geliştiricilerin kullanıcı arabirimleri oluşturmasına yardımcı olan popüler bir bildirim kitaplığı <a href="https://beta.reactjs.org/">React'tir</a>.

### React: Bildirime dayalı bir UI kitaplığı

Bir geliştirici olarak, kullanıcı arayüzüne ne olmasını istediğinizi React'e söyleyebilirsiniz ve React, DOM'u sizin adınıza nasıl güncelleyeceğinizin adımlarını çözecektir.

Bir sonraki bölümde, React'i nasıl başlatabileceğinizi keşfedeceğiz.