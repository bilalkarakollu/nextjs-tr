---
sidebar_position: 1
---

# Pre-rendering

Veri getirme hakkında konuşmadan önce, Next.js'deki en önemli kavramlardan biri hakkında konuşalım: Pre-rendering.

Varsayılan olarak, Next.js her sayfayı önceden işler. Bu, Next.js'nin her şeyi istemci tarafı JavaScript ile yapmak yerine önceden her sayfa için HTML oluşturduğu anlamına gelir. Ön işleme, daha iyi performans ve SEO ile sonuçlanabilir.

Oluşturulan her HTML, o sayfa için gerekli olan minimum JavaScript koduyla ilişkilendirilir. Bir sayfa tarayıcı tarafından yüklendiğinde, JavaScript kodu çalışır ve sayfayı tamamen etkileşimli hale getirir. (Bu işleme hidrasyon denir.)

### Ön işlemenin gerçekleştiğini kontrol edin

Aşağıdaki adımları uygulayarak ön işlemenin gerçekleşip gerçekleşmediğini kontrol edebilirsiniz:

- Tarayıcınızda JavaScript'i devre dışı bırakın (<a href="https://developers.google.com/web/tools/chrome-devtools/javascript/disable">burada Chrome'da nasıl yapılır</a>)
- <a href="https://next-learn-starter.vercel.app/">Bu sayfaya erişmeyi deneyin</a>.

Uygulamanızın JavaScript olmadan oluşturulduğunu görmelisiniz. Bunun nedeni, Next.js'nin uygulamayı statik HTML'ye önceden oluşturması ve JavaScript çalıştırmadan uygulama kullanıcı arayüzünü görmenize izin vermesidir.

Uygulamanız düz bir React.js uygulamasıysa (Next.js olmadan), önceden oluşturma yoktur, dolayısıyla JavaScript'i devre dışı bırakırsanız uygulamayı göremezsiniz. Örneğin:

- Tarayıcınızda JavaScript'i etkinleştirin ve <a href="https://create-react-template.vercel.app/">bu sayfaya göz atın</a>. Bu, <a href="https://create-react-app.dev/">Create React App</a> ile oluşturulmuş sade bir React.js uygulamasıdır.
- Şimdi JavaScript'i devre dışı bırakın ve aynı sayfaya tekrar erişin.
- Uygulamayı artık görmeyeceksiniz - bunun yerine "Bu uygulamayı çalıştırmak için JavaScript'i etkinleştirmeniz gerekiyor" diyecek. Bunun nedeni, uygulamanın statik HTML olarak önceden oluşturulmamış olmasıdır.

### Özet: Ön İşleme ve Ön İşleme Yok

İşte hızlı bir grafik özet:

<img src="https://nextjs.org/static/images/learn/data-fetching/pre-rendering.png"/>

<img src="https://nextjs.org/static/images/learn/data-fetching/no-pre-rendering.png"/>

Şimdi, Next.js'de iki ön işleme biçimi hakkında konuşalım.








