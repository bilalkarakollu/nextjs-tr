---
sidebar_position: 2
---

# İki Ön İşleme Biçimi

Next.js'nin iki ön işleme biçimi vardır: Statik Oluşturma(Static) ve Sunucu Tarafı(Server Side) İşleme. Fark, bir sayfa için HTML oluşturduğundadır.

- Statik Oluşturma, HTML'yi derleme zamanında oluşturan ön işleme yöntemidir. Önceden oluşturulmuş HTML daha sonra her istekte yeniden kullanılır.
- Sunucu Tarafı İşleme(Server Side), her istekte HTML oluşturan ön işleme yöntemidir.


<img src="https://nextjs.org/static/images/learn/data-fetching/static-generation.png"/>

<br/>
<br/>

<img src="https://nextjs.org/static/images/learn/data-fetching/server-side-rendering.png"/>

### Per-page Basis

Daha da önemlisi, Next.js, her sayfa için hangi ön işleme formunun kullanılacağını seçmenize izin verir. Çoğu sayfa için Statik Oluşturma'yı ve diğerleri için Sunucu Tarafı İşleme'yi kullanarak bir "karma" Next.js uygulaması oluşturabilirsiniz.

<img src="https://nextjs.org/static/images/learn/data-fetching/per-page-basis.png"/>

### Statik Oluşturma ve Sunucu Tarafı Oluşturma Ne Zaman Kullanılır ?

Sayfanız bir kez oluşturulabilir ve CDN tarafından sunulabilir, bu da onu her istekte bir sunucunun sayfayı oluşturmasından çok daha hızlı hale getirir.

Statik Oluşturma'yı aşağıdakiler dahil birçok sayfa türü için kullanabilirsiniz:

- Pazarlama sayfaları
- Blog gönderileri
- E-ticaret ürün listelemeleri
- Yardım ve belgeler

Kendinize şunu sormalısınız: "Bu sayfayı bir kullanıcının isteğinden önce önceden oluşturabilir miyim?" Cevabınız evet ise Static Generation seçmelisiniz.

Öte yandan, kullanıcının isteğinden önce bir sayfayı önceden oluşturamazsanız Statik Oluşturma iyi bir fikir değildir. Belki sayfanız sık güncellenen verileri gösteriyor ve sayfa içeriği her istekte değişiyor.

Bu durumda Server-side Rendering kullanabilirsiniz. Daha yavaş olacak, ancak önceden oluşturulmuş sayfa her zaman güncel olacaktır. Veya ön oluşturmayı atlayabilir ve sık güncellenen verileri doldurmak için istemci tarafı JavaScript'i kullanabilirsiniz.


### Statik Üretime Odaklanacağız

 Bu derste, Statik Üretime odaklanacağız. Bir sonraki sayfada, data ile ve data olmadan Statik Üretim hakkında konuşacağız.

