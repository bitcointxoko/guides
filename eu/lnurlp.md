# Zer da lightning address bat?

Lightning address bat irakurgarria den helbide elektroniko baten antza duen helbidea da, adibidez erabiltzailea@domeinua.com, baina bitcoinetan ordainketak berehala eta merke jasotzeko aukera ematen du. Ez duzu zure gailuan nodo bat linean izatea behar, eta ez duzu eskuz faktura bat sortu behar norbaitek ordainketa egin nahi dizunean.  
Oso interesgarria, ezta?

## Nola funtzionatzen du, orduan?

Lightning Address-ek LNURL pay protokoloa erabiltzen du, Lightning Network-aren gainean dagoen geruza bat da. 
![image](https://github.com/user-attachments/assets/7b27efc0-d143-4351-8504-0ca215d79e7e)

Prozesua hurrengo urratsetan laburbil daiteke:

1. Erabiltzaile batek zure Lightning Address erabiliz ordainketa egin nahi duenean, haien zorroak helbide hori LNURL payRequest batean bihurtzen du.
2. LNURL payRequest arrakastatsu baten bidez, zorroak BOLT11 faktura bat eskuratzen du, eta faktura hori ordainketa burutzeko erabiltzen da.

Hau da, prozesuaren oinarrizko pausoak hurrengoak dira:  
💡 **Lightning Address > LNURLp > BOLT11 faktura.**  
Lightning Network-ekin integratuta dagoen sistema honi esker, ordainketak erraz, azkar eta modu automatizatuan burutu daitezke.

### Oso ondo dirudi, baina zein da tranpa?

Lightning Address-en inplementazio askok kustodia dute (nahiz eta ez den beti horrela), izan ere, domeinu bat eta beti linean dagoen nodo bat behar dira Lightning Address-ak funtzionatzeko. Kustodia sistema bat denez, zure fondoak kudeatzen dituenak edozein momentutan kontrolatu edo kendu ahal dizkizu eta zure transakzioak monitorizatu ditzake.  
Domeinuaren jabearengan fidatu behar duzu, zure Lightning Address-aren erregistroa aldatu ez dezan. Eta, gainera, LNURL zerbitzaria linean ez badago, sistema ez da funtzionatzen.  
**Bitcoin Txoko**-k LNbits-en oinarritutako Lightning Address irtenbide sinplea eskaintzen du. Hau ere kustodia sistemakoa da, beraz, gomendagarria da Bitcoin Txoko zorroan kopuru txiki bat bakarrik gordetzea eta gero auto-kustodia zorro batera ateratzea, satoshi gehiago jasotzen dituzun heinean.

## Hasteko prest bazaude, hona hemen behar duzuna:

1. **Zure zorroa sortzea**  
   Lehenik eta behin, ez baduzu oraindik egin, joan [bitcointxoko.com](https://bitcointxoko.com) webgunera eta zorro bat sortu. Zorroari nahi duzun izena jar diezaiokezu.

2. **Luzapenak aktibatzea**  
   Lightning Address-ak funtzionatzeko Pay Links luzapena behar da. Horretarako:
   - Joan tresna-barrako Extensions (Luzapenak) atalera eta Pay Links luzapena aktibatu.

3. **Ordainketa esteka bat sortzea**
   - Ireki Pay Links luzapena eta egin klik New Pay Link (Ordainketa Esteka Berria) aukeran.
   - Aukeratu sortu duzun zorroa.
   - "Item Description" atalean, nahi duzun testua sar dezakezu.
   - Aukeratu zure Lightning Address-erako erabiltzaile izena. Zure Lightning Address hau bezalakoa izango da: erabiltzailea@bitcointxoko.com.
   - Fixed Amount aukera desmarkatu eta jarri gutxieneko balioa 1 eta gehienekoa 500000.
   ![image](https://github.com/user-attachments/assets/42429f3a-4141-42da-b0dd-ef0557c83b79)

     ⚠️ Gehienezko balioa handiagoa jar dezakezu, baina ordainketa handiek huts egiteko probabilitate handiagoa dute, Bitcoin Txoko Lightning nodoaren kanalaren sarrera-gaitasun mugatua dela eta. Gomendagarria da 500000 satoshitan mantentzea.
   - Orain, ireki Advanced Options (Aukera Aurreratuak) eta aldatu Comment maximum characters (Komentarioaren gehieneko karaktere kopurua) 799-ra. Ez da beharrezkoa, baina aurrerantzean funtzionalitate gehiago emango dizu.
   - Azkenik, markatu Enable nostr zaps aukera behealdean, Lightning Address bidez zaps jasotzeko aukera izateko.

   Aukera aurreratuak beste parametro batzuk konfiguratzea ahalbidetzen dute, baina nahi baduzu hutsik utz ditzakezu.  
   Azkenik, dena zuzen dagoela egiaztatu ondoren, egin klik **Create Pay Link** (Sortu Ordainketa Esteka) botoian.

Horrela, zure Lightning Address sortuta izango duzu eta ordainketak jaso ahal izango dituzu!

## Proba egitea

Zure Lightning Address ondo funtzionatzen duen probatu nahi baduzu, beste zorro batera joan, **Bidali (Send)** aukera hautatu eta helmuga gisa zure Lightning Address idatzi. Ondoren, bidali zeure buruari satoshi batzuk.  
Ondoren, itzuli Bitcoin Txoko zorrora eta egiaztatu ordainketa jaso duzun. Litekeena da orria freskatu behar izatea ordainketa agertzeko.  
Dena ondo atera bada, zorionak! 🥳  
Bestela, jakinarazi iezaguzu. Beti prest gaude laguntzeko.

## Hurrengo urratsak

### Nostr zaps
Zure Bitcoin Txoko Lightning Address nostr profilean gehitu dezakezu eta horrela zaps jasotzeko erabil dezakezu. Normalean, hau hurrengo pausuekin egiten da:
- Joan **Profile** (Profila) atalera.
- Hautatu **Edit** (Editatu) eta Lightning Address aldatu.

### LNDhub
Zure LNbits zorroa telefonoan inporta dezakezu LNDhub bezala, Zeus edo BlueWallet bezalako aplikazioak erabiliz. Horrela, ez duzu nabigatzailean zorroa ireki beharko aldian-aldian saldoa egiaztatu edo ordainketak egiteko.  
Nola egin jakiteko, ikus ezazu nostr helbidea: `naddr1qvzqqqr4gupzqkvlvlma7a55ccp6d5rrdc27h3ssmdmael286mjaq5uxmqslk04fqqxnzd3exuerqdfkxccnyv3cs0uvul`.

### QR kodea
Zure LNURLp QR kodea parteka edo inprima dezakezu, jendeak mugikorrarekin eskaneatu dezan. Oso erabilgarria da zure denda lokaleko jabeak Lightning ordainketak jasotzeko sistema ezartzea nahi baduzu!
- Parteka ezazu **Sharable Page** (Parteka daitekeen Orrialdea) esteka.
- Edo, QR kodea PDF formatuan inprima dezakezu: joan **View Link** (Esteka Ikusi) atalera eta hautatu **Print** (Inprimatu).

Horrela, zure Lightning Address erabilera praktikoa handitu eta errazago kudeatu dezakezu! Hasi zaitez !
