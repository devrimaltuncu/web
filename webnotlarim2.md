
1. **HTTP(S) Nedir? (HyperText Transfer Protocol)

HTTP, 1989-1991 yılları arasında Tim Berners-Lee ve ekibi tarafından geliştirilen, bir web sitesini her görüntülediğinizde kullanılan şeydir. HTTP, ister HTML, Resimler, Videolar, vb. olsun, web sayfası verilerinin iletilmesi, web sunucularıyla iletişim kurmak için kullanılan kurallar kümesidir.

HTTPS, HTTP'nin güvenli sürümüdür. HTTPS verileri şifrelenmiştir, bu nedenle yalnızca insanların aldığınız ve gönderdiğiniz verileri görmesini engellemekle kalmaz, aynı zamanda doğru web sunucusuyla konuştuğunuza ve onu taklit eden bir şey olmadığına dair size güvence verir.

HTTP ne anlama geliyor? HyperText Transfer Protocol
HTTPS'deki S ne anlama geliyor? Secure

2. **Talepler ve Yanıtlar

Bir web sitesine eriştiğimizde, tarayıcınızın HTML, Resimler gibi varlıklar için bir web sunucusuna istekte bulunması ve yanıtları indirmesi gerekecektir. Bundan önce, tarayıcıya bu kaynaklara nasıl ve nereden erişeceğini özellikle söylemeniz gerekir, URL'lerin yardımcı olacağı yer burasıdır.

2a. **URL Nedir? (Uniform Resource Locator)

Bir URL, ağırlıklı olarak internetteki bir kaynağa nasıl erişileceğine dair bir talimattır. URL'in tüm özellikleri (her istekte tüm özellikleri kullanılmaz):

Scheme  - HTTP, HTTPS, FTP (File Transfer Protocol) gibi kaynağa erişmek için hangi protokolün kullanılacağını bildirir.

User - Bazı hizmetler oturum açmak için kimlik doğrulaması gerektirir, oturum açmak için URL'e bir kullanıcı adı ve şifre girebilirsiniz.

Host - Erişmek istediğiniz sunucunun alan adı veya IP adresi.

Port - Bağlanacağınız port, genellikle HTTP için 80 ve HTTPS için 443, ancak bu, 1 - 65535 arasında herhangi bir portta barındırılabilir.

Path - Erişmeye çalıştığınız kaynağın dosya adı veya konumu.

Query String - İstenen yola gönderilebilen fazladan bilgi bitleri. Örneğin, /blog?id=1, blog pathine 1 idsine sahip blog makalesini almak istediğinizi söyler.

Fragment - Bu, istenen gerçek sayfadaki bir konuma yapılan bir referanstır. Bu, genellikle uzun içeriğe sahip sayfalar için kullanılır ve sayfanın belirli bir bölümü doğrudan ona bağlı olabilir, bu nedenle kullanıcı sayfaya erişir erişmez kullanıcı tarafından görüntülenebilir.

2b. **Talepte Bulunmak

Sadece bir satır "GET / HTTP/1.1" ile bir web sunucusuna istek yapmak mümkündür. Ancak çok daha zengin bir web deneyimi için başka verileri de göndermeniz gerekecek. Bu diğer veriler, Headers adı verilen şekilde gönderilir; burada headers, iletişim kurduğunuz web sunucusuna verilmek üzere fazladan bilgi içerir.

Örnek Talep:

```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/
```

Her satır detaylı olarak:

Satır 1 - Bu istek, GET yöntemini  gönderiyor, / ile ana sayfayı istiyor ve web sunucusuna HTTP protokolü sürüm 1.1'i kullandığımızı söylüyor.
Satır 2 - Web sunucusuna tryhackme.com web sitesini istediğimizi söylüyoruz.
Satır 3 - Web sunucusuna 87. Sürüm Firefox tarayıcısını kullandığımızı söylüyoruz.
Satır 4 - Web sunucusuna bizi buna yönlendiren web sayfasının https://tryhackme.com olduğunu söylüyoruz.
Satır 5 - HTTP istekleri, web sunucusuna isteğin bittiğini bildirmek için her zaman boş satırla biter.

Örnek Yanıt:

```http
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
<head>
    <title>TryHackMe</title>
</head>
<body>
    Welcome To TryHackMe.com
</body>
</html>
```

Her satır detaylı olarak:

Satır 1 - HTTP 1.1, sunucunun kullandığı HTTP protokolünün sürümüdür ve ardından bu durumda isteğin başarıyla tamamlandığını bize bildiren HTTP Durum Kodu "200 Ok" gelir.
Satır 2 - Web sunucusu yazılımını ve sürüm numarasını söyler.
Satır 3 - Web sunucusunun geçerli tarihi, saati ve saat dilimi.
Satır 4 - Content-Type başlığı, müşteriye HTML, resimler, videolar, PDF, XML gibi ne tür bilgilerin gönderileceğini söyler.
Satır 5 - Content-Length, müşteriye yanıtın ne kadar sürdüğünü söyler, bu şekilde hiçbir verinin eksik olmadığını doğrulayabiliriz.
Satır 6 - HTTP yanıtı, HTTP yanıtının sonunu onaylamak için boş bir satır içerir.
Satır 7-14 - İstenen bilgiler, bu örnekte ana sayfa.

Yukarıdaki örnekte hangi HTTP protokolü kullanılıyor? HTTP/1.1
Hangi yanıt headerı, tarayıcıya ne kadar veri beklemesi gerektiğini söyler? Content-Length

3. **HTTP Yöntemleri

HTTP yöntemleri, istemcinin bir HTTP isteği yaparken amaçlanan eylemi göstermesinin bir yoludur. Pek çok yöntem vardır, ancak çoğunlukla GET ve POST yöntemiyle ilgileneceksiniz.

GET Request - Bir web sunucusundan bilgi almak için kullanılır.
POST Request - Web sunucusuna veri göndermek ve potansiyel olarak yeni kayıtlar oluşturmak için kullanılır.
PUT Request - Bilgileri güncellemek için bir web sunucusuna veri göndermek için kullanılır.
DELETE Request - Bir web sunucusundan bilgi/kayıt silmek için kullanılır.

Yeni bir kullanıcı hesabı oluşturmak için hangi yöntem kullanılır? POST
E-posta adresinizi güncellemek için hangi yöntem kullanılır? PUT
Hesabınıza yüklediğiniz bir resmi kaldırmak için hangi yöntem kullanılır? DELETE
Bir haber makalesini görüntülemek için hangi yöntem kullanılır? GET

4. **HTTP Durum Kodları

Önceki kısımda, bir HTTP sunucusu yanıt verdiğinde, ilk satırın her zaman istemciyi isteğinin sonucu ve potansiyel olarak nasıl ele alınacağı konusunda bilgilendiren bir durum kodu içerdiğini öğrendik. Bu durum kodları 5 farklı aralığa ayrılabilir:

100-199 - Information Response - Müşteriye talebinin ilk kısmının kabul edildiğini ve talebinin geri kalanını göndermeye devam etmesi gerektiğini bildirmek için gönderilir. Bu kodlar artık çok yaygın değil.

200-299 - Success - Müşteriye isteğinin başarılı olduğunu söylemek için kullanılır.

300-399 - Redirection - Müşterinin isteğini başka bir kaynağa yönlendirmek için kullanılır. Bu, farklı bir web sayfasına veya tamamen farklı bir web sitesine olabilir.

400-499 - Client Errors - İstemciye isteğinde bir hata olduğunu bildirmek için kullanılır.

500-599 - Server Errors - Sunucu tarafında meydana gelen hatalar için ayrılmıştır ve genellikle sunucunun isteği işleme koymasıyla ilgili oldukça büyük bir sorun olduğunu gösterir.

4a. **Yaygın HTTP Durum Kodları

Pek çok farklı HTTP durum kodu vardır ve buna uygulamaların kendi kodlarını tanımlayabilmesi dahil değildir. Karşılaşılması muhtemel en yaygın HTTP yanıtları:

200 - OK - İstek başarıyla tamamlandı.

201 - Created - Bir kaynak oluşturuldu (örneğin, yeni bir kullanıcı veya yeni blog gönderisi).

301 - Permanent Redirect - Müşterinin tarayıcısını yeni bir web sayfasına yönlendirir veya arama motorlarına sayfanın başka bir yere taşındığını ve oraya bakmalarını söyler.

302 - Temporary Redirect - Permanen Redirect'e benzer, ancak bu yalnızca geçici bir değişikliktir ve yakın gelecekte tekrar değiştirilebilir.

400 - Bad Request - Tarayıcıya isteklerinde bir şeylerin yanlış veya eksik olduğunu söyler. Bu bazen, talep edilen web sunucusu kaynağı, istemcinin göndermediği belirli bir parametre bekliyorsa kullanılabilir.

401 - Not Authorised - Genellikle bir kullanıcı adı ve parola ile web uygulamasıyla yetkilendirme yapana kadar bu kaynağı görüntülemenize izin verilmiyor.

403 - Forbidden - Giriş yapsanız da yapmasanız da bu kaynağı görüntüleme izniniz yok.

405 - Method Not Allowed - Kaynak bu yöntem isteğine izin vermiyor, örneğin, /create-account kaynağına bir POST isteği beklerken bir GET isteği gönderirseniz.

404 - Page Not Found - İstediğiniz sayfa/kaynak mevcut değil.

500 - Internal Service Error - Sunucu, isteğinizle ilgili olarak nasıl doğru bir şekilde ele alınacağını bilmediği bir tür hatayla karşılaştı.

503 - Service Unavailable - Bu sunucu, aşırı yüklendiği veya bakım nedeniyle kapalı olduğu için isteğinizi karşılayamıyor.

Yeni bir kullanıcı veya blog gönderisi makalesi oluşturduysanız hangi yanıt kodunu alabilirsiniz? 201
Var olmayan bir sayfaya erişmeye çalıştığınızda hangi yanıt kodunu alabilirsiniz? 404
Web sunucusu veri tabanına erişemezse ve uygulama çökerse hangi yanıt kodunu alabilirsiniz? 503
Önce oturum açmadan profilinizi düzenlemeye çalışırsanız hangi yanıt kodunu alabilirsiniz? 401

5. **Headerlar

Headerlar, istekte bulunurken web sunucusuna gönderebileceğiniz ek veri parçalarıdır.

5a. **Yaygın Talep Headerları

Bunlar, istemciden (genellikle tarayıcınızdan) sunucuya gönderilen headerlardır.

Host - Bazı web sunucuları birden çok web sitesini barındırır, bu nedenle host headerları sağlayarak hangisine ihtiyacınız olduğunu söyleyebilirsiniz, aksi takdirde sunucu için yalnızca varsayılan web sitesini alırsınız.

User-Agent - Tarayıcı yazılımınız ve sürüm numaranızdır. Web sunucusuna tarayıcı yazılımınızın web sitesini tarayıcınız için uygun şekilde biçimlendirmesine yardımcı olduğunu söyler ve ayrıca HTML, CSS ve JavaScript'in bazı öğeleri yalnızca belirli tarayıcılarda bulunur.

Content-Length - Form gibi bir web sunucusuna veri gönderirken, Content-Length web sunucusuna web içeriğinde ne kadar veri bekleyeceğini söyler. Bu şekilde sunucu, herhangi bir verinin eksik olmadığından emin olabilir.

Accept-Encoding - Web sunucusuna, tarayıcının ne tür sıkıştırma yöntemlerini desteklediğini söyler, böylece veriler internet üzerinden iletilmek üzere daha küçük hale getirilenilir.

Cookie - Bilgilerinizi hatırlamaya yardımcı olmak için sunucuya gönderilen veriler.

5b. **Yaygın Yanıt Headerları

Bunlar, bir talepten sonra sunucudan istemciye döndürülen headerlardır.

Set-Cookie - Her talepte web sunucusuna geri gönderilen, depolanacak bilgiler.

Cache-Control - Yanıt içeriğinin, tekrar istemeden önce tarayıcının önbelleğinde ne kadar süreyle saklanacağı.

Content-Type - Müşteriye ne tür verilerin döndürüldüğünü söyler, yani HTML, CSS, JavaScript, Görüntüler, PDF, Video vb. Content-Type hederını kullanan tarayıcı, verileri nasıl işleyeceğini bilir.

Content-Encoding - Verileri internet üzerinden gönderirken daha küçük hale getirmek için hangi sıkıştırma yöntemi kullanılmıştır.

Hangi header web sunucusuna hangi tarayıcının kullanıldığını söyler? User-Agent
Hangi header, tarayıcıya ne tür verilerin döndürüldüğünü söyler? Content-Type
Web sunucusuna hangi web sitesinin talep edildiğini hangi header bildirir? Host

6. **Cookieler

Bunlar yalnızca bilgisayarınızda depolanan küçük veri parçalarıdır. Bir web sunucusundan "Set-Cookie" headerı aldığınızda kaydedilir. Daha sonra yaptığınız her istekte cookie verilerini web sunucusuna geri gönderirsiniz. HTTP durum bilgisiz olduğundan (önceki isteklerinizi takip etmez), web sunucusuna kim olduğunuzu, web sitesi için bazı kişisel ayarları veya web sitesini daha önce ziyaret edip etmediğinizi hatırlatmak için cookieler kullanılabilir.
Cookieler birçok amaç için kullanılabilir, ancak en yaygın olarak web sitesi kimlik doğrulaması için kullanılır. Cookie değeri genellikle şifreyi görebileceğiniz bir açık metin dizesi değil, bir belirteç (insanlar tarafından kolayca tahmin edilemeyen benzersiz gizli kod) olacaktır.

6a. **Cookieleri Görüntüleme

Tarayıcınızdaki geliştirici araçlarını kullanarak tarayıcınızın bir web sitesine hangi cookieleri gönderdiğini kolayca görüntüleyebilirsiniz. 

Çerezleri bilgisayarınıza kaydetmek için hangi başlık kullanılır? Set-Cookie
