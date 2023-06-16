
1. **Web Siteleri Nasıl Çalışır

Bir web sitesini ziyaret ettiğinizde, tarayıcınız ziyaret ettiğiniz sayfa hakkında bilgi isteyen bir web sunucusuna istekte bulunur. Tarayıcınızın size sayfayı göstermek için kullandığı verilerle yanıt verecektir; bir web sunucusu, dünyanın herhangi bir yerindeki isteklerinizi yerine getiren özel bir bilgisayardır.

Bir web sitesini oluşturan iki ana bileşen vardır:

-Front End (Client-Side) - Tarayıcınızın bir web sitesini işleme şekli

-Back End (Server-Side) - İsteğinizi işleyen ve bir yanıt döndüren bir sunucu.

Bir web sunucusuna istekte bulunan tarayıcınızda yer alan başka birçok işlem vardır, ancak şimdilik, bir sunucuya istekte bulunduğunuzu ve tarayıcınızın size bilgi sağlamak için kullandığı verilerle yanıt verdiğini anlamanız yeterlidir.

Tarayıcınız tarafından oluşturulan bir web uygulamasının bileşenini en iyi tanımlayan terim hangisidir? Front End

2. **HTML

Web siteleri öncelikle aşağıdakiler kullanılarak oluşturulur:

-Web siteleri oluşturmak ve yapılarını tanımlamak için HTML.

-Stil seçenekleri ekleyerek web sitelerinin güzel görünmesini sağlamak için CSS.

-Sayfalarda karmaşık özellikler uygulamak için JavaScript.

HyperText Markup Language (HTML), web sitelerinin yazıldığı dildir. Elementler (tag olarak da bilinirler), HTML sayfalarının yapı taşlarıdır ve tarayıcıya içeriğin nasıl görüntüleneceğini söyler. Aşağıda her web sitesi için aynı olan basit bir HTML belgesi örneği bulunmaktadır:

<!DOCTYPE html>
<html>
	<head>
		<title>Sayfa Başlığı</title>
	<head>
	<body>
		<h1>Örnek Başlık</h1>
		<p>Örnek Paragraf</p>
	</body>
</html>

HTML yapısı (örnekte gösterildiği gibi) aşağıdaki bileşenlere sahiptir:

-<!DOCTYPE html>, sayfanın bir HTML5 belgesi olduğunu tanımlar. Bu, farklı tarayıcılarda standardizasyona yardımcı olur ve tarayıcıya sayfayı yorumlamak için HTML5 kullanmasını söyler.

-<html>, HTML sayfasının kök elementidir, diğer tüm elementler bundan sonra gelir.

-<head>, sayfa hakkında bilgi içerir (sayfa başlığı gibi).

-<body>, HTML belgesinin gövdesini tanımlar; tarayıcıda yalnızca gövde içindeki içerik gösterilir.

-<h1>, büyük bir başlığı tanımlar.

-<p>, paragrafı tanımlar.

Farklı amaçlar için kullanılan başka birçok element (tag) vardır. Örneğin, butonlar (<button>), resimler (<img>), listeler ve çok daha fazlası için tagler vardır.

Tagler, bir öğeye stil vermek için kullanılabilen class özelliği (örneğin, tagi farklı bir renk yapmak) <p class="bold-text"> veya resimlerde konumu belirtmek için kullanılan src, <img src="img/cat.jpg"> gibi özellikler içerebilir. Elementlerin her birinin kendine özgü amacı olan birden çok özelliği olabilir, örneğin, <p özellik1="değer1" özellik2="değer2">

Elementler ayrıca, elemente özgü bir id özelliğine (<p id="örnek">) sahip olabilir. Birden çok elementin aynı classı kullanabileceği class özelliğinin aksine, bir elementin benzersiz bir şekilde tanımlanması için farklı id'lere sahip olması gerekir. Element id'leri, stil vermek ve onu JavaScript ile tanımlamak için kullanılır. 

3. **JavaScript

JavaScript (JS), dünyadaki en popüler kodlama dillerinden biridir ve sayfaların etkileşimli hale gelmesini sağlar. Web sitesi yapısını ve içeriğini oluşturmak için HTML kullanılırken, JavaScript web sayfalarının işlevselliğini kontrol etmek için kullanılır. JS olmadan bir sayfada etkileşimli elementler olmaz ve her zaman statik kalır. JS, sayfayı gerçek zamanlı bir şekilde dinamik olarak güncelleyebilir ve sayfada belirli bir olay meydana geldiğinde (örneğin, bir kullanıcı bir butonu tıklattığında) bir butonun stilini değiştirme veya hareketli animasyonlar görüntüleme işlevi sunar. 

JavaScript, sayfa kaynak koduna eklenir ve script tagleri içine yüklenebilir veya src özelliğiyle uzaktan dahil edilebilir: <script src="/location/of/javascript_file.js"></script>

Aşağıdaki JavaScript kodu sayfada "demo" idsine sahip bir HTML tagi bulur ve tagin içeriğini "Gezegeni Hackle" olarak değiştirir: document.getElementById("demo").innerHTML = "Gezegeni Hackle";

HTML taglerinde, olay gerçekleştiğinde JavaScript'i yürüten "onclick" veya "onhover" gibi etkinlikler de olabilir. Aşağıdaki kod, demo idsine sahip tagin metnini Düğme Tıklandı olarak değiştirir: <button onclick='document.getElementById("demo").innerHTML = "Düğme Tıklandı";'>Click Me!</button> - onclick etkinliği doğrudan tagler üzerinde değil, JavaScript tagleri içinde de tanımlanabilir.

4. **Hassas Verilerin Açıklanması (Sensitive Data Exposure)

Bir web sitesi hassas clear-text bilgilerini son kullanıcıya uygun şekilde korumadığında (veya kaldırmadığında) gerçekleşir; genellikle sitenin frontend kodunda bulunur.

Web sitelerinin, yalnızca "sayfa kaynağını görüntüleyerek" görebildiğimiz birçok HTML elementi kullanılarak oluşturulduğunu biliyoruz. Bir web sitesi geliştiricisi, oturum açma bilgilerini, web sitesinin özel bölümlerine giden gizli bağlantıları veya HTML ve JS'te gösterilen diğer hassas verileri kaldırmayı unutmuş olabilir.

Bir saldırganın bir web uygulamasının farklı bölümlerine erişimini ilerletmek için hassas bilgiler potansiyel olarak kullanılabilir. Örneğin, geçici oturum açma kimlik bilgilerine sahip HTML yorumları olabilir ve sayfanın kaynak kodunu görüntülediyseniz ve bunu bulduysanız, bu kimlik bilgilerini uygulamanın başka bir yerinde oturum açmak için kullanabilirsiniz (veya sitenin diğer backend bileşenlerine erişmek için kullanılabilir).

Bir web uygulamasını güvenlik sorunları açısından değerlendirdiğinizde, yapmanız gereken ilk şeylerden biri, açığa çıkmış oturum açma bilgilerini veya gizli bağlantıları bulup bulamayacağınızı görmek için sayfanın kaynak kodunu incelemektir.

5. **HTML İnjection

Sayfada filtrelenmemiş kullanıcı inputu görüntülendiğinde oluşan bir güvenlik açığıdır. Bir web sitesi kullanıcı inputunu temizleyemezse (kullanıcın siteye eklediği herhangi bir "kötü niyetli" metni filtreleyemez) ve bu input sayfada kullanılırsa, saldırgan savunmasız bir web sitesine HTML kodu enjekte edebilir.

Bir kullanıcın bir web sitesine input ettiği bilgiler genellikle diğer frontend ve backend ilevlerinde kullanıldığından, input temizliği bir web sitesini güvenli tutmada çok önemlidir.

Bir kullanıcı inputunun nasıl görüntülendiğini kontrol ettiğinde, HTML (veya JavaScript) kodunu gönderebilir ve tarayıcı bunu sayfada kullanarak kullanıcının sayfanın görünümünü ve işlevselliğini kontrol etmesine izin verir. 

Genel kural, asla kullanıcı inputlarına güvenmemektir. Kötü amaçlı inputu önlemek için, web sitesi geliştiricisi, kullanıcının input ettiği her şeyi JavaScript işlevinde kullanmadan önce temizlemelidir; bu durumda, geliştirici herhangi bir HTML tagini kaldırabilir.

