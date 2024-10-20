# Zer da Cashu?

Cashu Bitcoinentzako Ecash protokolo irekia da, transakzio azkarrak eta doakoak eskaintzen dituena. Protokolo honen ezaugarri nabarmenetako bat pribatutasun ia perfektua eskaintzea da. Nostr [nostr:npub12rv5lskctqxxs2c8rf2zlzc7xx3qpvzs3w4etgemauy9thegr43sf485vg](nostr:npub12rv5lskctqxxs2c8rf2zlzc7xx3qpvzs3w4etgemauy9thegr43sf485vg) erabiltzaileak sortu zuen.

Hona hemen Cashu eta on-chain Bitcoin alderatzen dituen taula, Bangkok 2023ko Bitcoin Konferentzian nostr [nostr:npub1cj6ndx5akfazux7f0vjl4fyx9k0ulf682p437fe03a9ndwqjm0tqj886t6](nostr:npub1cj6ndx5akfazux7f0vjl4fyx9k0ulf682p437fe03a9ndwqjm0tqj886t6)-k aurkeztutako Nuts and Bolts hitzaldian oinarrituta:

| **Cashu**             | **Bitcoin (on-chain)**     |
|-----------------------|----------------------------|
| Libururik gabe         | Liburu banatua              |
| Titulartasun tokena    | UTXO (Ustiaketa Ezberdinen Irteera) |
| Transakzio itsutuak    | Transakzio publikoak        |
| Zentralizatua          | Deszentralizatua            |
| Konfiantzazkoa         | Konfiantzarik gabe          |
| Aldi baterako transakzioak | Betiko transakzioak     |

Ikusten dugunez, Cashuk pribatutasuna hobetzeko konfiantza gabeko izaera eta deszentralizazioa sakrifikatzen ditu. Konpentsazio hauek zentzuzkoak dira zaintza-zerbitzuetan, erabiltzailea dagoeneko zerbitzu zentralizatu eta fidagarri bat erabiltzen ari baita. Zaintza tradizionaleko irtenbideek pribatutasun eskasa dute, zaintzaileak erabiltzailearen funtsak zenbat diren eta norekin ari den transakzioak egiten jakin dezakeelako. Horrek esan nahi du norbanakoak erraz helburu eta zentsura daitezkeela. Gainera, datu-erregistroek "honeypot" bihurtzeko arriskua dute, hau da, erasotzaileentzat erakargarri.

Alderantziz, Cashu-ren mint-ek zaintzaile gisa jardun dezakete, baina erabiltzaileen nortasuna, duten funtsen kopurua edo norekin ari diren transakzioak egiten ezagutzeko aukerarik gabe. Mint-ek duten datu-erregistro bakarra gastatutako sekretuen zerrenda da, berriro erabili ezin direnak, baina erabiltzaileekin lotzeko modurik gabe. Horrela, Cashu-k pribatutasuna bermatzen du, zaintzaileak ez duelako inolako informaziorik erabiltzaileen jarduerei buruz, ohiko zaintza-soluzioekin gertatzen denaren kontrara.
![image](https://github.com/user-attachments/assets/4af672e7-4e60-4096-bb86-f6f801601ab8)

## Cashu-ren erabilera kasu batzuk

Cashu-ren erabilera kasu batzuk honako hauek dira: bonuak, dagoeneko zentralizatuak eta zaintza-zerbitzuak dituztenak; baliabide bakoitzeko ordainketa (pay-per-resource) APIak, nostr bideratzaileak eta mixnet-ak bezalako zerbitzuetarako; sistema integratuak, kontu eta saldo eredu tradizionala ordezkatzen dutenak; eta truke/mixinge zerbitzuak, gordailuak eta ateratzeak deslotzeko, pribatutasuna hobetzeko.

## Historia

Ecash David Chaum-ek 1982an asmatu zuen, sinadura itsuak erabiliz balio elektronikoaren transmisiorako protokolo gisa. Cashu Ecash-en inplementazio bat da, David Wagner-en 1996ko Chaum-en itsutze-aldaketan oinarrituta dagoena, eta nostr sortu zuen.

## Terminologia

Cashu nola funtzionatzen duen ulertzen laguntzeko, lehenik eta behin funtsezko terminologia batzuk azalduko ditugu.

### Mint

Cashu-ren mint-a erabiltzaileen funtsen zaintzailea da. Bere zeregina tokenak jaulkitzea eta erretzea da, baita bikoiztutako gastuak saihestea ere. Cashu-ren mint-a Lightning nodo baten gainean dago, beraz, Lightning ordainketak bidali eta jaso ditzake, beste mint batzuekin trukeak barne. Hala ere, Lightning nodoa lineaz kanpo badago ere, ecash tokenekin transakzioak egin daitezke. Lightning-ekin ez bezala, jasotzailea linean egon beharrik ez du tokenak jasotzeko.

Mint-ak ez daki nor den erabiltzailea, zenbat funts dituzten edo norekin ari diren transakzioak egiten. Hala ere, mint-a erabiltzaileen funtsen zaintzailea denez, fidagarria den mint bat aukeratu behar duzu, eta eragilea nor den jakin. Erabil ezazu funts txikiekin edo tokenak berehala trukatu.

### Token

Cashu token-a mint-ak sinatutako datu-puska bat da, eta erabiltzaileak token horiek bere zorroan gordetzen ditu. Ecash tokenak testu-kate hutsak direnez, edozein testu bidezko protokoloaren bidez bidal daitezke, adibidez, nostr, posta elektronikoa, SMS, etab. Cashu-k txanpon-sistema bat erabiltzen du, zenbateko finkatuak dituena. Analogia bat eginez, hau moneta fiduziarioen billeteen zenbatekoei dagokie. Adibidez, eurotan 5, 10, 20, 50, 100 euroko billeteak daude. Cashu-n, tokenak 2ren indarren arabera sailkatzen dira. Adibidez, 1, 2, 4, 8, 16, 32, 64, 128 satoshi, eta horrela aurrera.

Zenbatekoak erabiltzea erabiltzaileen artean anonimotasuna areagotzeko egiten da, eta mint-ek transakzioak erabiltzaileen nortasunekin lotzea zailagoa bihurtzeko.

## Nola funtzionatzen duen, 5 urteko bati bezala azaldua
![image](https://github.com/user-attachments/assets/336599a1-eedc-4d0e-9a24-a29b97530068)


Erabiltzaile Alice-k Cashu token berriak sortu nahi ditu. Horregatik, Bob mint-aren arduradunarengana joaten da eta esaten dio: "Kaixo! Cashu token berriak sortu nahi ditut."
![image](https://github.com/user-attachments/assets/c5615f7c-44de-4340-83ff-037d13234a6f)

Bob-ek erantzuten dio: "Ados, ordaindu iezadazu eta bidali iezadazu sekretu itsu bat." Sekretu itsua esan nahi du Alice-k sekretua ezagutzen duela, baina Bob-ek ezin duela sekretu hori ikusi. 
![image](https://github.com/user-attachments/assets/e86be1bb-f6f2-4652-b088-a2525eb671da)

Alice-k sekretu bat sortzen du, eta ondoren itsutzen du, horrela Bob-ek ez dezan jakin zein den sekretu hori.
![image](https://github.com/user-attachments/assets/89f5159e-130f-4e4c-95c4-07a808a82fc9)

Alice-k Bob-i ordainketa egiten dio eta ordainketaren egiaztagiria eta sekretu itsua bidaltzen dizkio. Bob ordainketa jaso duela ziur dagoenean, Alice-ren sekretu itsua sinatzen du eta sinatutako sekretu itsua itzultzen dio. Bob-ek sinatu duelako, etorkizunean ziur egon daiteke tokena baliozkoa dela.
![image](https://github.com/user-attachments/assets/2de8a08f-a1c7-426b-af92-fb4f850af217)
![image](https://github.com/user-attachments/assets/24233981-24d2-4aad-b8d6-7c7716d852b4)


Alice-k Carol-i ordaindu nahi dio. Horretarako, sekretua eta sinatutako sekretu itsua desitsutzeko gakoa bidaltzen dizkio Carol-i. 
![image](https://github.com/user-attachments/assets/4f2adc49-11bb-4d7d-9983-28e4c2723bfd)
![image](https://github.com/user-attachments/assets/3ecf7e53-3b66-4655-8bbe-121823b1499e)

Carol-ek bere tokena trukatu nahi du. Beraz, Bob-engana (mint-aren arduradunera) joaten da eta Alice-k eman dion sekretua eta desitsututako gakoa erakusten dizkio.


### Nola jakiten du mint-ak Carol-i zenbat satoshi eman behar dizkion?

Lehenago aipatu genuen bezala, Cashu tokenak 2ren indarren araberako zenbatekoetan banatuta daude (1, 2, 4, 8, 16, 32...), paperezko diru billeteen antzera. Bob mint-ak zenbateko bakoitza sinatzeko gako pribatu berezi bat du. Adibidez, 1 satoshi zenbatekoaren tokenak sinatzeko gako pribatu bat du, 2 satoshi zenbatekoaren beste bat, 8 satoshi zenbatekoaren beste bat, eta abar. Horrela, Carol tokenak trukatzera datorrenean, Bob-ek badaki zein gako pribaturekin sinatu zuen token hori, eta horren arabera, tokenak zein zenbatekotakoak diren ezagutzen du. Horrela, Bob-ek Carol-i dagokion satoshi kopurua itzuli diezaioke, sinatutako tokenaren zenbatekoa kontuan hartuta.

### Zer gertatzen da itzulkinekin?

Cashu-n ez dago itzulkinik diru fisikoan bezala. Horren ordez, mint-ari (Bob-i) eskatu behar diozu token zaharrak suntsitzeko eta berriak sortzeko, zenbateko berarekin. Adibide batekin azalduz: Demagun Alice-k bi token dituela, guztira 10 satoshi balio dutenak. Bata 8 satoshi da eta bestea 2 satoshi. Alice-k 9 satoshi bidali nahi dizkio Carol-i. Horretarako, mint-ari (Bob-i) eskatzen dio bere 2 satoshi tokena bi 1 satoshi token bihurtzeko. Horrela, Alice-k 9 satoshi bidal diezazkioke Carol-i: 8 satoshi token bat eta 1 satoshi token bat erabiliz. Gainera, beste 1 satoshi tokena berarentzat gordetzen du.

### Lightning sarearen papera konektatzeko elementu gisa

Zer gertatzen da Alice-k David-i ordaindu nahi dionean, baina David-ek Bob-en mint-a ez du fidatzen, eta, aldiz, Erin ezagutzen du eta bere mint-a erabiltzen du? Alice-k bere tokenak Bob-en mint-ean trukatzen ditu, eta Bob-i eskatzen dio token horiek "urtzeko" edo Lightning satoshietara bihurtzeko. Ondoren, Bob-en mint-ak Lightning transakzio bat bidaltzen dio Erin-en mint-ari. Erin-en mint-ak transakzio hori jasotzen du, eta David-entzat token berriak sortzen ditu Lightning sarearen bidez Bob-en mint-etik jasotako satoshiekin. Horrela, Lightning sareak mint ezberdinak konektatzen ditu, erabiltzaileak (Alice eta David) mint ezberdinak fidatu arren, transakzioak segurtasunez egiteko.

## Zer dator hurrengoa Cashu-rentzat?

### Programagarri den ecash

Cashu-ri gastatzeko baldintzak gehitu ahal izango zaizkio, mint-ak baldintza horiek betearaziko dituelarik. Horrek ahalbidetu dezake kontratu adimendun sendoak sortzea, oinarrizko katean (Bitcoin blockchain) edo Lightning sarean sartu gabe. Horrela, ordainketa publikoak, lineaz kanpokoak eta maiztasun handikoak posible izango dira.

### Zorren froga eskema (Proof of Liabilities Scheme)

Zorren Froga (PoL) Eskema Cashu-rentzat zaintzailea den mint-ak erabiltzaileak iruzurrez erabiltzea zailtzen du, epoka kontzeptua aurkeztuz. Eskema honetan, zaintzaile den mint-ak epoka bakoitzean gako pribatuak aldian-aldian biratzen ditu, eta azken epokan jaulkitako eta erretako tokenen zerrenda publikoak argitaratzen ditu. Hau Erreserben Froga (Proof of Reserves) eskemarekin uztartzen da, non erreserbak katean bertan multisig batean gordetzen diren. Horrela, mint-ak ezingo du bere erantzukizunak murriztu, erabiltzaileek iruzurra detektatzeko arriskua handitu gabe. Xehetasun gehiagorako, eskema honen azalpen osoa kontsultatu dezakezu.

## Saiatu Cashu

Cashu probatzeko, [Nutstash] eta [eNuts] gidak erabil ditzakezu. Horretarako Lightning zorro bat eta telefono edo ordenagailu bat besterik ez duzu behar.
