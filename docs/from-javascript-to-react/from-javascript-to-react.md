---
sidebar_position: 0
---

# JavaScript'ten React'e

### Kullanıcı Arayüzlerini Oluşturma

React'in nasıl çalıştığını anlamak için öncelikle tarayıcıların etkileşimli kullanıcı arayüzleri (UI) oluşturmak için kodunuzu nasıl yorumladığına dair temel bir anlayışa ihtiyacımız var.

Bir kullanıcı bir web sayfasını ziyaret ettiğinde, sunucu tarayıcıya şuna benzeyen bir HTML dosyası döndürür:

<img src="https://nextjs.org/static/images/learn/foundations/html-to-dom.png"/>

Tarayıcı daha sonra HTML'yi okur ve Belge Nesne Modelini (DOM) oluşturur.

### DOM nedir?

DOM, HTML öğelerinin nesne temsilidir. Kodunuz ve kullanıcı arayüzü arasında bir köprü görevi görür ve ebeveyn ve çocuk ilişkileri ile ağaç benzeri bir yapıya sahiptir.

<img src="https://nextjs.org/static/images/learn/foundations/dom-to-ui.png"/>

Kullanıcı olaylarını dinlemek ve kullanıcı arabirimindeki belirli öğeleri seçerek, ekleyerek, güncelleyerek ve silerek <a href="https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents">DOM'yi işlemek için</a> DOM yöntemlerini ve JavaScript gibi bir programlama dilini kullanabilirsiniz. DOM manipülasyonu, yalnızca belirli öğeleri hedeflemenize değil, aynı zamanda stillerini ve içeriklerini değiştirmenize de olanak tanır.

Bir sonraki bölümde JavaScript ve DOM yöntemlerini nasıl kullanabileceğinizi görelim.
