Inoiz pentsatu al duzu norbaiti satoshiak modu originalean oparitzea, Bitcoin mundura hurbiltzeko? LNbits zorro batekin NFC opari txartel bat erraz sor dezakezu. Honek LNURLw esteka bat NFC txartelean idatziz funtzionatzen du, eta jasotzaileak bere satoshiak erabili ditzake LNURL gaitutako zorro batekin.

### Zer behar dut?
- LNbits zorroa
- Android telefono bat
- NTAG2* gaitasunak dituen NFC txartela, adibidez NTAG216.

💡 NTAG2* txartelek esteka **bat** idazteko aukera ematen dute. Adibidez, enpresaren webgunerako URLa duen bisita-txartel gisa joka dezakete. NTAG424 txartelek ez dute memoria handiagoa bakarrik, baizik eta SUN parametro deitzen den zerbait ere badute, zerbitzariaren autentifikazioa ahalbidetzen duena, eta horrek segurtasun gehiago ematen die zure ordainketei. Azkenean txartel mota hau [BoltCard](https://boltcard.org/) bat bihur daiteke.

### 1. Errepozitorioa Aktibatu
Ireki zure LNbits zorroa. Tresna-barran, aktibatu `Withdraw Links` luzapena eta ondoren joan luzapenera.

### 2. Erretiratzeko esteka sortu
`Withdraw Links` luzapen orrian, aukeratu `Advanced Withdraw Link(s)` aukera. 

Ondoren, aukeratu satoshiak ateratzeko erabiliko duzun zorroa. Ziurrenik, hori zure LNbits zorro nagusitik bereizi nahi izango duzu. Horretarako, LNbits zorro berri bat sor dezakezu tresna-barratik, `+ Add a new wallet` aukera hautatuz. Behin zorro berria sortuta, sartu satoshi batzuk bertan.

![configure](https://cdn.satellite.earth/9eefb0bcc03e218aac55a5c3bfa06f0cdd59d3b36959c58e3f2f88941cca0d01.webp)

Eman izenburu bat erretiratzeko estekari. 

Ezarri erreskatatu daitezkeen gutxieneko eta gehienezko zenbatekoak.

Ezarri esteka zenbat aldiz erabil daitekeen eta erretiratze saiakeren arteko denbora.

Aukeran, argazki pertsonalizatu bat gehi dezakezu `Use a custom voucher design` laukitxoa markatuz, eta .png irudi baten URL-a sartuz.

Gogoan izan “assmilking” laukitxoa ez markatzea.

Konfigurazioa amaitu ondoren, jarraitu erretiratzeko esteka sortzera.

### 3. Idatzi esteka NFC txartelean
Zure erretiratzeko esteka berrian, klikatu `View LNURL` estekan. Ondoren, sakatu `Write to NFC` botoia eta eutsi NFC txartela telefonoaren aurrean idazketa-prozesua burutzeko.

![write](https://cdn.satellite.earth/7d290d0c076c724af88089f3ad2bdc7c22cac5bc7bb521e5f28c5646a4fe350d.webp)

✔️ **EGINDA**

💡 Esan txartelaren jasotzaileari satoshi saldoari buruz, denbora ez dezan galdu azkeneko satoshia lortzen saiatzeko.

💡 Jasotzaileak txartelaren satoshiak atera ondoren, bere zorroan berridatzi dezake eta berrerabili. Gainera, eman diozun txartela NTAG424 bada, aurreko gidako (nostr:naddr1qqxnzd3e8qcr2wfn8qcrgwf4qyg8wumn8ghj7mn0wd68ytnhd9hx2q3qtx0k0a7lw62vvqax6p3ku90tccgdka7ul4radews2wrdsg0m865sxpqqqp65whwqrr5) bezala Lightning "zor txartela" bihur dezake. Baina txartela NTAG2* bakarrik bada, beste opari txartel bat bihur dezake soilik.
