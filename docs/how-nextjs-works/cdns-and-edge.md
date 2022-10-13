---
sidebar_position: 10
title: CDN'ler ve Edge
---


### Ağ nedir?

Uygulama kodunuzun nerede saklandığını ve ağa dağıtıldıktan sonra çalıştırıldığını bilmek faydalıdır. Ağı, kaynakları paylaşabilen bağlantılı bilgisayarlar (veya sunucular) olarak düşünebilirsiniz. Bir Next.js uygulaması olması durumunda, uygulama kodunuz kaynak sunuculara , İçerik Dağıtım Ağlarına (CDN'ler) ve Edge'e dağıtılabilir . Bunların her birinin ne olduğunu görelim:

### Köken Sunucular(Origin Server)

Daha önce tartıştığımız gibi, sunucu, uygulama kodunuzun orijinal sürümünü depolayan ve çalıştıran ana bilgisayarı ifade eder.

Bu sunucuyu CDN sunucuları ve Edge sunucuları gibi uygulama kodunun dağıtılabileceği diğer yerlerden ayırt etmek için Origin terimini kullanıyoruz.

Origin sunucusu bir istek aldığında, yanıt göndermeden önce bazı hesaplamalar yapar. Bu hesaplama çalışmasının sonucu bir CDN'ye (İçerik Dağıtım Ağı) taşınabilir.

### İçerik Dağıtım Ağı

CDN'ler, statik içeriği (HTML ve görüntü dosyaları gibi) dünyanın çeşitli yerlerinde depolar ve istemci ile kaynak sunucu arasına yerleştirilir. Yeni bir istek geldiğinde, kullanıcıya en yakın CDN konumu önbelleğe alınan sonuçla yanıt verebilir.

<img src="https://nextjs.org/static/images/learn/foundations/cdn.png"/>

Bu, hesaplamanın her istekte gerçekleşmesi gerekmediğinden, Origin üzerindeki yükü azaltır. Ayrıca, yanıt coğrafi olarak kendilerine daha yakın bir konumdan geldiği için kullanıcı için daha hızlı hale getirir.

Next.js'de, önceden oluşturma önceden yapılabildiğinden, CDN'ler işin statik sonucunu depolamak için çok uygundur ve içerik dağıtımını daha hızlı hale getirir.

### The Edge

Edge, ağın kullanıcıya en yakın olan kenarı ( veya kenarı ) için genelleştirilmiş bir kavramdır . CDN'ler, ağın kenarında (kenarında) statik içerik depoladıkları için "Edge"nin bir parçası olarak kabul edilebilir.

CDN'lere benzer şekilde, Edge sunucuları dünya çapında birden çok konuma dağıtılır. Ancak statik içerik depolayan CDN'lerin aksine, bazı Edge sunucuları kod çalıştırabilir.

Bu, kullanıcıya daha yakın olan Edge'de hem önbelleğe alma hem de kod yürütmenin yapılabileceği anlamına gelir.

Edge'de kod çalıştırarak, geleneksel olarak istemci tarafında veya sunucu tarafında yapılan çalışmaların bir kısmını Edge'e taşıyabilirsiniz. Bu, uygulamanızı daha performanslı hale getirebilir, çünkü istemciye gönderilen kod miktarını azaltır ve kullanıcının isteğinin bir kısmının orijin sunucusuna kadar gitmesi gerekmez - böylece gecikmeyi azaltır.

Next.js'de, Edge'de Middleware ile ve yakında React Server Components ile kod çalıştırabilirsiniz.