---
sidebar_position: 6
title: Kod Bölme nedir?
---

# Kod Bölme nedir?(Code Splitting)

Geliştiriciler genellikle uygulamalarını farklı URL'lerden erişilebilen birden çok sayfaya böler. Bu sayfaların her biri uygulamaya benzersiz bir giriş noktası olur.

Kod bölme, uygulama paketini her giriş noktasının gerektirdiği daha küçük parçalara bölme işlemidir. Amaç, yalnızca o sayfayı çalıştırmak için gereken kodu yükleyerek uygulamanın ilk yükleme süresini iyileştirmektir.

<img src="https://nextjs.org/static/images/learn/foundations/code-splitting.png"/>

Next.js, kod bölme için yerleşik desteğe sahiptir. Dizininizdeki her dosya `pages/`, derleme adımı sırasında otomatik olarak kendi JavaScript paketine bölünecektir.

Daha öte:

- Sayfalar arasında paylaşılan herhangi bir kod, daha fazla gezinme sırasında aynı kodun yeniden indirilmesini önlemek için başka bir pakete bölünür.
- İlk sayfa yüklendikten sonra Next.js, kullanıcıların gezinmesi muhtemel diğer sayfaların kodunu önceden yüklemeye başlayabilir.
- Dinamik içe aktarmalar, hangi kodun başlangıçta yüklendiğini manuel olarak ayırmanın başka bir yoludur.

