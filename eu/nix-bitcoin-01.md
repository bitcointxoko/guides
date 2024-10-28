# NixOS instalatu

NixOS instalatzeko hainbat modu daude. Birtualizazio makina baten bidez edo hardware espezifiko batean instalatzea aukeratu dezakezu. NixOS birtualizazio makina batean instalatzea aukera ona da sistema probatzeko, eta Nix-en erreproduzigarritasunari esker, birtualizazio makinan egindako konfigurazio funtzional bat hardware espezifikora erraz kopiatu dezakegu ondoren. Gida honetan, VirtualBox erabiliz NixOS irudia birtualizazio makina batean nola instalatu azalduko dugu; hala ere, hardware espezifikoan ari bazara, gainerako urratsak funtsean berdinak dira.
## VirtualBox-en NixOS instalatzeko jarraibideak

1. Hautatu nahi duzun ISO fitxategia iturri ofizialetik deskargatzeko. Gida honetan gomendatutako GNOME bertsioa erabiliko dugu, nahiz eta Plasma aukeratzeak ez duen berez alderik eragingo.
2. VirtualBox ireki eta menu barran Berria botoian klik egin.
3. Birtualizazio makina izendatu (VM).
4. Deskargatutako ISO irudia hautatu.
5. ISOren motan Linux hautatu.
6. Bertsiorako Beste Linux (64-bit) aukeratu.
7. Hurrengoa botoian klik egin.
8. (Gomendatua) Gutxienez 4 GB RAM esleitu.
9. (Gomendatua) Gutxienez 2-4 prozesadore nukleo esleitu.
10. (Gomendatua) Instalaziorako gutxienez 30 GB disko espazio aukeratu.
11. Dena ondo badago, Amaitu sakatu, eta VirtualBox-ek NixOS birtualizazio makina sortuko du.
12. Instalatzaile grafikoaren bidez aurrera egin, zure nahiak kontuan hartuta.
13. Instalazio fasean, baliteke instalazioa 46%-an blokeatuta dagoela ematea. Ez kezkatu; utzi instalatzaileari bere lana egiten eta itzuli geroago.
14. Instalazioa amaitu ondoren, ez berrabiarazi berehala, baizik eta birtualizazio makina itzali, berriz instalatzailea kargatuko ez dadin.
   - Makina itzaltzeko, aukeratu Itxi aukera Fitxategia menutik eta aukeratu Makina itzali.
15. Boot (abioko) ordena aldatu VirtualBox-en:
   - NixOS birtualizazio makina horretarako ezarpenetan sartu eta Sistema hautatu.
   - Han, abioko ordena aurkituko duzu.
   - Disko gogorra lehen abio aukera izan dadin, gora gezia erabili.
   - Ezarpenak gordetzeko, Ados sakatu.
   - Bestela, hasierako ISO irudia kendu dezakezu, instalazioa hasteko gehitu genuen bezala.

Horrela, NixOS instalazioa VirtualBox birtualizazio makinan amaituta izango duzu eta lehen aldiz abiarazteko prest egongo da.

## NixOS lehen begirada

Lehenik eta behin, NixOS ingurune berrian pixka bat esploratuko dugu, funtzionamenduari eta oinarrizko konfigurazioari buruz gehiago ikasteko.

