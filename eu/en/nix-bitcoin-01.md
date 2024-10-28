## NixOS Instalatu

NixOS instalatzeko hainbat modu daude. Aukera dezakezu makina birtual bat edo dedikaturiko hardware batean instalatzea. NixOS makina birtual batean instalatzea aukera ona da proba egiteko, eta Nixen erreproduzigarritasunak esan nahi du konfigurazio bat erraz kopiatu dezakegula VMtik dedikaturiko hardware batera. VirtualBox erabiliz NixOS irudia VM batean nola instalatu azalduko dugu, baina dedikaturiko hardwarearekin jarraitzen baduzu, gainerako gida berdina izango da funtsean.

### VirtualBox

Deskargatu nahi duzun ISO fitxategia [iturritik](https://nixos.org/download). GNOME bertsio gomendatua erabiliko dugu, baina Plasma aukeratzen baduzu ere, berdin du.

NixOS VirtualBox VM batean nola instalatu jakiteko gida honetan jarraitu dezakezu: [hemen](https://itsfoss.com/install-nixos-vm/#dont-reboot-but-turn-off-the-vm). Jarraian pausoen laburpena dago:

- Ireki VirtualBox
- Egin klik `Berria` aukeran menuko barran
- Izendatu zure VM
- Aukeratu deskargatu berri duzun ISO irudia
- Aukeratu `Linux` ISO mota gisa
- Aukeratu `Beste Linux (64-bit)` bertsio gisa
- Egin klik `hurrengoa` botoian
- (Gomendatua) Aukeratu gutxienez 4GB RAM
- (Gomendatua) Aukeratu gutxienez 2-4 prozesadore nukleo
- (Gomendatua) Aukeratu gutxienez 30GB instalazio honetarako
- Dena ondo badago, egin klik `Amaitu` botoian eta VirtualBox-ek NixOS makina birtual bat sortuko dizu.

- Egin instalatzaile grafikoaren bidez nahi dituzun konfigurazioekin.
- `Instalatu` atalean, 46%-an geldirik dagoela eman dezake. Ez kezkatu, utzi instalatzaileari lanean eta itzuli geroago.

- Instalazio-prozesua amaitzean, **ez berrabiarazi** baina itzali VM. Bestela, instalatzailea berriz kargatuko da!
- VM-a itzaltzeko, hautatu `Itxi` aukera **Fitxategi menuan** eta hautatu `Makina itzali`

- Aldatu abio-ordena VirtualBox-en
  - NixOS VM-an abio-ordena aldatzeko, ireki VM horren ezarpenak
  - Ezarpenetan, hautatu `Sistema` eta hor aurkituko duzu abio-ordena
  - Hemen, hautatu `Disko Gogorra` eta erabili **gezi gora** ikonoa lehen abio aukera gisa jartzeko
  - Sakatu `Ados` aldaketak gordetzeko.
  - Bestela, kendu instalazioa hasteko gehitu dugun ISO irudia.

## NixOS-en lehen begirada

Lehenik eta behin, gure berriki instalatutako ingurunea arakatuko dugu eta harekin ohituko gara.

Kontsola ireki eta `/etc/nixos` direktorioan nabigatu, bertan dagoena ikusteko.

```bash
cd /etc/nixos
ls
```
