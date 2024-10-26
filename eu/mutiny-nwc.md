# Mutiny Wallet

**Mutiny Wallet** kode irekiko Bitcoin eta Lightning zorro autokudeatua da, eta nabigatzailean zein Android eta iOS (TestFlight, ordainpekoa) aplikazio natiboetan funtzionatzen du. Ez da bakarrik nostr-en bidez ukitu bakarrean autokudeatutako ordainketak bidaltzeko modurik erosoena, baita erabiltzaile berriak autokudeatutako Bitcoin-ekosistemara erakartzeko modurik errazena ere. Gida honetan, Mutiny taldeak nostr-en "magia" erabiliz hori nola gauzatu duen aztertuko dugu.

⚠️ **Mutiny Wallet** beta faseko softwarea da. Probak egiteko signet txanponak erabili, eta ez sartu galtzeko prest zauden diru kopurua baino gehiago.

## Mutiny abiarazi

Web Mutiny-k Lightning nodo bat exekutatu dezake web-nabigatzailean. Nola funtzionatzen du honek? Azalpen sinple bat ematearren, Lightning nodo bat osagai desberdinez osatuta dago, hala nola, gossip syncer, block explorer, egoera-makina eta sinatzailea. Mutiny-k atal horiek bereizten ditu, eta horrela, sinatzailea bakarrik gordetzen da tokian bertan; beste osagaiak urrunetik eskuratzen dira API bidez.

Mutiny zure nabigatzailean exekutatzeko, jo ezazu [hemen](https://mutiny.mempool.space/api). Ondoren, orria Aplikazio Aurreratu Progresibo (Progressive Web App) gisa gorde dezakezu sarbide errazagoa izateko. Nabigatzaile gehienetan, aukera hau "Aplikazioa Instalatu" edo "Gehitu Hasiera Pantailan" izenarekin agertzen da.

Bestela, Mutiny Bitcoin Txokok bere zerbitzarian autokudeatuta probatu dezakezu, baina ezaugarri batzuk, hala nola opariak eta nostr kontaktuak, oraindik ez dira erabilgarri. Eguneratzeak GitHub-en jarraitu ditzakezu.

### Bitcoin Txoko erabiltzearen alde egiten baduzu

Gogoan izan guk soilik aurrealdea, Lightning Network-era konektatzeko web-soket proxya eta egoerak gordetzeko Bertsio Anitzeko Biltegia (VSS) exekutatzen ditugula. Gossip syncer eta block explorer-erako, Mutiny-k eskaintzen dituen lehenetsitako aukerak erabiltzea gomendatzen dizugu. Horiek gehitzeko, jarraitu urrats hauek:

1. Joan **Ezarpenak > Zerbitzariak** atalera.
2. **Esplora** atalean, itsatsi `https://mutiny.mempool.space/api`
3. **RGS** atalean, itsatsi `https://scorer.mutinywallet.com/v1/rgs/snapshot/`
4. Beste eremuak lehenetsita agertu beharko lirateke, LSP barne.
5. Sakatu **Gorde**.

## Android

Mutiny-ren Android-erako APKa zuzenean GitHub-etik deskargatu daiteke. Android aplikazioak kudeatzeko, Obtainium erabiltzea gomendatzen dugu. Ikusi gure [Gida](https://github.com/mutiny-wallet).

## iOS (TestFlight)

Mutiny Wallet doan eskuragarri dago, baina **Mutiny+ harpidetza** eginez ezaugarri gehigarriak desblokeatu eta garapena lagun dezakezu ordainketa eginez.

Mutiny+ harpidetza egiteko, gutxienez 10.500 satoshi balantzea izan behar duzu Lightning-en Mutiny Wallet zorroan. Zorroa finantzatzeko prozesua gida honetan azalduko dugu geroago. Zorroa finantzatu ondoren, joan **Ezarpenak > Mutiny+** atalera harpidetza egiteko. Ordainketa egin ostean, sakatu iOS beta sarbidearen esteka Mutiny+ fitxan, TestFlight gonbidapena jasotzeko.

## Zorroa Finantzatzea

Mutiny zorroarekin transakzioak egiten hasteko modurik errazena Lightning ordainketa bat jasotzea da. Prozesu honetan, zuretzat kanal bat automatikoki irekiko du **Voltage Flow 2.0 LSP**-k. Horretarako, sakatu **Jaso** botoia, irakurri arretaz gutxieneko kanal tamainari eta konfiguratze gastuei buruzko abisua, eta ezarri jasotzeko zenbatekoa. Faktura ordaindu eta minutu gutxitan kanal bat martxan izango duzu.

Bestela, on-chain funtsak ere bidal ditzakezu Mutiny zorroan kanal bat zeure kabuz irekitzeko. On-chain saldoa baieztatzen denean, trukatzeko botoi bat agertuko da. Horri sakatuta, Lightning-era bihurtu dezakezu saldoa.

💡 Mutiny-rekin ez zaude nodo bakar bat erabiltzeko mugatuta. Mutiny beste nodo batera konekta dezakezu, lehenetsitako Voltage Flow 2.0 LSP-ren ordez. Aukeratutako nodoarekin konektatzeko, joan **Ezarpenak > Admin Orria** atalera. Lehenik, konektatu zure nodoa pare bezala, **Peer konektatu** atalean nodoaren helbidea `pubkey@address` formatuan itsatsiz, eta ondoren ireki kanal bat nodo horrekin **Pubkey** eta **Zenbatekoa** sartuz. Kanalak sei baieztapen jaso beharko ditu erabili aurretik.

## Babeskopia

Mutiny zorroa nabigatzailean edo aplikazioan kargatu ondoren transakzioak egiten hasi zaitezke, baina zuhurtziaz jokatzeko, gomendagarria da funtsak babestea babeskopia bat eginez.

Prozesua erraza da: klik egin **Babeskopia** atalean orri nagusian eta idatzi 12 hitzak. Nahi izanez gero, pasahitz bat gehitu dezakezu zure hazia hitzak enkriptatzeko.

Zure hazia hitzak ahaztu badituzu, oraindik ikus ditzakezu berriro **Ezarpenak > Babeskopia** atalera joanda.

## Nostr

### Zaps

Ukitu bakarreko zaps! Hori **NIP-47 Nostr Wallet Connect (NWC)** erabiliz gauzatzen da.

Wallet Connect erabiltzen hasteko:

1. Joan **Ezarpenak** atalera, eta aukeratu **Beta Ezaugarriak > Wallet Connections**.
2. Sortu konexio berria **Gehitu Konexioa** botoia sakatuz.
3. Eman izen bat konexioari, zertarako den gogorarazteko.
4. Ukitu bakarreko zap esperientzia osoa nahi baduzu, markatu **Auto Approve** laukia eta ezarri aurrekontu bat zorro-konexio honetarako. Bestela, Mutiny-ra itzuli beharko duzu transakzio zainak eskuz onartzeko.
5. Aurrekontuarekin ados zaudenean, sakatu **Sortu Konexioa** eta QR kode bat erakutsiko zaizu. Eskaneatu dezakezu beste gailu batean Nostr bezero batetik edo **Ireki Nostr Bezeroan** aukeratu gailu berean irekitzeko. Nostr bezeroak NWC onartu behar du funtziona dezan.
   - **Amethyst-en**, baliteke eremu desberdinetan itsatsi behar izatea datuak.

### Kontaktuak

Zure npub inporta dezakezu zure kontaktuek nori zap egiten dioten ikusteko. Horretarako, joan **Ezarpenak > Nostr Kontaktuen Sinkronizazioa** atalera. Sartu zure Nostr npub, eta segundo gutxiren buruan zure kontaktuen zap jarduera ikusiko duzu.

### Opariak

Mutiny-k kriptoak ez dituztenak ekosistemara sartzea inoiz baino errazagoa bihurtzen du. Norbaitek web-nabigatzailea erabiltzeko aukera badu, sats-ak oparitu ahal zaizkio, aitzakiarik gabe. Eta hobekien dena, prozesu osoa autokudeatua da!

Opari bat sortzeko, **Mutiny+ harpidetza** izan behar duzu. Hori egin ondoren (eta benetan egin beharko zenuke; oso aukera argia da), joan **Beta Ezaugarriak > Opariak** atalera. Idatzi hartzailearen izena erregistroetarako eta hautatu zenbatekoa. **Opari bat sortu** botoian klik egitean, QR kode bat eta URL bat izango dituzu.

Oparia eskuratzeko, erabiltzaile berriak QR kodea eskaneatu edo esteka nabigatzailean ireki besterik ez du egin behar. LSP-k kanal bat irekiko die oparia eskuratzean. Gogoan izan zure zorroa irekita eta linean egon behar duela hartzaileak oparia eskuratzeko.

Azpiko prozesuan, hau guztia Nostr Wallet Connect erabiliz egiten da. 🤯 QR kodeak hartzaileari faktura sortzeko beharrezko informazioa ematen dio. Bidaltzailearen zorroa entzuten ari da relay-tik datorren faktura, eta ikusten duenean ordaintzen du.

💡 Oso aurrezti-emailea bazara eta Mutiny+ ordaindu nahi ez baduzu, Mutiny autokudea dezakezu. Hala ere, Mutiny-ren garapena babestea gomendatzen dugu. Zap egin diezaiekezu hemen: nostr:npub1mutnyacc9uc4t5mmxvpprwsauj5p2qxq95v4a9j0jxl8wnkfvuyque23vg.

## Mutiny+

Mutiny-k Lightning bidezko harpidetza-fakturazioa automatikoki sortzeko sistema eraiki du... asmatu duzu, NWC erabiliz. Harpidetza NWC gertaera bat da, eta hilero fakturak sortuko ditu automatikoki. Ez al da zoragarria? Gainera, edozein unetan bertan behera utzi dezakezu, zorro-konexioa ezabatuz. Mutiny-ren harpidetza ezaugarriari buruzko xehetasun guztiak [hemen](https://mutinywallet.com) irakur ditzakezu.

## Migrazioa

Zure zorroa beste gailu batera edo nabigatzailetik aplikazio natiboetara migratzerakoan, bi aukera dituzu: egoera-fitxategia erabiliz migratu (gomendatutako metodoa) edo zure babes-hazi-esaldia erabiliz. Kontsultatu gida ofiziala urrats guztiak ikusteko.

## Ondorioa

Nostr eta Lightning elkartzen direnean, emaitza ikusgarriak lortzen dira. **Mutiny Wallet**-ek hau erakutsi du ukitu bakarreko zap-ekin, harpidetzei eta opariei esker, guztiak Nostr Wallet Connect bidez funtzionatzen dutela.

Baina hori ez da Mutiny-k eskaintzen duen guztia. Etorkizunean datozen funtzionalitate zirraragarriak ere badira, hala nola **RedShift** eta **Synthetic USD**. Eguneraketak jarraitzeko, bisitatu Mutiny Blog.

Gida hau lagungarri izan zaizu? Jo ta ke saiatu ukitu bakarreko zap bat bidaltzen zure Mutiny zorro berritik. :)
