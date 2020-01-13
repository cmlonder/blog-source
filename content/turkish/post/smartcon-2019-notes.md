---
title: "Smartcon 2019 Notları"
date: 2019-10-02T08:14:40+03:00
lastmod: 2019-10-02T08:14:40+03:00
keywords: ["yapay zeka", "makine öğrenmesi", "konferans", "smartcon"]
description: "Yapay zeka ve Makine öğrenmesi konularında sektörün önde gelen firmalarının bir araya geldiği
smartcon2019 konferans notları"
tags: ["yapay zeka", "makine öğrenmesi"]
categories: ["konferans"]
author: "cemal"
---

Bilgilendirici ve keyifli bir konferans sonrası notlarımı paylaşmak istiyorum. Beni en çok etkileyen Citus oldu, Microsoft
ise partnerleri ve yaptığı yatırımlarla Açık Kaynak konusundaki vizyonunu nasıl daha da geliştirdiğini göstermiş oldu.
Sunumların şablonları şu şekilde; problemi ortaya koy, şirketin buna getirdiği çözümden bahset. Paneller ise sohbet
havasında geçti.

[smartcon2019](https://www.smartcon.com/istanbul-2019/)

## Değişen Nesil ve Kendi Kendini Yöneten Teknolojiler
> Işıl Kılınç Gürtuna, Oracle Türkiye, Satış Kıdemli Direktörü

* Startup maliyetleri düşüyor, 5000$ civarlarında.
* Büyük kurumlarda yaratıcılık boşa harcanıyor, 80'e 20 kuralı geçerli. Kaliteli işler 20'lik kesimden geliyor.
* Veri tabanı işlerinin %95'i hala manual yönetiliyor
* Veri kayıplarının, db çökmeleri vb. işlerin %90'ı insan hatası, sıkıcı işlerin/rutinlerin yapılmak istememesi vb.
durumlardan ortaya çıkıyor..
* Otonom teknolojiler burada ön plana çıkıyor -> kendi kendine yanlışı düzeltme, güvenliğini sağlama, insan hatalarının olduğu
örneğin; "operasyonel sıkıcı işleri" otomatize etme

Oracle'ın bunlara çözümü, dünyanın ilk [otonom veritabanı](https://www.oracle.com/database/autonomous-database/feature.html)

## Hazine Avcıları: Veriden Değer Yaratmak
> Hamit Hamutcu, smartcon & Analytics Center, Kurucu Ortak  
İlker Kuruöz, Garanti BBVA, Mühendislik Hizmetleri ve Veri GMY  
Ömer Nadirler, SnA Consulting, Kurucu  
Önder Ömer Oğuzhan, Teknosa, Pazarlama ve Teknoloji GMY  
Ömer Uyar, Intertech, Genel Müdür  
Tayfun Topkoç, SAS, Genel Müdür, Türkiye ve Orta Asya  

* Şirket içi Data Scientist(Veri Bilimci) eğitimleri veriliyor, günümüzde Veri Bilimci yetiştirmenin önemi büyük. (Intertech)
* Her trende kapılmamak gerekiyor. Trend gerçekten bir çözüm mü, ihtayacı karşılıyor mu analiz ettikten sonra aksiyon
alınmalı. (Garanti)
* Dünyada Veri Bilimci eksiği var. Türkiye'de teknolojiye yatırım %70 donanım, %10 yazılım, %20 servis yönünde.
* Günümüzde veri bilimi müşteri sesinden krediyi ödeyip ödeyememe tahmini gibi alanlara kadar yönelmiş durumda. (SnA)
* Şirketlerde garaj modeli kullanılması önemli. Bu modelde farklı departmanlardan çalışanlar bir araya gelip birbirlerinin
ihtiyaçlarını daha yakından tartışıp karar alıyorlar. (Teknosa, Pazarlama ve Teknoloji GMY'si olması dolasıyla açılan bir muhabbet,
çünkü birbirinden uzak gibi görünen iki birimi aynı anda en tepeden kontrol etmesi ilklerden, dünyada benzerleri var)
* Veri Bilimci eksiği nasıl gideriliyor? Skor kartlarıyla, çeşitli yazılımlarla kaynak arayışı. Altın sorular ise bu kişinin
Veri Bilimcilik kariyerinde ne kadar istekli olduğu ve dayanıklı olacağı. (SnA)
* Veri güvenliği için çeşitli araçlar kullanılıyor; hem çalışanı dış etkenlerden korumak için hem de şirketi iç & dış etkenlerden
korumak için anomali tespitleri yapılıyor.
* "Transactional" ve "Unstructured" yapıları birlikte kullanmak ileriki hedeflerden.
* Veri Bilimci olmak isteyen insanlar uçtan uca iş yapabilmeli, Problemi anlama, harmanlama, modelleme, iş birimleriyle konuşma,
pazara yakın olmalı.
* Günümüzde siber güvenliğe ve veri bilimine olan yatırımlar artıyor ve artacak.

## İş Dünyasında Robotların Çağı
> Tuğrul Cora, UIPath Türkiye, Genel Müdür

* 2018 RPA kullanımı -> %19
* 2020 RPA kullanımı -> ~%70
* Robotik süreç otomasyonu -> yazılımlara rutin işleri yaptırmak
* Örneğin; Faturalama sürecinde RPA:
    * Faturaları okuyor
    * SAP'a yüklüyor
    * Doğrulama yapıyor (KDV doğru girilmiş mi vb.)
    * İlgili kişiye mail atıyor (SAP sayesinde)
* Diğer bir örnek ise SGK teşvik süreci;
    * Dosya ve başvuru analizi -> ~120 farkıl kaynaktan doğrulama lazım. Robotlarla bu doğrulama işlemleri x90 kat hızlandırılmış.
* API bağlantısı yok, UI kullanılıyor. Manual sürecin aynısı yapılıyor, bu da yeniden bir akış çıkarılması maliyetini ortadan kaldırıyor. 
ROI 1-3 yıldan 3-6 aya indiriyor geleneksel yaklaşıma göre.
* İnsanlar rutin olan işleri değil, daha fazla katma değerli iş yapmak istiyor. RPA ile hem işler hızlanıyor
hem de çalışanın şirkete bağlılığı artarken, hata payı 0'a indiriliyor.
* 1970-2015'te 3.5 M iş gücü kaybolurken, aynı seneler içerisinde robotların sağladığı yeni iş imkanı ~10M civarı (nüfüsun yaklaşık %10luk kısmı kadar)
* Karar ve muhakeme gerektiren süreçleri otomize etmek gelecekteki hedef.
* Şirketlerde merkesi otomasyon %3-7 civarı, çalışanın yaptığı işlere gereken otomasyon ise %40 civarı.
Bu yüzden her çalışana bir robot vizyonu.

## Challenges of (BIG, small, right) Data & ML
> Dr. Ricardo Baeza-Yates, NTENT, Chief Technology Officer

* Büyük Veri(Big Data) başlı başına zorlu iken, Veri (Huge Data, referans alabilecek bir ceviri bulamadım) daha zorlu bir süreç.
* Tavsiye ettiği kitap -> Funes the Memorious, Borges
* Küçük Verinin (Small Data) önemi -> Yenilik küçük verinin işlenmesiyle gelir, çünkü üzerinde çalışması daha kolaydır, büyük verinin önce
sadeleştirilmesi ve çalışmaya mümkün hale getirilmesi lazım.
* Bias (Eğilim, Yargı, Taraflılık diyebiliriz. Malesef ortak kullanılan bir Türkçe karşılığını bulamadım. Kendim de Bias olarak kullanıyorum günlük hayatta.)
sorunu mevcut. Bu Bias problemi farklı kategorilerde değerlendirilebilir:

### Cinsiyet Biası
İstatistiksel olarak kadınlar daha fazla bebek bakıcılığı, erkekler de daha fazla doktor oluyorsa, cinsiyet ayrımı olmayan bir dil için (örneğin Türkçe),

   * He is a baby sitter -> O bir bebek bakıcısı
   * She is a doctor -> O bir doktor
    
çevirilerini yaptığımızda, tersi bir çeviri şu şekilde olabiliyor:

   * O bir bebek bakıcısı -> **She** is a baby sitter
   * O bir doktor -> **He** is a doctor
   
Google Translate ile kontrol ettiğimde "Translations are gender specific" uyarısını verip her iki tercümeyi de göstermekte. Google bu kısmı halletmiş gibi görünüyor, en azından
içerik (context) bağımsız bir cümle ile sorduğumuzda. Çünkü şu cümleyi denediğim zaman

   * Kadın ne yapacağını bilemedi. Aslında bir doktor olmasına rağmen soğukkanlılığını koruyamadı.
Çevirisi:

   * **She** didn't know what to do. Although **he** was actually a **doctor**, he could not maintain his composure.
   ``
Yani hala bu bias'ın geçerliliği var diyebiliriz.

### Aktivite Biası;
Sosyal medyalardaki içeriğin %50'si kullanıcıların %10'undan daha azından geliyor. Bu yüzden bu verilere dayanarak yapılan
çıkarımlar aslında %10'luk bir kesimin yönlendirmesiyle olanlar. Örneğin %50'lik içerik (sunumdaki kaynak ve yılı hatırlayamıyorum ama benzer aramayı yaptığımda
günümüzde de benzer sonuçlarla karşılaştım);

   * Wikipedi'ya içeriği kullanıcılarının %0.04'ünden
   * Twitter tweetleri kullanıcılarının %2'sinden
   * Facebook paylaşımları kullanıcılarının  %7'sinden
    
### Sıralama ve Sosyal Bias;
Bir ürünü alırken/almaya karar verirken örneğin amazon üzerinden, bize sunulan sıralama o ürünün alma kararımızda etkili. İnsanların 
verdiği ya da verdiğini zannettiğimiz (eğer sahte yorumlar/puanlamalar kullanılıyorsa) puanlar da bir başka faktör.

### Bias Çıkmazı
Yeni bir blog açan bir kullanıcı eğer blogunun içeriğini, aradığı konuda webde bulduğu ilk makalelerin bir kısmını kopyalayarak yeni
makale oluşturduysa, aslında sıralama bias'ını daha da kuvvetlendirmiş oldu.

İlgili Yayın -> [Bias on the Web](https://cacm.acm.org/magazines/2018/6/228035-bias-on-the-web/abstract)

## Tekneloji ile Şekillenen Müşteri Deneyimi
> Atilla Bayrak, SabancıDX, İleri Veri Analitiği GMY  
Emre Tok, Careem, Dijital Pazarlama ve Müşteri Yönetimi GMY  
Lale Can, Afiniti Türkiye, İş Geliştirme Direktörü  
Poyraz Özkan, AlternaCX, Kurucu  
Önder Sönmez, Hitachi Türkiye, Genel Müdür  

* Careem, Orta Doğu'nun Uber'i diyebileceğimiz (ve Uber'in satın aldığı) ulaşım aracı. Bu taşıma sadece insan taşımayla sınırlı bir vizyon değil.
* Careem Müşteri Deneyimini 3 kolda değerlendiriyor;
   * Hizmet Öncesi -> Araç müşteriyi alması gereken yere geldi mi? Örneğin evinin önünden alıcaktı ama arka kapıya mı geldi?
   * Hizmet Sırası -> Sürüş deneyimi iyi miydi?
   * Hizmet Sonrası -> Ödemi seçenekleri müşterinin ihtiyaçlrını sağlayacak şekilde ve kolaylıkta mıydı?
* Basitlik ve çözüm önemli. Örneğin internet olmayan veya sık kesilebilen bir ülkede müşteri SMS ile telefon çağırabilmeli veya WhatsApp'ın yaygın olduğu
bir yerde WhatsApp ile çağırabilmeli.
* Afiniti ise call-center'lara yapılan aramalarda arayan müşteri için en uygun satıcıyı eşleştirip hem müşteri deneyimini
hem de satış oranını arttırmayı hedefliyor.

## Yapay Zekadan İş Değeri Yaratmak
> Münir Kundakçı, Microsoft Türkiye, Pazarlama ve Operasyonlardan Sorumlu GMY  
Mete Bayrak, Motiwe

* Yapay zeka ve görüntü/video işleme çözümleri bir arada
* İş güvenliği çözümü; baret var mı? İnsan girmemesi gereken yere insan girmiş mi?
* Kalite kontrol; pizza olması gereken kalitede mi? Buzdolabı kalitesi olması gerektiği gibi mi? Çizik vb. algılayıp
hem müşteri memnuniyetini arttırma hem de olası hatalarda oluşabilecek lojistik maliyetlerini önceden önleme.
* Mevcut kameralara entegre olarak manavdaki kasaların doluluğunun takibi ve bildirim verilmesi. Daha da ileri seviyelerde
bu verilerin anlamlandırılıp hangi gıdaların hangi semtlerde/saat aralıklarında nasıl talep gördüklerinin raporu.
* Bebek doğru yatıyor mu, odada bir sorun var mı tespiti

## Yapay Zeka ve Etik
> Cansu Canca, AI Ethics Lab, Kurucu

* 2017'den sonra dünya geneli skandallar oluşması. Örneğin; Facebook Cambridge Analytica, insanların davranışları tespit edilip
reklamlarla seçim sonucunu manipüle etmeye çalışmaları vb. Microsoft, IBM vb. şirketlerin de benzer veri sızıntısı olayları var.
* 2017'den sonra ülke ve şirketlerde veri korunumuna dair bir çok bildirge yayınlanmaya başlanıyor. Türkiye'de yayınlanan
bir bildirge yok ancak skandal da yok.
* Kişilerin, kurumların veri hassasiyeti konusunda bilinçlenmesi ve nasıl davranması/ne önlemler alması gerektiği konusunda
eğitim almaları gerekir, AI Etchis Lab.

## Veri Biliminde Yeni Yönelimler ve Başarı Hikayeleri
> Özgür Doğan, Blend 360, Kurucu ve Yönetici Ortak

Trendler:

   * Data scientiests
       * Piyasada büyük boşluk var. Veri Bilimci iş ilanları %31 artarken iş ilanları %14 artmış.
   * Open Source kullanım arttı, özellikle Python'un sunduğu kütüphanelerle şu andaki dil kullanımı
       * Python > R > SAS
   * addressability
       * Ürünün reklamını herkese yapmak yerine alma potansiyeli daha yüksek kişilere reklam yapmak.
   * personalization
       * Kişiye özel deneyim sunabilme
   * Reach Consumer
       * Müşteri bir çok kanalı kullanıyor, TV, Mail, Sosyal Medyalar, Uygulamalar vb. Müşteriye bu araçlardan erişimi
        yönetmek ve raporları tek bir yerden alabilmek gerekiyor.

## Kuruluştan Satışa Bir Girişim Hikayesi
> Utku Azman, Citus EMEA-Microsoft, Direktör
    
* Aynı anda bir çok bilgisayarı işleterek paralel olarak veri işleme.
* Başarısının sırrı -> Cloud + Open Source + Big Data (Trendler) + İyi bir takım + Doğru zamanlama

## Yeni Dünya için Girişimcilik
Son oturumdu, çok fazla kişi kalmamıştı. Takip edebildiğim Tospaa girişimi oldu. Ecording ise diğer bir girişimdi ancak 
takip edemedim. 

Tospaa:

 * Programlama dersi zorunlu hale geldi. Ancak okullardaki bilgisayar labarotuarları yeterli değil.
 * Tospaa'nın çözümü, programlamayı kutu oyunu ile öğrencilere öğretmek.

