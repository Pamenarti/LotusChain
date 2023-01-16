## PRW -  Lotuscoin Core integration/staging tree (yes tree)

This is the ultra-stable backbone full node and wallet for lotuscoin,
the project aiming to be the longest lived and cheapest public blockchain.  

> openssl version
OpenSSL 1.1.0g  2 Nov 2017

If you have OpenSSL v. 1.0.x please use the "lotuscoin-openssl-1.0" version of this repository located here:  
http://github.com/Pamenarti/lotuschain-openssl-1.0.git

The Lotuscoin block chain is a log structured database.
The money supply is logarithmic.
The unit is log.

## Technical Details:
- RPC Port = 9338
- P2P Ports = 8338 (testnet 18338)
- In Wallet mining/logging = Console, "setgenerate true"
- 120 Second Block Target, Diff Retarget every 1 hour
- 30 Confirms for spendable-coins
- Block reward = Harmonic Series
- 1000000/nHeight logs  (after first 100 blocks which form unspendable forest of 5187377 logs) 
- Money Supply = 1000000*(log(nHeight) + gamma)     gamma=Euler-Mascheroni constant 
- ECDSA curve: X9_62_prime256v1 
- Algo = Pure Skein2 (double skein) Bruce Schneier is a lumberjack and NSA didn't choose this algo.

## Build Instructions

You will need these dependencies or equivalent:

```
sudo apt-get install git build-essential libboost-all-dev libssl-dev qt-sdk libdb-dev libdb++-dev libminiupnpc-dev libqrencode-dev 
```

#### Get the source with this command:
```
git clone https://github.com/Pamenarti/lotuschain.git
```

## This project is a fully armed and operational bitcoin-core ported to the lotuscoin network.  

#### Dedicated to Sipa, Nullc, and Coblee.  Props and Kudos.  

#### Three tasks have made this port complete:

1) Skein2 hash function for Proof Of Work inserted
2) prime256r1 for ECDSA signatures (including backport to OpenSSL and removal of libsecp256k1)
3) Logarithmic supply curve for long-term economics

Voila - we now have a segwit-enabled lotuscoin client in place for those who would like to use it.


https://github.com/Pamenarti/lotuschain.git

Other clients including Lotuscoin-minimal and Fo-Realz-Lotuscoin are also available.  

## Mining (lotuscutting)

#### To start lotuscutting with lotuscoind, simply launch it like this: 
```
./lotuscoind setgenerate true
```
For the graphical client, simply go into the debug window (under Help) and type:

```setgenerate true```
---




# Güncelleme Notları: 1. ve 2. testnet sonucunda tespit edilen sorunlar, hatalar, buglar ve iyileştirme için yapılan geliştirmelerin listesi.

- CPU Miner ve GPU miner Diff paylaşım mekanizması düzeltildi.
- CPU anlık TXID blok çıkarımında ki anlık kasma hataları giderildi.
- CPU blok çıkarımında oluşturulan maks Voltaj/POWER %20 oranında idi giderildi.
- GPU diff hatalı Voltaj/POWER harcama giderildi.
- TXID blokları çift işlem orphan çıkarılmama sorunu giderildi.
- %51 invout hesaplama hataları giderildi
- Hardfork ve halving geçişleri test edildi ve görünen sorunlar KOD tabanına işlenerek iyileştirildi.
- Blok başı çıkarılan ödüllerinadil dağıtım problemleri sorunu iyileştirildi.
- Zincir blokları anlık blok çıkarım sırasında oluşan kasma sorunları giderildi.
- Vout miner pay tree problemleri test edildi görünen hatalar giderildi
- CPU+GPU Miner adil dağıtım sorunları zincir temelinde iyileştirildi.
- Node ve QT-Wallet bağlantı (connect) gecikme sorunları iyileştirildi.
- lotuscoin-cli + lotuscoin-txt-cli zincir çekirdek dosyaları yaratılarak Master-Node kullanımı için 3. testnet e aktif edildi, sorunları giderildi
- lotuscoin-cli peer-to-info parametresi eklendi.
- lotuscoin-cli getinfo parametresi genişletilerek "Sync : True/False" çıktısı Json/parse fonksiyonu eklendi olarak.
- Peer-disconnect Kopma problemleri sorunları giderildi ve iyileştirildi.
- Node2Node bağlantı More-Connect sorunları ve banlanma veya banlama sorunları giderildi.
- White Node/IP özelliği eklendi ve sorunları giderildi (Node-R sistemi için yeni kodladığım ve gerekli bir özellikdi mecburen eklemek zorunda kaldığımız bir mini kod-eklentisidir.)
- Peer Json parse döküm hataları/sorunları giderildi.
- Peer Json döküm tıkanmaları ve BUG da kalma sorunları giderilerek, hızı iyileştirildi.
- UTXO paylaşım ve parçalanma hızı yükseltildi. ( default normalize de 0.1 saniye de parçalanma yaşanmaktaydı. Node-R sistemi dahil olduktan sonra json data veriminde yavaşlama yaşanmıştı.) 
- UTXO pay back/bildirimi (gönderimden kalan küsüratın cüzdana geri dönme hızı ve hesaplamalarında ki hız arttırıldı.) 
- Node-R protokolü + aktivasyon ve yeni özelliklerin sisteme dahil edilerek peer/info ön bilgileri yazıldı ve giriş sorunları halledildi.


- 3. testnet için Node-R özelliği çekirdek sistemine eklenmek üzere plana alınacak 3. testnet de aktif edilmek üzere kodlanacaktır. fakat bir hayli kod yazılacağından. Planda olmayan 4. testnet yol haritasına eklenebilme olasılığı çok yüksektir. Bu yüzden 3 testnet sırasında Node-R kodlaması süreci daha önce de başlayabilir 3. testnet sonrasında da başlayacağından 4. testnet aktif edebiliriz.

 Node-R teşviki aktif edilmesi gereken bir Protokol olarak plana dahil edildiğinden Mainnet sürecinden önce 4. ve 5. testnet'ler yapılabilir. Aksi halde sistem sorunlu çalışacak ve HARDFORK yapılması olasılığı gün yüzüne çıkabilir. Hardfork yapılmaması için testnet'lerin uzun tutulması ve ince eleyerek sık dokumamız gereken bir KODlama süreci yaşamamız gerekiyor bunun için sabırla ve sukünet ile beklemeniz gerekmektedir.

 Malumunuz biliyorsunuz kodlama, testler, geliştirmeler, hata ayıklama, hata giderme, sorun bulma, kod/sistem/mekanizma analizi, Yeni gelişmeler ve gelişmelerin gibi bir çok iş ve işlerin hepsini tek başıma ve tek kişi olarak yaptığımdan bir hayli zaman, emek, çaba ve zorlayan bir süreç oluyor bu yüzden Sabrınız için Teşekkür ediyorum. 

## 3. Testnet gerekli kontroller yapıldı ve güncel kod verisi düzenlendi.
 sorunlar giderildi/FİX'lendi.  OPRTURN = Fair Share (adil pay) protokolü ve optimizasyonu zincir çekirdeğine eklenerek testleri yapıldı ve daha hızlı ödül dağılımı sağlandı. 

 Fair Share nedir ? ; kısaca anlatmak gerekirse, #Merkeziyetsiz sistemler de ve PoW protokollerin de Mine yapıldığında bir süre olgunlaşması beklenir ödüllerini, bu süreç sonun da hesaplamaları onaylanan veya "full calculation" tam hesaplama yapılan ödüller mainWallet yani ana cüzdanlara düşer ve kullanıma açılır.
 Ödüllerin olgunlaşmasının süresi kısaltılarak daha hızlı Olgunlaşan ödüller mekaniğe eklendi. Zincir kapatılıp açıldıktan sonra hızı ve Fair Share (adil pay) mekaniği, ödül dağılımın da ve olgunlaşan ödüller kısmında optimize edildikten sonra, Node-Mine yapan arkadaşlar bunu zaten fark edeceklerdir. 

şimdilik güncel düzeltmeler ve hata giderimi detayları bu kadar.

## #PLP #Maineable Coin olan #LTS'nin 3. Testnet aktif edildi. Local Node'larınız ile bağlanıp kazım yapabilirsiniz. 

Bir önceki 2. testnet de bulunan ve not alınan bütün sorunlar giderildi test edildi. Fakat aktif olarak, local 2 node yerine topluluk node'ları ve farklı Core,Proccess'lar ile, test edilmediğinden yatırımcıların ve Miner'ların tespit edilen ve bulunan sorunların giderilmesi adına. Farklı çeşitde donanım teçhizatlarımız kısıtlı olduğundan, hatalar/sorunlar/sıkıntılar ile ilgili geri bildirimleri göz önüne alarak, 3. testnet'i sağlıklı bir şekilde analiz ve gözlemler ile tamamlayacağımızı umuyorum. Malum tek başıma geliştirdiğimden, yeni 3. Testnet'imiz de "Woodcoin" yaratıcısı ve geliştiricisi aynı zaman da, eski LTC (litecoin) geliştiricilerinden" olan arkadaşım "funkenstein" bana işleri hızlandırmak adına, yardım edeceğini ve ekibe destek geliştirici olarak katkı sağlayacağını söylemek isterim. hem kodlama süresin de hem geliştirme aşamasında bir çok katkısı dokunacağını düşündüğümden, yardımlarının baya etkili olacağını söyleyebilirim. Aynı zaman da ben de "Woodcoin" Çekirdeğinin gelişiminde aynı şekilde destek geliştirici olarak yardımcı olacağımı söylerek anlaşma sağladık. Ekibimiz umarım uzman arkadaşlarla zamanla büyüyecektir. Bu sayede daha hızlı gelişim gösterebileceğiz.

Hali hazırda başka bir haber vermek isterim, Node-R protokolümüzü çok beğenen "funkenstein", Protokol geliştirmemiz bittikten sonra aynı şekilde kendi sistemleri olan "Woodcoin" de Node-R protokolümüzü ilerleyen süreçlerde aktif ederek kullanmayı düşünüyorlar. Node-R protokolü sağlıklı bir şekilde hayata geçirildikten sonra ki süreçte başka bir projenin bu protokolü kullanacağını bilmenizi isterim. (ayrıca ki bu anlaşma beni baya bişr mutlu etti açıkcası.). Protokolümüzün teşvik oluşturma açısından etkili, işlevsel bir protokol olacağını düşünmüştüm ve kendilerinin onaylamaları bu düşüncemi doğrular nitelikte oldu.
3. testnet de yapılacak işlemler kısaca. 

- Pool sistemi test edilerek aktif ve stabil hale getirilecek. (Pool = 3rd havuz sistemi/yazılımı)
- Pool sistemi Oto-ödeme sistemi test edilecek.
- Pool sistemi adil ödeme dağıtımı kontrol edilerek analiz edilecek.
- GPU-Mine ve Node-Mine mekaniği kazançları analiz edilerek oran hesaplamaları gözlemlenerek not alınacak.
- Node-R mekaniği kodlaması yapılarak sisteme entegre edilecek.
- Node-R add/remove/ban eklenecek.
- Node-R mekaniği ve Mine oranları, Adil dağıtım, Adil kazım miktarları gözlemlenerek not alınacak.
- Düzeltilen Peerinfo hataları kontrol edilerek aktif Node'lar da ki sorunların giderildiği gözlemlenecek yeni sorunlar not alınacak.
- Mining info parametresi sorunları giderildi analiz ve test edilecektir.
- Hali hazır da bulunan Blokzincir Mine Sistematik adil ödeme sorunları giderildi incelenecek.
- Mine sırasında OPreturn hataları tespit edilmişti test edilerek kontrol sağlanacak..
 ve dahası..

3. testnet ile başarılı bir şekilde geliştirmeye ve gelişime devam edeceğiz.


## contact :
~Paro, (c) 2019 (discord id : Paro#7842)


