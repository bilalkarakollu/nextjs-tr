---
sidebar_position: 4
---

# getStaticProps Ayrıntıları

İşte bilmeniz gereken bazı temel bilgiler getStaticProps.

### Harici API veya Sorgu Veritabanını Getir


```js
export async function getSortedPostsData() {
  // Instead of the file system,
  // fetch post data from an external API endpoint
  const res = await fetch('..');
  return res.json();
}
```

Ayrıca veritabanını doğrudan sorgulayabilirsiniz:

```js
import someDatabaseSDK from 'someDatabaseSDK'

const databaseClient = someDatabaseSDK.createClient(...)

export async function getSortedPostsData() {
  // Instead of the file system,
  // fetch post data from a database
  return databaseClient.query('SELECT posts...')
}
```

Bu mümkündür çünkü getStaticPropsyalnızca sunucu tarafında çalışır . Asla istemci tarafında çalışmaz. Tarayıcı için JS paketine bile dahil edilmeyecek. Bu, tarayıcılara gönderilmeden doğrudan veritabanı sorguları gibi kod yazabileceğiniz anlamına gelir.

### Geliştirme ve Üretim

- Geliştirme aşamasında ( npm run devveya yarn dev), her istek üzerinegetStaticProps çalışır.


Derleme zamanında çalıştırılması gerektiği için, sorgu parametreleri veya HTTP üstbilgileri gibi yalnızca istek sırasında kullanılabilen verileri kullanamazsınız.

### Yalnızca Bir Sayfada İzin Verilir

`getStaticProps` yalnızca bir sayfadan dışa aktarılabilir. Sayfa dışı dosyalardan dışa aktaramazsınız.

Bu kısıtlamanın nedenlerinden biri, React'in sayfa oluşturulmadan önce gerekli tüm verilere sahip olması gerektiğidir.

### İstek Zamanında Veri Almam Gerekiyorsa Ne Olur?

Statik Oluşturma, derleme sırasında bir kez gerçekleştiğinden, sık sık güncellenen veya her kullanıcı isteğinde değişen veriler için uygun değildir.

Bu gibi durumlarda, verilerinizin değişebileceği durumlarda, Sunucu Tarafı İşleme'yi kullanabilirsiniz. Bir sonraki bölümde sunucu tarafı oluşturma hakkında daha fazla bilgi edinelim.

