---
layout: post
title: LibreOffice'e Katkı Vermek
---
	LibreOffice,pek çok platformda çalışan ve diğer ofis programlarıyla uyumlu, özgür ve ücretsiz bir ofis yazılımıdır.

LibreOffice'e katkı vermeyi düşünüyorsanız, katkı vermeden önce gerçekleştirilmesi gereken aşamaları ve yama göndermek için gerekli adımları anlatacağım.

### 1. adım: Geliştirici listesine üye olmak
	
[Geliştirici listesine](http://lists.freedesktop.org/mailman/listinfo/libreoffice) bu adresten üye olunmalı.

### 2. adım: Hata takip sistemine üye olmak

Libreoffice hata takip sistemi olarak bugzilla kullanılmaktadır. Bugzilla, libreoffice kullanımı sırasında ortaya çıkan hataların kullanıcılar tarafından geliştiricilere bildirilmesini sağlayan web tabanlı bir arayüzdür.

[Hata takip sistemi üyeliği](https://bugs.documentfoundation.org/) buradan yapılmalı.

### 3. adım: Kaynak kodun indirilmesi

[Belgede](https://bugs.documentfoundation.org/) bahsedildiği gibi kaynak kod indirilmeli.


	$ git clone git://anongit.freedesktop.org/libreoffice/core libreoffice


### 4. adım: Kaynak kodun derlenmesi

[Kaynak kodu derlemek](https://wiki.documentfoundation.org/Development/BuildingOnLinux) için yardımcı olacaktır. ([Video](https://www.youtube.com/watch?v=2gIqOOajdYQ&hd=1))

<b>Kısaca adımlar</b>

<i>Önce depoyu derliyoruz: </i>
{% highlight js %}
 $ sudo apt-get update
 $ sudo apt-get dist-upgrade
{% endhighlight %}

<i>Bağımlılıkları kuruyoruz:</i>
{% highlight js %}
 $ sudo apt-get build-dep libreoffice
{% endhighlight %}

<i>LibreOffice deposunu indiriyoruz:</i>
	
 	$ git clone git://anongit.freedesktop.org/libreoffice/core libreoffice
	

<i>Dizinde betik dosyasının hatasız çalıştığını görmek için komutu çalıştırıyoruz:</i>
{% highlight js %}
 $ cd libreoffice
 $ ./autogen.sh
{% endhighlight %}

<i>Derliyoruz:</i>
{% highlight js %}
 $ make -jN 
{% endhighlight %}
<i>[Not1: N: çekirdek sayısı], [Not2: Derleme işlemi uzun sürüyor]</i>

<i>Derleme tamamlanınca Libreoffice5'in çalıştığından emin olmak için bu komutu kullanabilirsiniz:</i>

{% highlight js %}
 $ instdir/program/soffice 
{% endhighlight %}

### 5. adım: Feragatname göndermek

[Feragatname göndermek](https://wiki.documentfoundation.org/index.php?title=Development/Developers&oldid=117013) için gerekli adımlardan bahsediliyor. Fakat kısaca açıklayacak olursak:

Kısaca; " <b>libreoffice@lists.freedesktop.org</b> "adresine,

Konu:
{% highlight js %}
 <your name> license statement
{% endhighlight %}
olacak şekilde şu içerik yollanmalıdır:

"
 <b>All of my past & future contributions to LibreOffice may be licensed under the MPLv2/LGPLv3+ dual license.</b>
" 


###  6. adım: Yama gönderilmesi

Yamaları  [gerrit](https://gerrit.libreoffice.org/#/q/status:open) üzerinden yolluyoruz. Gerrit özgür web tabanlı kod gözden geçirme aracıdır. Gerrit'e yama göndermek için gerekli adımlar [burada](https://wiki.documentfoundation.org/Development/gerrit) anlatılmış.

<b>Adımlar:</b>

{% highlight js %}
 $ ./logerrit setup 
{% endhighlight %}

komutunu çalıştırıyoruz. Daha sonra /home/[username]/.ssh/id_rsa.pub içeriğini ayarlar kısmındaki SSH Public Keys kısmına ekliyoruz.

<i>[Daha önce oluşturulmamış ise; "$ ssh-keygen " komutuyla anahtarımızı oluşturuyoruz.]</i>

{% highlight js %}
 $ ./logerrit test 
{% endhighlight %}

komutu sorunsuz çalışıyorsa gerrit aracını kullanabiliriz.

Daha sonra:
{% highlight js %}
 $ git checkout -b <yeni_dal_adi>
 $ git add file[file]
 $ git commit 
 libreoffice$ ./logerrit submit master 
{% endhighlight %}

komutları ile yamanızı gerrite gönderebilirsiniz.

<i><b>Notlar:</b></i>
<i>(Değişiklik yaptığınız dizinin bir üst dizinindeyken " $ git add . " komutunu kullabilirsiniz.)</i>
<i>$ git commit dediğimizde,commit mesajının başına tdf#<bug_id> diyerek bug numarası ile ilişkilendirmelisiniz. Tam yapı:

	tdf#<bug_id>  <commit_mesaji>

<i>şeklinde olmalıdır.</i>

<b>Yeni versiyon commit göndermek için gerekli adımlar da [burada](https://wiki.documentfoundation.org/Development/gerrit/SubmitPatch) anlatılmış. Kısaca:</b>

{% highlight js %}
 $ git checkout -b <dal_adi>
 $ git add .
 $ git commit --amend
 libreoffice$ ./logerrit submit master 
{% endhighlight %}


### 7. adım: Katkıcı listesine isim ekleme

İlk yamanız kabul edildikten sonra [listeye](https://wiki.documentfoundation.org/index.php?title=Development/Developers) isminizi eklemelisiniz.

<i>[Not: Edit diyerek kendinizi ekleyebilirsiniz. Alfabetik sıraya dikkat ediniz.]</i>










