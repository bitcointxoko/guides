LNDhub-ek zure zorroa erraz inportatzea ahalbidetzen du bateragarriak diren aplikazioetan. Bitcoin Txoko LNbits zorroa progresiboko web aplikazio (PWA) modura gorde dezakezun arren zure telefonoan, [Zeus](https://zeusln.app/) edo [BlueWallet](https://bluewallet.io/) bezalako aplikazio natibo batek erabiltzaile-esperientzia hobea eta segurtasun handiagoa eskaintzen du. 

[Alby](https://getalby.com/) erabiliz, zorroa zure nabigatzailearen luzapenean ere inporta dezakezu, webgunean Lightning ordainketak egiteko eta Nostr zap-ak egiteko erraztasun handiagoz. Zorionez, zorro hauek guztiek hizkuntza komun bat ulertzen dute, [LNDhub](https://github.com/BlueWallet/LndHub/tree/master) izenekoa.

Gida honetan, zorroa zure nabigatzailera eta telefonora nola inportatu azalduko dugu. Zorroa nabigatzailean eta telefonoan erabili nahi baduzu, hasi [Alby konfigurazioarekin](#Alby), pausoetako batek zorroa Zeus-era erraz inportatzeko aukera emango baitizu. Baina zorroa soilik zure telefonoan erabili nahi baduzu, zuzenean [Zeus atalera](#Zeus) jo dezakezu.

## Alby

nostr:nprofile1qqsyv47lazt9h6ycp2fsw270khje5egjgsrdkrupjg27u796g7f5k0s8jq7y6 nabigatzailearen luzapena da, Lightning eta Nostr nabigatzailera ekartzen dituena. [WebLN](https://www.webln.dev/) protokoloa erabiliz, luzapenak webguneetan fakturak automatikoki detekta eta ordaintzen ditu, eta Lightning bidez webguneetan saioa hasteko aukera ematen du. Gainera, Lightning gune gogokoenetan aurrekontuak ezar ditzakezu. Luzapen honek [NIP-07](https://github.com/nostr-protocol/nips/blob/master/07.md) protokoloa erabiliz Nostr sinadura gisa ere funtziona dezake, zure giltza pribatua web bezeroetan sartzea baino askoz seguruagoa dena.

### Zer behar dut?

- Chrome edo Firefox luzapenak onartzen dituen web nabigatzailea.
- LNbits zorroa. Oraindik zorro bat ez baduzu, joan [gure zorroen orrira](https://bitcointxoko.com) eta sortu bat.
- (Aukerazkoa) Zeus konfiguratzeko mugikor bat.

### 1. LNDhub luzapena gaitzea zure LNbits zorroan

Nabigatzailean, joan zure zorroaren estekara. Egin klik Extensions atalean eta gaitzazu `LNDhub` luzapena. Gaitu ondoren, joan LNDhub luzapenaren orrira.

### 2. Alby luzapena instalatu

Joan [getalby.com](https://getalby.com/)-era eta egin klik `Add Browser Extension` botoian. Instalatu luzapena zure nabigatzailearen luzapen dendetik. Ezarri desblokeatzeko pasahitza eta gorde toki seguruan.

### 3. Inportatu Alby-ra

![alby-config](https://cdn.satellite.earth/2074a44ea548ce28368d0aba2d54eafdc698159c5ee0956afa87fa155e3b511d.webp)

Hurrengo pantailan, aukeratu `Connect`, eta ondoren aukeratu `LNDhub`. Itzuli zure LNDhub luzapenera eta kopiatu konexioaren URL-a. Itsatsi hori LNDhub esportazioaren URI eremuan. Sakatu `Continue`. Orain LNbits zorroa LNDhub bidez konektatuta eduki beharko zenuke!

💡 Aukeratu dezakezu Invoice URL eta Admin URL artean. Bi hauek Alby-ri zure LNbits zorroarekin elkarreragiteko baimen desberdinak ematen dizkiote:
- *Invoice URL*-ak fakturak sortzea eta ordainketak jasotzea ahalbidetzen du.
- *Admin URL*-ak ordainketak bidaltzeko aukera ere ematen du.
  
### 4. (Aukerazkoa) Zeus konfiguratu Alby-rekin

![alby-export](https://cdn.satellite.earth/8807b296bb8bd6086a795616cc49068a17d93df450d0a65ce3818e5539eb6a09.webp)

Orain LNbits zorroa Alby-rekin konektatu duzunez, Zeus-en ere erraz inportatu dezakezu. Ireki luzapena, egin klik zure zorroaren izenean, eta joan `Account Settings` atalean. `Account` azpian aurkituko duzu `Connect your mobile wallet` aukera. Sakatu `Connect`, eta Zeus-ekin eskaneatzeko QR kode bat erakutsiko dizu.

Zeus aurretik instalatu ez baduzu, joan [zeusln.app](https://zeusln.app/)-era eta deskargatu Zeus zure mugikorreko sistema eragilerako. Zeus deskargatu ondoren, joan `Settings` > `Add a new node` atalera. Hemen, Alby-k erakusten dizun QR kodea eskaneatu eta zorroa inportatu dezakezu.

Listo! Orain Lightning-aren indarra zure eskuetan duzu. Jainko baten moduan sentitzen al zara jada?

## Zeus

nostr:nprofile1qqsrf5h4ya83jk8u6t9jgc76h6kalz3plp9vusjpm2ygqgalqhxgp9g84ctjf kode irekiko aplikazio bikaina da, zure nodo propioa mugikorrean konektatzeko aukera ematen duena. Lightning nodo nagusi guztiak onartzen ditu, hala nola LND, CLN eta Eclair, bai eta Tor bidezko zein clearnet bidezko konexioak ere. Azkenaldian, beren LSP (Lightning Service Provider) propioa iragarri dute.

### Zer behar dut?

- Android edo iOS telefono bat.
- LNbits zorroa ikusi ahal izateko beste gailu bat (QR kodea eskaneatzeko).
- LNbits zorroa eskuragarri izatea. Zorro bat oraindik ez baduzu, joan [gure zorroen orrira](https://bitcointxoko.com) eta sortu bat.

### 1. Zeus deskargatu

Deskargatu Zeus aplikazioa zure sistema eragilerako [hemen](https://zeusln.app). 

### 2. LNDhub luzapena gaitzea zure LNbits zorroan

Zure LNbits zorroaren orrian, egin klik `Extensions` atalean eta gaitzazu `LNDhub` luzapena. Gaitu ondoren, ireki LNDhub luzapenaren orria.

### 3. Inportatu Zeus-en

Joan `Settings` > `Add a new node` atalera Zeus-en. Eskaneatu nahi duzun zorroa inportatzeko.

💡 Aukeratu dezakezu Invoice URL eta Admin URL artean:
- *Invoice URL*-ak fakturak sortzea eta ordainketak jasotzea ahalbidetzen du.
- *Admin URL*-ak ordainketak bidaltzeko aukera ere ematen du.

QR kodea eskaneatu ondoren, Zeus-en eremu guztiak automatikoki beteko dira. Zorroarentzat ezizena ere gehitu dezakezu.

![zeus-config](https://cdn.satellite.earth/3be62f55d32460b7aa33d58fd9c25f3260e379ddde60fa1fe2c99016915da8b3.webp)

Orain, `Save Node Config` sakatu eta zorroa zure mugikorretik kontrolatu dezakezu!

### Bonus

Zeus-ek ezaugarri interesgarriak ere eskaintzen ditu, hala nola gai pertsonalizatuak, prezioen bihurketak, lurker modua eta biometria bidezko egiaztapena. Gida honen esparrutik haratago doazen ezaugarriak dira hauek, baina aplikazioa erabili eta zuk zeuk aurkitu ditzakezu!
