1. **Hepsi Bir Arada

Önceden, tarayıcıda bir web sayfası talep ettiğimizde perde arkasında pek çok şeyin döndüğünü öğrendik.

Özetlemek gerekirse, bir web sitesi talep ettiğinizde, bilgisayarınızın konuşabilmesi için sunucunun IP adresini bilmesi gerekir; bunun için DNS kullanır. Bilgisayarınız daha sonra HTTP protokolü adı verilen özel bir komut seti kullanarak web sunucusuyla konuşur; web sunucusu daha sonra tarayıcınızın web sitesini size doğru şekilde biçimlendirmek ve görüntülemek için kullandığı HTML, JavaScript, CSS, Resimler vb. döndürür.
Web'in daha verimli çalışmasına yardımcı olan ve ekstra özellikler sağlayan birkaç başka bileşen de vardır.

2. Diğer Bileşenler

2a. **Load Balancers (Yük Dengeleyiciler)

Bir web sitesinin trafiği oldukça artmaya başladığında veya yüksek kullanılabilirliğe sahip olması gereken bir uygulama çalıştırıldığında, bir web sunucusu artık işi yapamayabilir. Yük dengeleyiciler, yüksek trafikli web sitelerinin yükü kaldırabilmesini sağlayan ve bir sunucu yanıt vermediğinde yük devretme sağlayan iki ana özellik sunar.

Yük dengeleyici ile bir web sitesi talep ettiğinizde, yük dengeleyici önce talebinizi alacak ve ardından arkasındaki birden çok sunucudan birine iletecektir. Yük dengeleyici, hangi sunucunun istekle en iyi şekilde ilgileneceğine karar vermesine yardımcı olmak için farklı algoritmalar kullanır.

Yük dengeleyiciler ayrıca, doğru çalıştıklarından emin olmak için her sunucudan düzenli kontroller gerçekleştirir; buna sağlık kontrolü denir. Bir sunucu uygun şekilde yanıt vermezse veya yanıt veremezse, yük dengeleyici tekrar uygun şekilde yanıt verene kadar trafik göndermeyi durdurur.

2b. **CDN (Content Delivery Networks)

Bir CDN, yoğun bir web sitesine gelen trafiği azaltmak için mükemmel bir kaynak olabilir. Web sitenizden JavaScript, CSS, Resimler gibi statik dosyaları barındırmanıza ve bunları dünyanın her yerindeki binlerce sunucuda barındırmanıza olanak tanır. Bir kullanıcı barındırılan dosyalardan birini istediğinde, CDN en yakın sunucunun fiziksel olarak nerede olduğunu bulur ve isteği muhtemelen dünyanın diğer ucu yerine oraya gönderir.

2c. **Database (Veritabanı)

Genellikle web siteleri, kullanıcıları için bilgi depolamanın bir yoluna ihtiyaç duyar. Web sunucuları, veri depolamak ve onlardan veriyi geri çağırmak için veritabanlarıyla iletişim kurabilir. Veritabanları, basit bir düz metin dosyasından, hız ve dayanıklılık sağlayan birden çok sunucunun karmaşık kümelerine kadar değişebilir. Bazı yaygın veritabanları: MySQL, MSSQL, MongoDB, GraphQL vb. Her birinin kendine özgü özellikleri vardır.

2d. **WAF (Web Application Firewall)

Web talebiniz ile web sunucusu arasında bir WAF bulunur; birincil amacı, web sunucusunu bilgisayar korsanlığı veya hizmet reddi saldırılarına karşı korumaktır. Talebin bir bottan ziyade gerçek bir tarayıcıdan olup olmadığına bakılmaksızın, yaygın saldırı teknikleri için web isteklerini analiz eder. Ayrıca, bir IP'den saniyede yalnızca belirli bir miktarda talebe izin verecek olan hız sınırlama adı verilen bir şey kullanarak aşırı miktarda web talebinin gönderilip gönderilmediğini de kontrol eder. Bir talep potansiyel bir saldırı olarak kabul edilirse, düşürülür ve asla web sunucusuna gönderilmez.

Statik dosyaları barındırmak ve bir müşterinin bir web sitesini ziyaretini hızlandırmak için ne kullanılabilir? CDN
Bir ana bilgisayarın hala hayatta olduğundan emin olmak için bir yük dengeleyici ne yapar? Health Check
Bir web sitesinin hacklenmesine karşı ne yardımcı olabilir? WAF

3. **Web Sunucuları Nasıl Çalışır

3a. **Web Sunucusu Nedir

Bir web sunucusu, gelen bağlantıları dinleyen ve ardından web içeriğini istemcilerine iletmek için HTTP protokolünü kullanan bir yazılımdır. En yaygın sunucu yazılımları Apache, Nginx, IIS ve NodeJS'dir. Bir web sunucusu, yazılım ayarlarında tanımlanan kök dizini adı verilen dizinden dosya gönderir. Örneğin, Nginx ve Apache, Linux işletim sistemlerinde /var/www/html ile aynı varsayılan konumu paylaşır ve IIS, Windows işletim sistemleri için C:\inetpub\wwwroot kullanır. Örneğin, http://www.example.com/picture.jpg dosyasını talep ettiyseniz, yerel sabit sürücüsünden /var/www/html/picture.jpg dosyasını gönderir.

3b. **Virtual Host

Web sunucuları, farklı alan adlarına sahip birden çok web sitesini barındırabilir; bunun için virtual host kullanırlar. Web sunucusu yazılımı, HTTP başlıklarından istenen host adını kontrol eder ve bunu virtual hostlarla eşleştirir (virtual hostlar yalnızca metin tabanlı yapılandırma dosyalarıdır). Bir eşleşme bulursa, doğru web sitesi sağlanacaktır. Eşleşme bulunamazsa, bunun yerine varsayılan web sitesi sağlanacaktır.

Virtual hostlar, kök dizinlerini sabit sürücüdeki farklı konumlara eşleyebilir. Örneğin, one.com'un /var/www/website_one ile eşlenmesi ve two.com'un /var/www/website_two ile eşlenmesi.

Bir web sunucusunda barındırabileceğiniz farklı web sitelerinin sayısında bir sınır yoktur.

3d. **Statik ve Dinamik İçerik

Adından da anlaşılacağı gibi statik içerik, asla değişmeyen içeriktir. Bunun yaygın örnekleri resimler, JavaScript, CSS vb.'dir, ancak asla değişmeyen HTML'i de içerebilir. Ayrıca bunlar, üzerinde herhangi bir değişiklik yapılmadan doğrudan web sunucusundan sunulan dosyalardır. 

Dinamik içerik ise farklı isteklerle değişebilen içeriktir. Örneğin bir blog ele alın. Blogun ana sayfasında size en son girişleri gösterecek. Yeni bir giriş oluşturulursa, ana sayfa en son girişle güncellenir veya ikinci bir örnek, bir blogdaki arama sayfası olabilir. Hangi kelimeyi aradığınıza bağlı olarak, farklı sonuçlar görüntülenecektir.

Sonunda gördüğünüz şeylerdeki bu değişiklikler, programlama ve script dillerinin kullanımıyla backend adı verilen şeyde yapılır. Buna backend denir çünkü yapılanların tamamı perde arkasında yapılır. Web sitelerinin HTML kaynağını görüntüleyemez ve backendde neler olduğunu göremezsiniz, HTML ise backendden işlemenin sonucudur. Tarayıcınızda gördüğünüz her şeye ise frontend denir.

3e. **Script ve Backend Dilleri

Bir backend dilinin çok fazla bir sınırı yoktur ve bunlar bir web sitesini kullanıcı için etkileşimli yapan şeydir. Bu dillerden bazıları PHP, Python, Ruby, NodeJS, Perl ve çok daha fazlasıdır. Bu diller veritabanlarıyla etkileşime girebilir, harici hizmetleri arayabilir, kullanıcıdan gelen verileri işleyebilir ve çok daha fazlasını yapabilir. Bunun çok basit bir PHP örneği, http://example.com/index.php?name=adam web sitesini talep etmeniz olacaktır.

Eğer index.php şu şekilde oluşturulmuşsa:

<html><body>Hello <?php echo $_GET["name"]; ?></body></html> 

İstemciye aşağıdaki çıktıyı verir:

<html><body>Hello adam</body></html>

Backendde olduğu için istemcinin herhangi bir PHP kodu görmediğini fark edeceksiniz. Bu etkileşim, daha güvenli bir şekilde oluşturulmamış web uygulamaları için çok daha fazla güvenlik sorununa yol açar. 

Web sunucusu yazılımı birden fazla siteyi barındırmak için ne kullanır? Virtual Host
Değişebilen içerik türünün adı nedir? Dinamik
İstemci arka uç kodunu görüyor mu? Hayır

