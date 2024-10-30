## NixOS Instalatu

NixOS instalatzeko hainbat modu daude. Birtualizazio makina baten bidez edo hardware espezifiko batean instalatzea aukeratu dezakezu. NixOS birtualizazio makina batean instalatzea aukera ona da sistema probatzeko, eta Nix-en erreproduzigarritasunari esker, birtualizazio makinan egindako konfigurazio funtzional bat hardware espezifikora erraz kopiatu dezakegu ondoren. 
Gida honetan, VirtualBox erabiliz NixOS irudia birtualizazio makina batean nola instalatu azalduko dugu; hala ere, hardware espezifikoan ari bazara, gainerako urratsak funtsean berdinak dira.
### VirtualBox
VirtualBox-en NixOS instalatzeko Jarraibideak

1. ISO fitxategia deskargatu:[official source](https://nixos.org/download) Hautatu nahi duzun ISO fitxategia iturri ofizialetik deskargatzeko.
2. Gida honetan [guide](https://itsfoss.com/install-nixos-vm/#dont-reboot-but-turn-off-the-vm) gomendatutako GNOME bertsioa erabiliko dugu, nahiz eta Plasma aukeratzeak ez duen berez alderik eragingo.
3. VirtualBox ireki: Menu barran Berria botoian klik egin.
4. VM izendatu: Birtualizazio makina izendatu (VM).
5. ISO irudia hautatu: Deskargatutako ISO irudia hautatu.
6. ISOren mota definitu: Linux hautatu.
7. Bertsioa aukeratu: "Beste Linux (64-bit)" aukeratu.
8. Aurrera egin: Hurrengoa botoian klik egin.
9. RAM esleitu: (Gomendatua) Gutxienez 4 GB RAM esleitu.
10. Prozesadoreak esleitu: (Gomendatua) Gutxienez 2-4 prozesadore nukleo esleitu.
11. Disko espazioa esleitu: (Gomendatua) Instalaziorako gutxienez 30 GB disko espazio aukeratu.
12. Amaitu: Dena ondo badago, Amaitu sakatu, eta VirtualBox-ek NixOS birtualizazio makina sortuko du.
13. Instalatzaile grafikoarekin aurrera egin: Zure nahiak kontuan hartuta, instalatzaile grafikoaren bidez aurrera egin.
14. Instalazioan itxaron: Instalazio fasean, baliteke instalazioa 46%-an blokeatuta dagoela ematea. Ez kezkatu; utzi instalatzaileari bere lana egiten eta itzuli geroago.
15. Instalazioa amaitu ondoren: Ez berrabiarazi berehala. Birtualizazio makina itzali, berriz instalatzailea kargatuko ez dadin.
    - Makina itzaltzeko, aukeratu Itxi aukera Fitxategia menutik eta aukeratu Makina itzali.
16. Boot (abioko) ordena aldatu:
    - NixOS birtualizazio makina horretarako ezarpenetan sartu eta Sistema hautatu.
    - Han, abioko ordena aurkituko duzu.
    - Disko gogorra lehen abio aukera izan dadin, gora gezia erabili.
    - Ezarpenak gordetzeko, Ados sakatu.
    - Bestela, hasierako ISO irudia kendu dezakezu, instalazioa hasteko gehitu genuen bezala.

Horrela, NixOS instalazioa VirtualBox birtualizazio makinan amaituta izango duzu eta lehen aldiz abiarazteko prest egongo da.
## NixOS lehen begirada

Lehenik eta behin, NixOS ingurune berrian pixka bat esploratuko dugu, funtzionamenduari eta oinarrizko konfigurazioari buruz gehiago ikasteko.
Kontsola ireki: Instalazioa amaitu ondoren, kontsola ireki behar dugu.
/etc/nixos direktorioan nabigatu: Komando bidez zuzenean joan gaitezke direktorio honetara, eta bertan, sistema konfiguratzeko fitxategi nagusiak aurkituko ditugu.

```bash
cd /etc/nixos
ls
```
NixOS konfiguratzeko fitxategi nagusia configuration.nix da, eta bertan sistema osoaren ezarpenak definitzen dira. Beste fitxategi bat ere aurkituko dugu, hardware-configuration.nix, hardwarearen konfigurazioa automatikoki ezartzen duena. Fitxategi hau sistema bakoitzera moldatuta dagoenez, normalean ez dugu aldatu beharrik izango.
NixOS-en konfigurazio-fitxategia editatzeko:

```bash
sudo nano configuration.nix
```
Hemen, adibidez, host-izena edo sistema-mailako paketeak gehitu edo aldatu ditzakezu. Erabiltzailearen eta sistema-mailako paketeak honela definitzen dira:
```nix
# configuration.nix

# user packages
users.users.username = {
    isNormalUser = true;
    description = "main user";
    extraGroups = [ "networkmanager" "wheel" ];
    packages = with pkgs; [
        # thunderbird
    ];
};

# system-wide packages
environment.systemPackages = with pkgs; [
    vim
    wget
    git
];
```
Oharra: Aldatu erabiltzaile_izena zure erabiltzaile izenarekin.
Paketeak instalatzeko baliabide on bat [mynixos.com](https://mynixos.com) da.
Adibidea: Gehitu vim, wget, eta git sistema-mailako paketeetan.
```nix
# configuration.nix

environment.systemPackages = with pkgs; [
    vim
    wget
    git
];
```
Paketeak gehitu ondoren, konfigurazio fitxategian gordetako aldaketak sisteman sinkronizatzeko:
1.	Fitxategia gorde.
2.	Ondorengo komandoa exekutatu:
```bash
sudo nixos-rebuild switch
```
nixos-rebuild komandoak konfigurazio berriak aplikatuko ditu. switch atalak sistema berreraiki eta aldaketetara "aldatzeko" agindua ematen dio NixOS-i.
Paketeak instalatu ondoren, probatu vim abiarazten, behar bezala instalatuta dagoen egiaztatzeko.

## Flakes eta Kanalak
Orain arte, kanalak erabiltzen aritu gara paketeak instalatzeko. Baina Nix komunitatean, gehienek flakes izeneko metodo bat erabiltzen dute. Flakes-ek hainbat abantaila dituzte, sistemaren konfigurazioa erreproduzigarria izateari dagokionez.
Flake bat erabiltzen hasteko lehenengo urratsa, flakes funtzioa configuration.nix fitxategian gaitzea da.
```bash
sudo nano configuration.nix
```

```nix
# configuration.nix

nix.settings.experimental-features = [ "nix-command" "flakes" ];
```
Gorde aldaketak eta berreraiki sistema komando honekin: sudo nixos-rebuild switch.

## Flakes erabiltzen
Flake fitxategia sortzeko direktorio berri bat sortzea gomendatzen da erabiltzailearen direktorioan, .dotfiles izenekoa:

```bash
mkdir ~/.dotfiles
cd ~/.dotfiles
```
Kopiatu /etc/nixos/configuration.nix eta /etc/nixos/hardware-configuration.nix fitxategiak direktorio horretara.

```bash
cp /etc/nixos/configuration.nix .
cp /etc/nixos/hardware-configuration.nix .
```

Gero, sortu flake.nix fitxategi bat zure testu-editore gogokoenarekin.

```bash
vim flake.nix
```

Oinarrizko flake.nix fitxategiak hiru atal ditu: deskribapena, sarrerak eta irteerak.

```nix
# flake.nix

{
    description = "my nix flake";

    inputs = {};

    outputs = {};
}
```
Irteerak zure eraikitako eta konfiguratutako sistemaren irteera edo emaitzak izango dira. Sarreretan, adibidez, nixpkgs eransteko.

### Irteerak sortzea
Sarrerak gehitu ondoren, irteerak atalean sistema konfigurazioa adieraz dezakegu.

```nix
# flake.nix

{
    #...

    inputs = {
        nixpkgs = {
            url = "github:NixOS/nixpkgs/nixos-unstable";
        };
    };

    # ...
}
```
