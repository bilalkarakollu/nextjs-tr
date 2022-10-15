---
sidebar_position: 1
---


# Kurmak

Öncelikle geliştirme ortamınızın hazır olduğundan emin olalım.

- Node.js kurulu değilse <a href="https://nodejs.org/en/">buradan kurun</a>. Node.js sürüm 10.13 veya daha yenisine ihtiyacınız olacak.
- Bu eğitim için kendi metin düzenleyicinizi ve terminal uygulamanızı kullanacaksınız.

### Bir Next.js uygulaması oluşturun

Bir Next.js uygulaması oluşturmak için, uygulamayı oluşturmak istediğiniz dizine terminalinizi açın ve aşağıdaki komutu çalıştırın:

```js
npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/learn-starter"
```

### Geliştirme sunucusunu çalıştırın

Artık `nextjs-blog` adında yeni bir dizininiz var. İçeri girelim ``cd``:


```js
cd nextjs-blog
```

Ardından, aşağıdaki komutu çalıştırın:

```js
npm run dev
```

Bu, Next.js uygulamanızın "geliştirme sunucusunu" (bundan daha sonra bahsedeceğiz) 3000 numaralı bağlantı noktasında başlatır.

Çalışıp çalışmadığını kontrol edelim. Tarayıcınızdan http://localhost:3000'i açın.
