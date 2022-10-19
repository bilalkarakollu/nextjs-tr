---
sidebar_position: 5
---

# İstek Zamanında Veri Alma

Verileri derleme zamanı yerine istek zamanında getirmeniz gerekiyorsa, Sunucu Tarafı Oluşturmayı deneyebilirsiniz:

<img src="https://nextjs.org/static/images/learn/data-fetching/server-side-rendering-with-data.png"/>


Sunucu Tarafı İşleme'yi kullanmak `getServerSideProps` için `getStaticProps` sayfanızdan dışa aktarmanız gerekir.

### getServerSideProps kullanma

İşte `getServerSideProps` başlangıç ​​kodu . Blog örneğimiz için gerekli değil, bu yüzden uygulamayacağız.

```js
export async function getServerSideProps(context) {
  return {
    props: {
      // props for your component
    },
  };
}
```

İstek zamanında çağrıldığından, `getServerSideProps` parametresi `(context)` isteğe özel parametreleri içerir.

`getServerSideProps` Yalnızca verileri istek zamanında alınması gereken bir sayfayı önceden oluşturmanız gerekiyorsa kullanmalısınız. İlk bayta ( TTFB ) kadar geçen süre, sunucunun her istekte sonucu hesaplaması gerektiğinden daha yavaş olacaktır ve sonuç, ekstra yapılandırma olmadan bir CDN `getStaticProps` tarafından önbelleğe alınamaz.

### İstemci Tarafı Oluşturma


Verileri önceden oluşturmanız gerekmiyorsa, aşağıdaki stratejiyi de kullanabilirsiniz (İstemci Tarafı Oluşturma olarak adlandırılır):

- Sayfanın harici veri gerektirmeyen kısımlarını statik olarak oluşturun (önceden oluşturun).
- Sayfa yüklendiğinde, JavaScript kullanarak istemciden harici verileri alın ve kalan bölümleri doldurun.

<img src="https://nextjs.org/static/images/learn/data-fetching/client-side-rendering.png"/>

Bu yaklaşım, örneğin, kullanıcı kontrol paneli sayfaları için iyi çalışır. Pano özel, kullanıcıya özel bir sayfa olduğundan, SEO alakalı değildir ve sayfanın önceden oluşturulmasına gerek yoktur. Veriler sık ​​sık güncellenir, bu da istek zamanında veri alınmasını gerektirir.

### SWR

Next.js'nin arkasındaki ekip, veri almak için SWR adlı bir React kancası oluşturdu. İstemci tarafında veri alıyorsanız bunu kesinlikle öneririz. Önbelleğe alma, yeniden doğrulama, odak izleme, aralıklarla yeniden getirme ve daha fazlasını yönetir. Ayrıntıları burada ele almayacağız, ancak işte örnek bir kullanım:


```js
import useSWR from 'swr';

function Profile() {
  const { data, error } = useSWR('/api/user', fetch);

  if (error) return <div>failed to load</div>;
  if (!data) return <div>loading...</div>;
  return <div>hello {data.name}!</div>;
}
```


Daha fazla bilgi edinmek için SWR belgelerine bakın.

