---
layout: post
title: LibreOffice İçin Eklenti Oluşturma
---

Selamlar,

LibreOffice çeşitli özelliklere sahip bir ofis yazılımıdır ancak ek özelliklere ihtiyacınız olabilir. Bunun için eklentileri kullanabilirsiniz.

Eklentiler, eklenebilen/kaldırılabilen ana programdan bağımsız araçlardır. Standart LibreOffice bileşenlerine yeni işlevler ekleyebilir ya da mevcut işlevselliği kolaylaştırabilir.

[Eklenti Marketinden](http://extensions.libreoffice.org/) indirip deneyebilirsiniz.

*****LibreOffice eklenti yapısının nasıl olduğundan yazmış olduğum küçük bir örnek yardımıyla bahsedeceğim.***

***.oxt*** formatındaki sıkıştırılmış dosyayı açtığımızda tam yapı şu şekildedir:

<p><img src="http://feyzayavuz.github.io/assets/by1-1.png" /></p>

Klasörde bulunan tüm dizin ve dosyaların eklenti içerisinde bir görevi var.  

***Dosyalar:***
---------------

 **Addons.xcu** -> Eklentiyi çalıştırdığınızda arayüzde görüntülenecek değişiklikleri barındırır.

 **build** -> Eklentide bir değişiklik yaptığınızda bu betiği çalıştırarak yeni bir "eklentiadi.oxt" dosyası oluşturabilirsiniz.

 **description.xml** -> Eklenti yöneticide görüntülenen eklentinin simgesi,adı, açıklaması gibi özelliklerinin (description dizini içerisinde bulunan dosyaların) dosya yolları bulunur.


 **extensionname.txt** -> İçerisinde eklenti adı bulunur "eklentiadi.oxt" şeklinde.

 **Hello.py** -> Eklentinin yapacağı iş bu dosyada tanımlanır.

***Dizinler:***
---------------

 **description** -> İçerisindeki license.txt dosyası lisans metnini oluşturur, description.txt dosyasının içeriği ise eklenti yöneticiye uzantıyı ekledikten sonra eklentinin açıklaması olarak görünmektedir.

**images** -> Eklentinin simgesi bu dosya içerisinde bulunur.

**META-INF** -> manifest.xml dosyası bulundurur bu dosya içinde paketin içindeki tüm dosyaların bir listesi, paketteki her dosyanın media tipi bilgileri bulunur.

Eklenti yöneticiden eklentiyi kurmak için;

	- Add
	- .oxt uzantılı dosyayı seç
	- Lisans sözleşmesini kabul et
	- LibreOffice'i yeniden başlat.



<p><img src="http://feyzayavuz.github.io/assets/by1-2.png" /></p>

*Bu eklenti araç çubuğuna bir buton ekliyor ve butona tıkladığınız "Hello World!" çıktısı veriyor.*

<p><img src="http://feyzayavuz.github.io/assets/by1-3.png" /></p>

Eklentiyi [github'a](https://github.com/feyzayavuz/HelloWorld) koydum. Eklentinin nasıl yazıldığını anlamak için temel bir örnek.


Not: Bozuk bir eklentiyi çalıştırınca, kaldırmak istediğimizde sorunla karşılaşıyoruz.

<p><img src="http://feyzayavuz.github.io/assets/by1-4.png" /></p>

Bu bozuk eklentileri eklenti yöneticiden kaldırmak için:

<b> /home/user/.config/libreoffice/4/user/uno_packages/cache/uno_packages/ </b> içerisinde hangi eklentiyi kaldırmak istiyorsak onun .tmp_ uzantılı dizinini siliyoruz. 

Geliştirici sürümünde aynı sorunla karşılaştığınızda ise:

<b> libreoffice/instdir/user/uno_packages/cache/uno_packages/ </b> içinde bulunan ilgili .tmp_ uzantılı dizini siliyoruz.

