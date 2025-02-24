---
sidebar_position: 7
---

# Durumla Etkileşim Ekleme

React'in durum(state) ve olay işleyicilerle(event handlers) etkileşim eklememize nasıl yardımcı olduğunu keşfedelim.

Örnek olarak, `HomePage` bileşeninizin içinde bir beğen düğmesi oluşturalım. İlk olarak, `return()` ifadenin içine bir düğme öğesi ekleyin:

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

            <button>Like</button>
        </div>
    );
}
```

### Olayları Dinleme (Listening to Events)

Butonun tıklandığında bir şeyler yapmasını sağlamak için `onClick` kolaydan faydalanabilirsiniz.

```js
function HomePage() {
    // ...
    return (
        <div>
            {/* ... */}
            <button onClick={}>Like</button>
        </div>
    );
}
```

React'te olay adları camelCased'dir. Olay `onClick`, kullanıcı etkileşimine yanıt vermek için kullanabileceğiniz birçok olası olaydan biridir. Örneğin, `onChange` giriş alanları veya `onSubmit` formlar için kullanabilirsiniz.

### Olayları İşleme

Olayları tetiklendikleri zaman "işlemek" için bir işlev tanımlayabilirsiniz. Çağrılan return ifadesinden önce bir işlev oluşturun `handleClick()`:

```js
function HomePage() {
    // ...

    function handleClick() {
        console.log("increment like count")
    }

    return (
        <div>
            {/* ... */}
            <button onClick={}>Like</button>
        </div>
    )
}
```

Ardından, `onClick` olayı tetiklendiğinde `handleClick` işlevi çağırabilirsiniz:

```js
function HomePage() {
    //    ...
    function handleClick() {
        console.log('increment like count');
    }

    return (
        <div>
            {/* ... */}
            <button onClick={handleClick}>Like</button>
        </div>
    );
}
```

### Durum(State) ve Kancalar(Hooks)

<a href="https://reactjs.org/docs/hooks-intro.html">React'in hooks</a> adı verilen bir dizi işlevi vardır. Kancalar, bileşenlerinize durum gibi ek mantık eklemenize olanak tanır. Durumu, genellikle kullanıcı etkileşimi tarafından tetiklenen, zaman içinde değişen, kullanıcı arayüzünüzdeki herhangi bir bilgi olarak düşünebilirsiniz.


<img src="/img/learn/learn-state.jpeg"/>

Bir kullanıcının beğen düğmesini tıklama sayısını depolamak ve artırmak için state kullanabilirsiniz. Aslında, durumu yönetmek için React kancasının adı budur: `useState()`

```js
function HomePage() {
    React.useState();
}
```

`useState()` bir dizi döndürür ve dizi yok etmeyi kullanarak bileşeninizin içindeki bu dizi değerlerine erişebilir ve bunları kullanabilirsiniz:

```js
function HomePage() {
    const [] = React.useState();

    // ...
}
```

Dizideki ilk öğe, herhangi bir `value` şey adlandırabileceğiniz durumdur. Açıklayıcı bir ad vermeniz önerilir:

```js
function HomePage() {
    const [likes] = React.useState();

    // ...
}
```

Dizideki ikinci öğe update, değerin bir işlevidir. Güncelleme işlevine herhangi bir ad verebilirsiniz, ancak ön ekinin `set` ardından güncellemekte olduğunuz durum değişkeninin adının gelmesi yaygındır:

```js
function HomePage() {
    const [likes, setLikes] = React.useState();

    // ...
}
```

Ayrıca, state `likes` inizin başlangıç ​​değerini ekleme fırsatını da kullanabilirsiniz : sıfır.

```js
function HomePage() {
    const [likes, setLikes] = React.useState(0);
}
```

Ardından, bileşeninizin içindeki durum değişkenini kullanarak ilk durumun çalışıp çalışmadığını kontrol edebilirsiniz.

```js
function HomePage() {
    // ...
    const [likes, setLikes] = React.useState(0);

    return (
        // ...
        <button onClick={handleClick}>Like({likes})</button>
    );
}
```

Son olarak , `HomePage` bileşeninizde durum `setLikes` güncelleyici işlevinizi çağırabilirsiniz, onu daha önce tanımladığınız işlevin `handleClick()` içine ekleyelim:

```js
function HomePage() {
    // ...
    const [likes, setLikes] = React.useState(0);

    function handleClick() {
        setLikes(likes + 1);
    }

    return (
        <div>
            {/* ... */}
            <button onClick={handleClick}>Likes ({likes})</button>
        </div>
    );
}
```

Düğmeye tıklandığında `handleClick` fonksiyonu çağırılır `setLikes` da state'i +1 günceller.

### State Yönetimi

Bu, duruma yalnızca bir girişti ve React uygulamalarınızda durum ve veri akışını yönetme hakkında öğrenebileceğiniz daha çok şey var. Daha fazla bilgi edinmek için <a href="https://beta.reactjs.org/learn/adding-interactivity">React Documentation'daki</a> Etkileşim Ekleme ve <a href="https://beta.reactjs.org/learn/managing-state">Durumu Yönetme</a> bölümlerine göz atmanızı öneririz .