# Zer da Cashu?
Cashu Bitcoin-erako ecash protokolo ireki bat da, transakzio azkarrak eta komisio gabekoak eskaintzen dituena, pribatutasun ia perfektuarekin. Xehetasun gehiago nahi izanez gero, gure azalpena ikus dezakezu.

## eNuts
eNuts Cashu-rako mugikorretarako zorro bikaina da, Android eta iOS (TestFlight) plataformetan eskuragarri dagoena. Mint anitzekin lan egitea ahalbidetzen du eta nostr bidez bidalketak egiteko aukera ere eskaintzen du.

⚠️ **eNuts eta Cashu oraindik beta fasean daude**. Funtsak galtzeko arriskua dago. Aplikazioa instalatzerakoan arriskuen inguruan irakurri. Galera ekonomikoei aurre egiteko gai zaren zenbateko txikiekin saiatu.

## Probatu
Prozesu honetan zehar mint-ekin elkarreragin, ecash-a jaso eta bidali, segurtasun-kopiak egin, Lightning-era ateratzeak eta mint-en artean trukaketak egingo ditugu. Azkenik, nostr kontaktu funtzionalitatea probatuko dugu.

### Instalatu
Sartu eNuts webgunera eta instalatu aplikazioa zure sistema eragilerako.

### Mint bat gehitzea
Ecash-arekin elkarreragiteko, lehenik mint bat behar duzu. Mint honetan zure ecash token-ak sortzen eta itzultzen dira. Mint-a da zure Bitcoin-en zaindaria, baina ez daki nor zaren, norekin egiten duzun transakzioa, ezta zenbat diru duzun ere. Probetarako Txoko mint erabili dezakezu.

1. Joan Txoko Mint-era. Kopiatu mint URL-a.
2. eNuts-en, joan Aukerak > Mint kudeaketa eta sakatu + botoia. Itsatsi lehen urratsean kopiatu duzun mint URL-a.  
💡 Mint gehigarriak ere gehitu ditzakezu. Mint publiko batzuk MintIndex-en aurki daitezke. Kontuan izan mint batzuek zenbateko jakin bat gordetzen dutela bideratze-gastuak ordaintzeko, eta, beraz, ezin dituzula zure sats guztiak atera.

### Tokenak sortzea
Mint bat gehitu duzunean, eNuts-ek automatikoki galdetuko dizu mint horretatik Cashu token berriak sortu nahi dituzun.

1. Erantzun **Bai**.
2. Sortu faktura bat mintu nahi duzun zenbatekoarentzat. Zenbateko txiki batekin saiatu, adibidez, 100 sats.
3. Ordaindu faktura Lightning zorro batetik. Faktura ordaindutakoan, ecash token-ak izango dituzu.

Prozesu honek aukera ematen dizu ecash token-ak sortzeko, eta horiek zure transakzioetarako erabiltzeko prest izango dituzu.

### Ecash-ekin transakzioak egitea
Ecash-ekin transakzioak egitea, funtsean, datu multzoak bidaltzea eta jasotzea da. Funtzionalitate hauek zuk zeuk probatzeko, bidali eta jaso dezakezu zure buruari.

1. Ecash bidaltzeko, sakatu **Bidali > Ecash bidali**.
2. Mint bat baino gehiago erabiltzen baduzu, aukeratu bidali nahi duzun mint-a. Ondoren, aukeratu **Kopiatu eta partekatu**.
3. Aukeratu zenbatekoa.
4. Nahi izanez gero, gehitu ohar bat, eta sakatu **Jarraitu**.
5. Berretsi ordainketa xehetasunak eta sortu token-a. Une honetan, **coin selection** funtzioa erabil dezakezu zein token erabili nahi dituzun hautatzeko.  
Ohartu token-ak 1 sat, 2 sats, 4 sats, 8 sats, 16 sats eta antzeko zenbatekotan sailkatuta daudela. Horiek 10 euroko, 20 euroko edo 50 euroko billeteak bezala irudika ditzakezu.
6. Kopiatu token-a.

Une honetan, token-a beste norbaiti bidal diezaiokezu edo zure zorroan berreskuratu. Saiakera moduan, bigarren aukera hau egingo dugu.

1. Ecash jasotzeko, sakatu **Jaso > Itsatsi eta berreskuratu Ecash**. eNuts-ek automatikoki irakurriko du zure arbeletik eta token-a berreskuratuko du.  
💡 Zure transakzioen historian ecash token-a zain dagoen egiaztatu dezakezu, eta hartzaileak ez badu berreskuratu, itzuli dezakezu. Horretarako, sakatu zure historiako irteerako transakzioan eta aukeratu **Egiaztatu token-a gastatu den**. Token-a zain badago, **Itzuli token-a** sakatu dezakezu eta berriro zure zorroan izango duzu.

### Multimint trukeak
Mint desberdinen artean bidalketak eta jasotzeak posibleak diren galdetu baduzu, erantzuna bai da, neurri batean. Hala ere, Cashu token-ak zuzenean mint batetik bestera bidaltzea ez da zuzenean egiten; horren ordez, transakzioak Lightning-era bideratzen dira, mint bat Lightning nodo bat ere badelako. Cashu token-ak ez dira bateragarriak nodo desberdinen artean. 

Hau probatzeko, beste mint bat gehitu dezakezu oraindik egin ez baduzu, adibidez, cashme LNbits mint edo eNuts mint lehenetsia.  
💡 Kontuan izan mint batzuek sats kopuru bat gordetzen dutela bideratze-gastuak ordaintzeko. Arazo hau konpontzeko, zure mint propioa sor dezakezu Bitcoin Txoko LNbits zorroarekin, Cashu luzapena aktibatuz.

1. Joan **Aukerak > Mint kudeaketa** atalera, eta aukeratu trukatu nahi duzun mint-a. Ondoren, joan **Multimint trukeak** atalean.
2. Aukeratu trukatu nahi duzun mint-a.
3. Aukeratu zenbatekoa eta sakatu **Kuotak aurreikusi** Lightning gastuen kalkulua egiteko.
4. Sakatu **Jarraitu**.
5. Egiaztatu xehetasunak, eta nahi izanez gero, **coin selection** funtzioa erabili. Ondoren, sakatu **Orain trukatu**.

Prozesu honetan, bidaltzen ari den mint-ak Lightning faktura bat ordaintzen du jasotzen ari den mint-aren bidez. Faktura osatu bezain laster, trukatuta dagoen token-a zure zorroaren saldoan agertu beharko litzateke jasotzen ari den mint-ean.

### Ateratzea 
Zure Cashu sats-ak berriro Lightning sats bihurtu nahi dituzunean, ateratzeko aukera duzu. Prozesua hauxe da:

1. Sakatu **Bidali > Lightning faktura ordaindu**.
2. Mint bat baino gehiago erabiltzen baduzu, aukeratu bidaliko duzun mint-a.
3. LN faktura edo LNURL atalean, sartu faktura bat, LNURL edo Lightning helbide bat; edo, besterik gabe, QR kode bat eskaneatu.
4. Aukeratu zenbatekoa eta sakatu **Kuotak aurreikusi**.
5. Egiaztatu xehetasunak, eta dena zuzen dagoela ikusi ondoren, sakatu **Ateratzea**.

Prozesu hau amaitutakoan, mint-ak Cashu token-ak trukatzen ditu eta Lightning faktura ordaintzen du.

### Segurtasun kopiak 
Cashu token-ak babesteko prozesua, agian, ezberdina izango da Bitcoin eta Lightning zorroak babesteko ohiko prozesuekin alderatuta. Diru-funtsak datu blokeekin irudikatzen direnez, Cashu token-ak babesten dituzunean datu bloke horiek bakarrik babesten ari zara. Honek esan nahi du segurtasun-kopiak baliogabetzen direla transakzio berri bat egiten duzun bakoitzean. 

eNuts aplikazioak Cashu token bat sortzen du zure funts guztiekin, eta token horiek zein mint-ekoak diren jasotzen du.

- **Segurtasun-kopia bat sortzeko**, joan Aukerak > **Segurtasuna > Sortu babeskopia token**. Kopiatu token-a eta gorde toki seguru batean.

Bestela, mint bakoitza banaka babestu dezakezu:
- Horretarako, joan Aukerak > **Mint kudeaketa** atalera eta aukeratu babestu nahi duzun mint-a. Ondoren, sakatu **Funtseak babestu**, kopiatu token-a eta gorde toki seguru batean.

### Berreskuratzea
Berreskuratzeko, kopiatu babeskopia token-a eta ireki eNuts aplikazioa. Aplikazioak automatikoki irakurriko du zure arbelean dagoena eta galdetuko dizu token-a berreskuratu nahi duzun.

### Nostr
eNuts aplikazioak Nostr integrazioa eskaintzen du, horrela zure kontaktu zerrendara ecash bidali ahal izateko. Funtzio hau erabiltzeko, honako pauso hauek jarraitu behar dituzu:

1. Joan **Kontaktuak** atalera eta itsatsi zure Nostr gako publikoa.
2. eNuts-ek zure kontaktu zerrenda eskuratuko du relays-etatik. Tamalez, bilaketa funtzioa oraindik ez dago eskuragarri, eta horrek kontaktu zuzena aurkitzea zaildu dezake, kontaktu asko izanez gero.

Hartzaileak Nostr motako 4 mezu zuzena jasoko du, Cashu token-arekin. Hartzaileak mezu hau bere zorroan berreskuratu eta token-a erabili ahal izango du.

## Ondorioa
Gida hau lagungarria iruditu zaizu? Saiatu Cashu token batzuk bidaltzen Nostr bidez!
