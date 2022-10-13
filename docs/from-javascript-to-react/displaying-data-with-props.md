---
sidebar_position: 6
---

# Props ile Veri Görüntüleme


Şimdiye kadar, `<Header />` bileşeninizi yeniden kullanacak olsaydınız, aynı içeriği iki seferde de görüntülerdi.

```js
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

function HomePage() {
  return (
    <div>
      <Header />
      <Header />
    </div>
  );
}
```

Ama ya farklı bir metin iletmek istiyorsanız veya harici bir kaynaktan veri getirdiğiniz için bilgileri önceden bilmiyorsanız?

Normal HTML öğeleri, bu öğelerin davranışını değiştiren bilgi parçalarını iletmek için kullanabileceğiniz niteliklere sahiptir. Örneğin `<img>` bir öğenin `src` değiştirmek, gösterilen görüntüyü değiştirir. Bir `<a>` etiketinin href niteliğini değiştirmek, bağlantının hedefini değiştirir.

Aynı şekilde, React bileşenlerine özellik olarak bilgi parçalarını iletebilirsiniz. Bunlara `props` denir.

<img src="https://nextjs.org/static/images/learn/foundations/props.png"/>

JavaScript işlevine benzer şekilde, bileşenin davranışını veya ekrana işlendiğinde görünür şekilde gösterilenleri değiştiren özel argümanları (veya destekleri) kabul eden bileşenler tasarlayabilirsiniz. Ardından, bu aksesuarları ana bileşenlerden alt bileşenlere aktarabilirsiniz.

``
Not: React'te veriler bileşen ağacından aşağı akar. Buna tek yönlü veri akışı denir. Bir sonraki bölümde tartışılacak olan durum, props olarak ebeveynden alt bileşenlere geçirilebilir.
``

### Props Kullanma

`HomePage` componentine, `Header` componentine `title` propsu geçebilirsiniz, tıpkı HTML de attributes geçtiğiniz gibi:

```js
// function Header() {
//   return <h1>Develop. Preview. Ship. 🚀</h1>
// }

function HomePage() {
  return (
    <div>
      <Header title="React 💙" />
    </div>
  );
}

// ReactDOM.render(<HomePage />, app)
```

Ve Header alt bileşeni, bu özellikleri ilk props parametresi olarak kabul edebilir:

```js
function Header(props) {
//   return <h1>Develop. Preview. Ship. 🚀</h1>
// }

// function HomePage() {
//   return (
//     <div>
//       <Header title="React 💙" />
//     </div>
//   )
// }

// ReactDOM.render(<HomePage />, app)

```

Eğer `console.log()` kullanırsanız obje olarak `title` parametresini görebilirsiniz.

```js
function Header(props) {
    console.log(props) // { title: "React 💙" }
//   return <h1>React 💙</h1>
// }

// function HomePage() {
//   return (
//     <div>
//       <Header title="React 💙" />
//     </div>
//   )
// }

// ReactDOM.render(<HomePage />, app)
```

Props bir nesne olduğundan, işlev parametrelerinizin içindeki props değerlerini açıkça adlandırmak için nesne yok etmeyi kullanabilirsiniz:

```js
function Header({ title }) {
    console.log(title) // "React 💙"
//  return <h1>React 💙</h1>
// }

// function HomePage() {
//   return (
//     <div>
//       <Header title="React 💙" />
//     </div>
//   )
// }

// ReactDOM.render(<HomePage />, app)
```

Ardından etiketin içeriğini `<h1>` başlık değişkeninizle değiştirebilirsiniz.

```js
function Header({ title }) {
  console.log(title);
  return <h1>title</h1>;
}
```

Projenizi tarayıcıda açarsanız, gerçek `title` kelimesini görüntülediğini göreceksiniz. Bunun nedeni, React'in DOM'a düz bir metin dizesi oluşturmayı düşündüğünüzü düşünmesidir.

Bunun bir JavaScript değişkeni olduğunu React'e göstermenin bir yoluna ihtiyacınız var.

### JSX'te Değişkenleri Kullanma

Tanımladığınız değişkeni kullanmak için, doğrudan JSX işaretlemenizin içine düzenli JavaScript yazmanıza izin veren özel bir JSX sözdizimi olan küme parantezlerini kullanabilirsiniz. `{}`

```js
// function Header({title}) {
//  console.log(title)
return <h1>{title}</h1>;
// }
```

Kıvrımlı parantezleri "JSX arazisi" içindeyken "JavaScript arazisine" girmenin bir yolu olarak düşünebilirsiniz. Kıvrımlı parantezler içine herhangi bir JavaScript ifadesi (tek bir değer olarak değerlendirilen bir şey) ekleyebilirsiniz . Örneğin:

1. Nokta gösterimli bir nesne özelliği .

```js
function Header(props) {
  return <h1>{props.title}</h1>;
}
```

2. Bir şablon değişmezi:

```js
function Header({ title }) {
  return <h1>{`Cool ${title}`}</h1>;
}
```

3. Bir işlevin döndürülen değeri.

```js
function createTitle(title) {
  if (title) {
    return title;
  } else {
    return 'Default title';
  }
}

function Header({ title }) {
  return <h1>{createTitle(title)}</h1>;
}
```

4. Veya üçlü operatörler.

```js
function Header({ title }) {
  return <h1>{title ? title : 'Default Title'}</h1>;
}
```


Artık herhangi bir dizeyi başlık desteğinize iletebilirsiniz ve bileşeninizdeki varsayılan durumu üçlü operatörle hesaba kattığınız için, bir başlık desteğini bile geçemezsiniz:

```js
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}

function Page() {
  return (
    <div>
      <Header />
    </div>
  );
}
```

Bileşeniniz artık uygulamanızın farklı bölümlerinde yeniden kullanabileceğiniz genel bir başlık desteğini kabul ediyor. Tek yapmanız gereken başlığı değiştirmek:

```js
function Page() {
  return (
    <div>
      <Header title="React 💙" />
      <Header title="A new title" />
    </div>
  );
}
```

### Listeler arasında yineleme

Liste olarak göstermeniz gereken verilere sahip olmak yaygındır. Verilerinizi işlemek ve stil olarak aynı olan ancak farklı bilgi parçalarını içeren UI öğeleri oluşturmak için dizi yöntemlerini kullanabilirsiniz.

`HomePage` Bileşeninize bir dizi ad ekleyin:

```js
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
    </div>
  );
}
```

Ardından, dizi üzerinde yineleme yapmak için `array.map()` yöntemi kullanabilir ve bir adı bir liste öğesine eşlemek için bir ok(Arrow) işlevi kullanabilirsiniz:

```js
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

"JavaScript" ve "JSX" alanına girip çıkmak için küme parantezlerini nasıl kullandığınıza dikkat edin.

Bu kodu çalıştırırsanız, React bize eksik bir `key` prop hakkında bir uyarı verecektir. Bunun nedeni, React'in DOM'da hangi öğelerin güncelleneceğini bilmesi için bir dizideki öğeleri benzersiz bir şekilde tanımlayacak bir şeye ihtiyaç duymasıdır.

Şu anda benzersiz oldukları için adları şimdilik kullanabilirsiniz, ancak benzersiz olduğu garanti edilen bir öğe kimliği gibi bir şey kullanmanız önerilir.

```js
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

Bir sonraki bölümde, durum ve React'te kullanıcı olaylarını nasıl dinleyeceğiniz hakkında daha fazla bilgi edineceksiniz.