<h1 align="center"> Naruno | Baklava Testnet</h1>

<div align="center">

 
![dark background animated small size logo](https://user-images.githubusercontent.com/108215275/225014938-75cace5d-2813-4667-b36b-d921395670bd.gif)

 
  ## Naruno Resmi Linkler: [Twitter](https://twitter.com/NarunoOfficial) | [Discord](https://discord.gg/NGapgYxd) | [Website](https://naruno.org/)| [Github](https://github.com/Naruno) | [NarunoDocs](https://docs.naruno.org/)
  
</div>

> ## ***Bu rehberi hazırlarken yararlandığım kaynak [NarunoDocs](https://docs.naruno.org/)***
> 
> ## ***Arkadaşlar Naruno Baklava Testnet başladı. Daha önce mail alıp cüzdan oluşturduysanız cüzdanınıza test tokenları gönderildi, artık baklava testnete katılabilirsiniz***
> ### ***Eğer daha önce kurulum yapıp cüzdan oluşturmadıysanız önce o işlemi yapın [CüzdanOLuşturma](https://github.com/0xSocrates/Testnet-Rehberler/blob/main/Naruno/C%C3%BCzdan-Olu%C5%9Fturma.md).***
> ### ***Bir tarayıcıya aşağıdaki linkte cüzdan adresinizi yazıp bakiyenizi kontrol edin.***
```
http://test_net.1.naruno.org:8000/balance/get/?address=CüzdanAdresi
```
# ***İlk olarak önceki kurulumu yeni versiyona güncelliyoruz***
> # ***ÖNEMLİ***
> ### ***Narunoyu Güncellemeden önce cüzdanı yedekleyip güncelledikten sonra tekrar import etmek gerekiyor***
> ### Bu adımda hata yapmayın



> ## ***Önce yedekleme (cüzdan oluşturduktan sonra yaptıysanız tekrar yapmanıza gerek yok)***
```
cd Naruno
narunocli --narunoexport
```
![image](https://user-images.githubusercontent.com/108215275/225010543-43bc6d17-ad68-4f7d-b0bd-6c4f062f4917.png)

>  ### ***Ardından sunucuda `/usr/local/lib/python3.8/dist-packages/naruno/backups/` altındaki .zip dosyasını bilgisayarınıza indirin***

> ##  ***Şimdi Nodumuzu güncelliyoruz***
```
cd /root
pip3 uninstall Naruno -y
```
![image](https://user-images.githubusercontent.com/108215275/225011529-403c221d-a953-49fc-beea-bc27ab463d2a.png)

```
pip3 install naruno==0.45.1
```

![image](https://user-images.githubusercontent.com/108215275/225011890-40309674-7ac4-43b3-8500-aa318d8de1c2.png)

> ## ***Cüzdanı import etme***

> ### ***Bilgisayarınıza indirdiğiniz .zip dosyasını sunucuda `/root` klasörü altına yükleyin Ardından aşağıdaki komutta `dosyaismi.zip` yazan yeri değiştirerek import işlemini tamamlayın***
```
narunocli --narunoimport /root/dosyaismi.zip
```
![image](https://user-images.githubusercontent.com/108215275/225013106-476299cd-8d5f-44d5-8dfb-ce7076b6fdbe.png)

# ***Kurulum***
```
cd /root/Naruno

narunocli --baklavaon

pip3 install naruno-api
```
![image](https://user-images.githubusercontent.com/108215275/225013950-37c161c7-6fe9-433f-9f49-711ee777f377.png)

# ***Node başlatma***
```
narunoapi &
```
### ***Bu komuttan  sonra node arka planda çalışmaya başlıyor***

# Sıradaki adım Naruno üzerinde bir app oluşturmak
> Buradaki örnekte mesaj gönderebileceğimiz bir app yapıyoruz.
 
> Önce root dizinine inin
```
cd /root
```
> Mesaj göndermek için bir python dosyası oluşturuyoruz
```
nano send.py
```

> Aşağıdaki komutları send.py içine kopyalayın.. Ve " " içindekileri aşağıdaki notlar gibi düzenleyin
 
> `Your_App_Name` yerine sizin oluşturacağınız uygulama adı örn:whatshapp
>
> `Your_Wallet_Password` yerine sizin cüzdan oluştururken kullandığınız şifreyi yazın
>
> `Your_Action_Name` yerine sizin oluşturacağınız uygulama adı örn:send_message
>
> `Your_Data` yerine yollayacağınız mesajı yazın örn: Gecen aksam neden bana selam vermedin :)
>
> `Recipient_Address` yerine mesajı ileteceğiniz cüzdan adresini yazın

> Bu işlemleri yaptıktan sonra CTRL ve X ardından y ve Enter tuşuna basıp kaydedin.
```
from naruno.apps.remote_app import Integration

integration = Integration("Your_App_Name", password="Your_Wallet_Password", host="localhost")

from naruno.lib.settings_system import baklava_settings
baklava_settings(True)

integration.send("Your_Action_Name", "Your_Data", "Recipient_Address")
```
> Dosyaya yetki verin
```
chmod +x send.py
```
> Çalıştırın
```
python3 send.py
```
**
> Şimdi de gelen mesajları görmek için bir python dosyası oluşturun( root dizini içinde olmalısınız)
```
nano get.py
```
> Aşağıdaki komutları get.py içine kopyalayın.. Ve " " içindekileri aşağıdaki notlar gibi düzenleyin

> `Your_App_Name` yerine sizin oluşturacağınız uygulama adı örn:whatshapp
> `Your_Wallet_Password` yerine sizin cüzdan oluştururken kullandığınız şifreyi yazın

> Bu işlemleri yaptıktan sonra CTRL ve X ardından y ve Enter tuşuna basıp kaydedin.


```
from naruno.apps.remote_app import Integration

integration = Integration("Your_App_Name", password="Your_Wallet_Password", host="localhost")

from naruno.lib.settings_system import baklava_settings
baklava_settings(True)

print(integration.get())
```
> Dosyaya yetki verin
```
chmod +x get.py
```

> Çalıştırın
```
python3 get.py
```

> ### ***Arkadaşlar yapılacak işlemler şu an için bu kadar, gelişmeler için Naruna hesaplarını takip etmeyi unutmayın***
> ### ***Buradaki örnekte bir mesaj gönderme uygulaması yaptık. Python dilini bilen herkes istediği gibi uygulama yapıp test edebilir***
> ### ***Eğer bu konuda deneyiminiz varsa ve Naruno üzerinde bir uygulama yapmak istiyorsanız bu konuda discordda yardım alabilirsiniz ve ekiple görüşebilirsiniz***


































