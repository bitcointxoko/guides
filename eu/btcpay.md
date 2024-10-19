Merkatari bat zara eta zure negozioan Bitcoin onartzen hasteko prest zaude? Edo agian Bitcoin zale sutsua zara, tokiko negozioak Bitcoinen mundura erakartzeko gogoz? Beharbada, ez zaizu Bitcoin interesatzen, baina ordainketa-prozesadore azkar eta merke bat erabili nahi duzu edo web-denda sinple bat sortu nahi duzu? Galdera hauetakoren bati baiezkoa erantzun badiozu, gida hau zuretzat da. Bitcoin Txoko-k ostatatutako [BTCPay Server](https://btcpayserver.org)-en denda bat konfiguratu dezakezu eta zure produktuak eta zerbitzuak Bitcoinen truke saltzen hasi hamar minuturen buruan, doan.

## Zer behar dut?

Mugikor edo ordenadore bat baduzu eta posta elektronikoko kontu bat ere bai, orduan prest zaude!

## Kontu bat sortu

Bitcoin Txoko-n BTCPay Server-en kontu bat sortzea doakoa da. Joan [btcpay.bitcointxoko.com](https://btcpay.bitcointxoko.com) helbidera kontu bat erregistratzeko. Egiaztatu zure posta elektronikoa, bertan bitcointxoko@gmail.com helbidetik bidalitako mezu bat aurkituko duzu, baieztapen-esteka bat izango duena.

## Zure lehen denda sortu

Baieztapen-estekan klik egitean, dendaren sorrera orrialdera eramango zaitu. Eman zure dendari izen bat eta hautatu moneta lehenetsia eta prezio iturri hobetsia. Adibidez, *EUR* eta *Kraken* aukeratu ditzakezu, azken hau gomendatutako prezio iturria baita. BTCPay Server-ek zure produktuen edo zerbitzuen prezioa *EUR*-tik *Bitcoin*-era bihurtuko du, erosketa unean aukeratutako prezio iturriaren arabera.

## Zorro bat konfiguratu

Ordainketak onartzen hasteko, lehenik eta behin zure denda zorro batera lotu behar duzu. Transakzio handiak (500 EUR baino gehiago) maiz espero ez badituzu, Lightning zorro bat konfiguratzeko gomendioa egiten dizugu, eta une honetan (on-chain) Bitcoin zorroa ez erabiltzea gomendatzen da. Lightning zorroa erabiliz, transakzioak azkarragoak eta merkeagoak izango dira.

💡 **Lightning** sarea Bitcoin ordainketak jasotzeko sare ezin hobea da, transakzio berehalakoak eta komisiorik baxuenak eskaintzen baititu **on-chain** transakzioekin alderatuta. Horrela, zure negozioak eraginkortasunez eta kostu txikiarekin jaso ditzake ordainketak.

Lightning zorro bat konektatzeko modurik errazena LNDhub erabiltzea da, zure Lightning nodo propioa exekutatu beharrik ez baituzu izango. LNDhub zorro bat ez baduzu oraindik, ez kezkatu; Bitcoin Txoko-k doako LNDhub zorroak eskaintzen ditu, eta bost minutu baino gutxiago behar dira konfiguratzeko. Begiratu nostr:naddr1qqxnzd3exuerqdfkxccnyv3cqgs9n8m87l0hd9xxqwndqcmwzh4uvyxmwlw0637kuhg98pkcy8ana2grqsqqqa28nkyu7t zure LNDhub zorroa nola lortu jakiteko, eta prest zaudenean itzuli konfigurazioa jarraitzeko.

![connect](https://cdn.satellite.earth/038642b9f6e77623b7affb20adfce5af46a64d9cecb53c1cb651043a88a72597.webp)

Zure LNDhub zorroa prest dagoenean, jarraitu urrats hauek BTCPay kontuan konfiguratzen:
1. Joan zure BTCPay kontura eta `Wallets` aukera bilatu alboko barran, ondoren `Lightning` aukeratu.
2. Hautatu `Use custom node`.
3. Kopiatu zure LNDhub administrazio URL-a eta itsatsi konexioaren konfigurazioan.
4. Proba ezazu zure zorroaren konexioa.
5. Ondo joan bada, honako mezua agertu beharko litzateke: *Connection to the Lightning node successful, but no public address has been configured*. Ez kezkatu *"no public address has been configured"* atalaz, horrek zure nodo propioa exekutatzen ari bazara bakarrik du garrantzia.
6. Zorroaren konexioa arrakastaz probatu ondoren, sakatu `Save` botoia.
7. `Save` sakatu ondoren, `LNURL` atalean, desaktibatu `Enable LNURL` aukera. Egin aldaketak eta ez ahaztu berriro `Save` botoian klik egitea.
8. (Hautazkoa) Une honetan, gomendagarria da `Display Lightning payment amounts in Satoshis` aukera markatzea, Satoshitan zenbatutako ordainketa kopuruak irakurtzeko errazagoak baitira. Satoshi Bitcoin-en zatirik txikiena da; Bitcoin bat 100 milioi satoshik osatzen dute.

Jarraitu urrats hauek zure zorroa arrakastaz konfiguratuta izateko eta Lightning bidezko ordainketak onartzeko.

![config](https://cdn.satellite.earth/d0f30a95573894f674dd7e21646e583bcc69f1a5179556b8cc7853de1cf1bb02.webp)

💡 Zure Lightning nodo propioa erabiltzen ari bazara, konfigurazio prozesua antzekoa da. Ziurtatu zure nodo inplementaziorako konexio kate egokia ematen duzula.

## Saltoki puntua (PoS) sortu

Urrats honetara iritsi bazara, zorionak! Zati aspergarriena amaitu da, eta orain zure Saltoki puntua (Point of Sale, PoS) sortzeko unea iritsi da, BTCPay bidez zure lehen Bitcoin ordainketa onartzen hasteko!

Saltoki puntu bat sortzeko:
1. Joan `Plugins` > `Point of Sale` atalera.
2. Eman izen bat zure Saltoki puntuari eta sakatu `Create` botoia.

Jarraian, zure PoS aplikazioarekin egin ditzakezun gauza erraz batzuk azalduko ditugu. BTCPay-k ezaugarri asko ditu, baina gida honetan oinarrizkoak soilik azalduko ditugu, hasiera emateko.

💡 **Gogoratu** BTCPay Server-en saltoki puntu bat baino gehiago sor ditzakezula, bakoitza erabilera jakin baterako. Horrela, negozio desberdinetarako edo produktu eta zerbitzu berezietarako konfigurazio bereiziak izatea posible da.

### Teklatua (Keypad)

![keypad](https://cdn.satellite.earth/019bd809f089c02d44a10d1824a9226b89d0199f4eeef06d09f859fce1b97310.webp)

Demostrazio erraz baterako, PoS estilo gisa teklatuaren eredua erabiliko dugu.

1. Eman zure PoS-ari izen bat eta erakusteko titulua.
2. Hautatu `Keypad` estiloa `Point of Sale style` aukeraren azpian.
3. Sakatu `Save` eskuineko goiko izkinan, eta ondoren `View` sakatu zure PoS begiratzeko.

Ordainketak lehenago konfiguratutako LNDhub zorroan jasoko dira. Jolas ezazu fakturak sortzen eta deskontu eta tip (aholkularitza) aukerak aktibatuz. Gainera, telefono bat baduzu (adibidez, iPhone ez den bat) NFC teknologia onartzen duena, bezeroek NFC txartelak erabiliz ere ordain dezakete, hala nola BoltCard erabiliz (ikusi nostr:naddr1qqxnzd3e8qcr2wfn8qcrgwf4qgs9n8m87l0hd9xxqwndqcmwzh4uvyxmwlw0637kuhg98pkcy8ana2grqsqqqa28qjzxr4). Ez al da zoragarria?

💡 PoS estilo honen erraztasuna maximizatzeko, Keypad PoS zure telefonoan Progressive Web App (PWA) gisa gorde dezakezu sarbide azkarrerako. Mugikor gehienetako nabigatzaileetan aukera hau `Install App` edo `Gehitu orri nagusian` izenarekin agertzen da.

Horrela, zure negozioan Bitcoin ordainketak erraz onar ditzakezu, eta erabiltzaileek ere modu intuitibo batean ordaindu ahal izango dute.

### Product list (with cart)

![product-list-with-cart](https://cdn.satellite.earth/3f7572de5585455096375bf05ead665f2172f6c0dd3b2caa8f67e79f30b13b4e.webp)

Posible da saltoki puntu bat sortzea produktu zehatzekin, bakoitza bere prezioarekin. Ezaugarri hau erabil dezakezu kutxa sinple bat, bezeroen auto-ordainketa sistema edo web denda bat konfiguratzeko.

Nola sortu produktu-zerrendadun Saltoki Puntua:
1. Joan berriro alboko barrara eta aukeratu `Point of Sale`.
2. Oraingoan, `Point of Sale Style` azpian, hautatu `Product list with cart`. "With cart" aukerak bezeroari produktu bat baino gehiago aldi berean erosteko aukera ematen dio.
3. Zure produktuak sortu, edo zuzenean sakatu `Save` eta `View` produktu laginak probatzeko.

## Ondorioa

Gida honetan, zure negozioan Bitcoin onartzen hasteko BTCPay Server erabiliz jarraitu beharreko oinarrizko urratsak azaldu ditugu. BTCPay Server [proiektu irekia](https://github.com/btcpayserver/btcpayserver) da eta etengabe garatzen ari da. Askoz ere ezaugarri eta funtzionalitate gehiago eskaintzen ditu, hala nola Shopify integrazioa, crowdfunding eta ordainketen banaketa automatikoa. Gainera, zure denda pertsonaliza dezakezu gaikako diseinuekin, ordainketa-gune pertsonalizatuarekin, erabiltzaileen kudeaketarekin, posta elektronikoko jakinarazpenekin eta askoz gehiago.

BTCPay Server-en ahalmen guztiak aprobetxatu nahi badituzu, zure [Lightning nodoa konfiguratu](https://v2.minibolt.info/home/readme) eta zure [BTCPay zerbitzaria ostatatzea](https://docs.btcpayserver.org/Deployment/) gomendatzen dizugu. Informazio gehiago lortzeko, haien [dokumentazioa](https://github.com/btcpayserver/btcpayserver) eta [bideoak](https://www.youtube.com/@BTCPayServer) ikustea komeni da.

Zalantzarik edo galderarik baduzu, jakinarazi iezaguzu! Zure iritziak entzutea gustatuko litzaiguke eta galderak argitzen lagundu nahi dizugu.

Bitcoin Txoko komunitate ireki bat da. Gure zerbitzu guztiak dohaintzekin finantzatzen dira. Gida hau erabilgarria iruditu bazaizu, kontuan hartu gure zerbitzariak martxan mantentzen laguntzeko [dohaintza](https://fund.bitcointxoko.com) bat egitea. Eskerrik asko aldez aurretik!
