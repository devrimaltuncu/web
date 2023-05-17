
1. **DNS Nedir?

DNS (Domain Name System), karmaşık sayıları hatırlamadan internetteki cihazlarla iletişim kurmamız için basit bir yol sağlar. İnternetteki her bilgisayarın IP adresi adı verilen iletişim kurmak için kendi benzersiz adresi vardır. Bir IP adresi, 0-255 arasında değişen ve bir noktayla ayrılmış 4 basamaktan oluşur. Bir web sitesini ziyaret etmek istediğinizde, bu karmaşık sayı dizisini hatırlamak tam olarak uygun değildir ve DNS'in yardımcı olabileceği yer burasıdır.

DNS ne anlama geliyor? Domain Name System

2. **Domain Hiyerarşisi

**TLD (Top-Level Domain)

TLD, bir alan adının en sağdaki kısmıdır. Örneğin google.com TLD'si .com'dur. İki tür TLD vardır, gTLD (Generic Top Level Domain) ve ccTLD (Country Code Top Level Domain). gTLD, kullanıcıya alan adının amacını anlatmak içindir; örneğin .com ticari amaçlar için, .org bir kuruluş için, .edu eğitim ve .gov devlet içindir. ccTLD coğrafi bilgiler içindir; Kanada merkezli siteler için .ca, Birleşik Krallık için .co.uk vb. Artan talepler nedeniyle .online, .club, .biz ve daha bir çok yeni gTLD akışı bulunmaktadır.

**Second-Level Domain

Örnek olarak google.com'u ele alırsak, .com kısmı TLD ve google kısmı ise Second Level Domain'dir. Bir domaini kaydederken, SLD 63 karakter + TLD ile sınırlıdır ve yalnızca a-z, 0-9 ve tire kullanılabilir (tire ile başlayamaz, bitemez ve ardışık tireler bulunamaz).

**Subdomain

SLD'nin sol tarafında, bir noktayla ayrılmış subdomain bulunur; örneğin admin.tryhackme.com'da admin kısmı subdomaindir. Bir subdomain, SLD ile aynı oluşturma kısıtlamalarına sahiptir, 63 karakter + TLD ile sınırlıdır ve yalnızca a-z, 0-9 ve tire kullanılabilir (tire ile başlayamaz, bitemez ve ardışık tireler bulunamaz). jupiter.servers.tryhackme.com gibi daha uzun adlar oluşturmak için noktalarla bölünmüş birden çok subdomain kullanılabilir. Ancak uzunluk 253 karakter veya daha az tutulmalıdır. Domain için oluşturulabilecek subdomain sayısında bir sınırlama yoktur.

What is the maximum length of a subdomain? 63
Karakterlerden hangisi bir alt alan adında kullanılamaz ( 3 b _ - )? _
Bir alan adının maksimum uzunluğu nedir? 253
.co.uk ne tür bir TLD'dir? ccTLD

3. **Kayıt Türleri

DNS yalnızca web siteleri için değildir ve birden çok DNS kayıt türü mevcuttur. En yaygın olanlardan bazıları:

**A Record

Bu kayıtlar IPv4 adreslerine çözümlenir, örneğin 104.26.10.229.

**AAAA Record

Bu kayıtlar IPv6 adreslerine çözümlenir, örneğin 2606:2700:20::681a:be5.

**CNAME Record

Bu kayıtlar başka bir domaine çözümlenir, örneğin, TryHackMe'nin online mağazasının subdomaini store.tryhackme.com'dur ve bu da bir CNAME kaydı olan shops.shopify.com'u döndürür. Ardından, IP adresini hesaplamak için shop.shopify.com'a başka bir DNS isteği yapılır.

**MX Record

Bu kayıtlar, sorguladığınız etki alanı için e-postayı işleyen sunucuların adresine çözümlenir, örneğin, tryhackme.com için bir MX Record yanıtı alt1.aspmc.l.google.com gibi görünür. Bu kayıtlar ayrıca bir priority flag (öncelik bayrağı) ile birlikte gelir. Bu, istemciye sunucuları hangi sırayla denemesi gerektiğini söyler; bu, ana sunucu çökerse ve e-postanın bir yedek sunucuya gönderilmesi gerekirse işe yarar.

**TXT Record

Herhangi bir metin tabanlı verinin depolanabileceği serbest metin alanlarıdır. TXT kayıtlarının birden çok kullanımı vardır, ancak yaygın olarak kullanılanlardan bazıları, domain adına e-posta gönderme yetkisine sahip sunucuları listelemek olabilir (bu, spam ve sahte e-postaya karşı savaşta yardımcı olabilir). Üçüncü Taraf hizmetlere kaydolurken alan adının sahipliğini doğrulamak için de kullanılabilirler.

E-postanın nereye gönderileceğini bildirmek için ne tür bir kayıt kullanılır? MX Record
Ne tür bir kayıt IPv6 adreslerini işler? AAAA Record

4. **Talepte Bulunmak

**Bir DNS isteği yaptığınızda ne olur?

Bir domain talep ettiğinizde, bilgisayarınız önce adresi daha önce arayıp aramadığınızı görmek için local cache'i (yerel önbellek) kontrol eder; bulamazsa, Recursive DNS Server'a istek yapar.

Recursive DNS Server genellikle İSS'niz tarafından sağlanır, ancak kendi sunucunuzu da seçebilirsiniz. Bu sunucu ayrıca yakın zamanda aranan alan adlarının local cache'ine sahiptir. Local bir sonuç bulunursa, bu bilgisayarınıza geri gönderilir ve talebiniz burada sona erer (bu, Google, Facebook gibi popüler ve yoğun talep edilen hizmetler için yaygındır). Talep local olarak bulunamazsa, internetin root DNS sunucularından başlayarak doğru cevabı bulmak için bir yolculuk başlar.

Root serverlar, internetin DNS omurgası görevini görür; onların işi, isteğinize bağlı olarak sizi doğru TLD'ye yönlendirmektir. Örneğin, www.tryhackme.com'u talep ederseniz, root server .com'un TLD'sini tanıyacak ve sizi .com adresleriyle ilgilenen doğru TLD sunucusuna yönlendirecektir.

TLD sunucusu, DNS isteğini yanıtlayacak authoritative server'ın (yetkili sunucu) nerede bulunacağına ilişkin kayıtları tutar. Authoritative server genellikle domain için nameserver olarak da bilinir. Örneğin, tryhackme.com için nameserver kip.ns.cloudflare.com ve uma.ns.cloudflare.com'dur. Bir domainin arızalanması durumunda yedek görevi görmesi için genellikle birden fazla nameserver bulunur.

Authoritative bir DNS sunucusu, belirli bir domain için DNS kayıtlarını depolamaktan sorumlu olan ve domainin DNS kayıtlarında herhangi bir güncellemenin yapılacağı sunucudur. Kayıt türüne bağlı olarak, DNS kaydı daha sonra Recursive DNS Server'a geri gönderilir; burada local bir kopya gelecekteki istekler için önbelleğe alınır ve ardından isteği yapan orijinal istemciye geri iletilir. DNS kayıtlarının tümü bir TTL (Time To Live) değeriyle gelir. Bu değer, siz tekrar aramanız gerekene kadar yanıtın local olarak kaydedilmesi gereken saniye cinsinden temsil edilen bir sayıdır. Önbelleğe alma, bir sunucuyla her iletişim kurduğunuzda bir DNS isteği yapmak zorunda kalmanızı önler.

Bir DNS kaydının ne kadar süreyle önbelleğe alınması gerektiğini hangi alan belirtir? TTL
İSS'niz tarafından genellikle ne tür bir DNS Sunucusu sağlanır? Recursive
Bir etki alanı için tüm kayıtları ne tür bir sunucu tutar? Authoritative