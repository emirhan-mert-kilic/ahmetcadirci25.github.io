---
title      : "Arduino Programlama"
description: "Arduino Programlama... Hobi uygulamaları için geliştirilmiştir. Açık kaynak ve yazılım / donanım geliştirilebilir."
date       : 2016-11-05 22:53:13
categories : [Kod, Program]
tags       : [Arduino, Arduino Uno]
image      : "/images/arduino-uno-r3-usb-kablo.png"
comments   : true
---

Arduino Programlama... Hobi uygulamaları için geliştirilmiştir. Açık kaynak ve yazılım / donanım geliştirilebilir.

#### Hedefler

* Analog ya da dijital giriş-çıkış devre elemanları ile mikrodenetleyiciye
arasında bilgi alışverişinin sağlamak
* Kapalı döngü otomatik kontrol uygulaması için mikrodenetleyiciyi
programlayabilmek
* Mikrodenetleyiciler için assembly dili ile program yazabilmek ve
hataları düzeltebilmek
* Problemi analiz ederek en uygun mikrodenetleyiciyi seçebilmek

### İçindekiler

1. [Arduino Uno R3 + USB Kablo](#arduino-uno-r3--usb-kablo)
2. [Arduino IDE](#arduino-ide)
3. [Sistem Tasarımında Mikrodenetleyiciler Ne Zaman Tercih Edilir?](#sistem-tasarımında-mikrodenetleyiciler-ne-zaman-tercih-edilir)
4. [Sistem Tasarımında Mikrodenetleyiciler Ne Zaman Gerekmez?](#sistem-tasarımında-mikrodenetleyiciler-ne-zaman-gerekmez)
5. [Gömülü Sistemlerdeki Genel Kontrol Yapısı](#gömülü-sistemlerdeki-genel-kontrol-yapısı)
6. [Kontrol Edilebilir Sistemler](#kontrol-edilebilir-sistemler)
7. [Örnek: Akıllı Testere](#örnek-akıllı-testere)
8. [Sensör + Sinyal Düzenleyici](#sensör--sinyal-düzenleyici)
9. [Güç Kaynakları](#güç-kaynakları)
10. [Güç Arayüzü](#güç-arayüzü)
11. [Aktuatör](#aktuatör)
12. [Kullanıcı Arayüzü](#kullanıcı-arayüzü)
13. [Denetleyici Donanımı](#denetleyici-donanımı)
14. [Denetleyici Yazılımı](#denetleyici-yazılımı)
15. [Mikrodenetleyici Üreticileri](#mikrodenetleyici-üreticileri)
16. [Neden Arduino ?](#neden-arduino-)
17. [Örnek Arduino Shields](#örnek-arduino-shields)


#### Arduino Uno R3 + USB Kablo

{% include picture.html image_id="/images/arduino-uno-r3-usb-kablo.png" imagealt="Arduino Uno R3 + USB Kablo" %}

**Teknik Özellikler:**

* ATmega328 Mikrodenetleyici
* 7-12V Giriş Voltajı
* 14 Dijital G/Ç Pini
* 6 PWM Çıkışı
* 6 ADC Girişi
* 16MHz Çalışma Frekansı
* 32KB Flash Hafıza

#### Arduino IDE

{% include picture.html image_id="/images/galeri/arduino-ide.png" imagealt="Arduino IDE" %}

* Son sürümüne [www.arduino.cc](http://www.arduino.cc){:target="_blank"}{:rel="nofollow noopener noreferrer"} resmi internet sitesinden ulaşabilirsiniz.
* Tamamen ücretsizdir

#### Gömülü Sistem Nedir?

**Gömülü sitemler;**

* Sensörler
* Aktüatörler
* İşlem gücüne

Sahip, sistem performansını arttıran, daha fazla kapasiteye sahip çok yönlü
sistemlerdir.

#### Sistem Tasarımında Mikrodenetleyiciler Ne Zaman Tercih Edilir?

* Sistemde işlem gücü gerekiyorsa
* Sistem karmaşıklığı azalıyorsa
* Aynı işi yapabilmek için kullanılan ayrık devre elemanlarının maliyetini
düşürebiliyorsak
* Sistemde çeşitli sensör ve aktuatör kullanımı varsa
* Başka sistemler ile iletişim gerekiyorsa

#### Sistem Tasarımında Mikrodenetleyiciler Ne Zaman Gerekmez?

* Eğer sistemin işlem yükü çok az ya da işlem yükü barındırmıyorsa
* Ayrık devre elemanları kullanarak daha kolay ve ucuza
üretilebiliyorsa
* Mikrodenetleyici problem için yetersiz kalıyorsa;
    - Çok yavaş
    - Tek bir mikrodenetleyicinin yetemeyeceği büyüklükte bir sistemse

Bunun gibi sistem tasarımında dezavantaj getirebilecek herhangi bir durumda mikrodenetleyici kullanımı tercih edilmez.

#### Gömülü Sistemlerdeki Genel Kontrol Yapısı

{% include picture.html image_id="/images/galeri/gomulu-sistemlerdeki-genel-kontrol-yapisi.png" imagealt="Gömülü Sistemlerdeki Genel Kontrol Yapısı" %}

#### Kontrol Edilebilir Sistemler

* Mekanik
* Elektrik
* Elektromekanik (Mekatronik)
* Biyolojik
* Termodinamik
* Kimyasal
* …………………

#### Örnek: Akıllı Testere

* Elektrikli tezgah testere dikkat etmezsek parmaklarımınız kesebilir.
* Bu durumdan nasıl korunabiliriz?
* Vücudumuz iletkendir ve genellikle tahtadan daha yumuşaktır. Bu iki
ipucu problemin çözülmesinde bizlere yardımcı olabilir.

{% include picture.html image_id="/images/galeri/akilli-testere.png" imagealt="Akıllı Testere" %}

* Akıllı testere kesici kısmına ufak bir elektrik sinyali uygulayabilir.
* Sensör ve DSP sayesinde sinyal izlenebilir.
* Testerenin kesici kısmı vücuda dokunduğu zaman elektrik sinyalinde
değişiklik meydana gelir.
* Değişim güvenlik sistemini devreye sokar.
    - Tablo üzerinde alüminyum firen kilit sistemi devreye girer
    - Dönen kesici kısmın momentumu sayesinde elektrikli testere tezgah
    altına sokulabilir.
    - Motorun elektrik enerjisi kesilir.

#### Sensör + Sinyal Düzenleyici

* «Kapalı Döngülü Sistemler» için gereklidir.
* (Peki sensör kullanılmazsa sistem ne diye adlandırılır?)
* Sistem değişkenleri için ölçümler önemlidir.
* Ölçümler işlemci tarafından beklenen sinyal şekillerinde
dönüştürülmelidir.
* Düzenleme işlemi; sinyalin genliğini değiştirme, ofset ayarlama,
filtreleme, vb. denetleyici elemanın veriyi anlamlandırması için
gerekli adımları içerebilir.

#### Güç Kaynakları

* Birden fazla gerilim seviyesine ihtiyacımız olabilir (+5V, ±12V, ±24V,
vb.)
* Bazen güç kaynakları elektrik dışında başka sistemlerin beslenmesinde de kullanılabilir (hidrolik, pnömatik, vb.)
* Belki kuvvetli akım ve düşük akım sinyallerinin ikisi de kullanılması gerekebilir.

#### Güç Arayüzü

* Genellikle bir güç yükselteç katına ihtiyacımız vardır.
* Aktüatör tarafından talep edilen gücü kontrol edilebilir olması
gerekir.
* Genellikle analog, PWM (Pulse Width Modulation) ile de mümkün

#### Aktuatör

* Enerji dönüşümünü gerçekleştiren devre elemanıdır.
* Enerjiyi kontrol edilmek istenen fiziksel büyüklüğe çevirir.
* Motor, fren, pompa, selonoid, doğrusal atuatörler, flapeler, vb.

#### Kullanıcı Arayüzü

* Kullanıcıdan giriş komutları ve parametreler alınabilir.
* Kullanıcı bilgilendirilebilir.
* Kullanıcı arayüzleri;
    - GUI (Graphical User Interface)
    - Ölçüm
    - Nümerik Okuma
    - Uyarı lambaları
    - Vb. olabilir.

#### Denetleyici Donanımı

* Hesaplama (Analog veya dijital)
* Mikrodenetleyici
* İletişim devresi
    - Diğer cihaz ya da donanım bileşenleri ile
* Diğer devre bileşenleri
    - Pullup/Pulldown dirençleri
    - Analog işaret işleme

#### Denetleyici Yazılımı

* C / C++ / Arduino IDE birçok işlem için yeterli
* Assembly Dili yüksek hız gerektiren uygulamalar için
* FPGA (Field Programmable Gate Array) çok yüksek hızlı uygulamalar için ,VHDL (VHSIC «Very High-Speed Integrated Circuit» Hardware Description Language)

#### Mikrodenetleyici Üreticileri

* AMCC
* Atmel
* Comfile Technology Inc.
* Coridium
* Cypress MicroSystems
* Dallas Semiconductor
* Elba Corp.
* Freescale Semiconductor
* Fujitsu
* Holtek
* Infineon
* Intel
* Microchip Technology
* National Semicondutor
* NEC
* Parallax, Inc.
* Philips Semiconductors
* PICAXE
* Renesas Technology
* Silabs
* Silicon Motion
* STMicroelectronics
* Texas Instruments
* Toshiba
* Western Design Center
* Ubicom
* Xemics
* Xilinx
* ZiLOG

#### Neden Arduino ?

* Hobi uygulamaları için geliştirilmiştir.
* Ucuzdur.
* IDE (Integrated Development Environment) birçok platform için geliştirilmiştir (Mac, Windows, Linux)
* «C» ile basit, anlaşılır programlama imkanı
* Açık kaynak ve yazılım / donanım geliştirilebilir.
* Arduino Shields

#### Örnek: Arduino Shields

* VGA Kamera
* GPS (Global Positioning System)
* LCD Ekran
* Eternet
* WiFi
* Motor Kontrol (DC, adım motoru)
* Load Cell
* İvme ölçer / jiroskoplar
* LED göstergeler
* Hafıza Kartları
* Hava sensörleri
* Röleler
* Robotik
