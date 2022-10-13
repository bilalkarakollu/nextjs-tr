---
sidebar_position: 1
---

# Geliştirme ve Üretim Ortamları

Ortamları, kodunuzun çalıştığı bağlam olarak düşünebilirsiniz.

Geliştirme sırasında uygulamayı yerel makinenizde oluşturuyor ve çalıştırıyorsunuz. Üretime geçme(Production), uygulamanızı kullanıcılar tarafından dağıtılmaya ve tüketilmeye hazır hale getirme sürecidir.

### Bu, Next.js için nasıl geçerlidir?

Next.js, bir uygulamanın hem geliştirme hem de üretim aşamaları için özellikler sağlar. Örneğin:

- Geliştirme aşamasında, Next.js, geliştirici ve uygulamayı oluşturma deneyimi için optimize eder. TypeScript ve ESLint entegrasyonu, Hızlı Yenileme ve daha fazlası gibi Geliştirici Deneyimini iyileştirmeyi amaçlayan özelliklerle birlikte gelir.
- Üretim aşamasında Next.js, son kullanıcılar ve uygulamayı kullanma deneyimlerini optimize eder. Kodu, performanslı ve erişilebilir hale getirmek için dönüştürmeyi amaçlar.

Her ortamın farklı düşünceleri ve hedefleri olduğundan, bir uygulamayı geliştirmeden üretime taşımak için yapılması gereken çok şey vardır. Örneğin, uygulama kodunun derlenmesi , paketlenmesi, küçültülmesi ve kod bölünmesi gerekir.

### Next.js Derleyicisi

Next.js, uygulamanızın üretime geçmesini kolaylaştırmak için bu kod dönüşümlerinin çoğunu ve temel altyapıyı yönetir.

Bu, Next.js'nin düşük seviyeli bir programlama dili olan Rust ile yazılmış bir derleyiciye ve derleme, küçültme, paketleme ve daha fazlası için kullanılabilecek bir platform olan SWC'ye sahip olması nedeniyle mümkün olmuştur.

Sonraki bölümlerde, bu dönüşümlerin her birinin ne olduğunu keşfedeceğiz.

