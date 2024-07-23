## Instalar NixOS

Hay varias formas de instalar NixOS. Puedes elegir entre una máquina virtual o instalarlo en hardware dedicado. Instalar NixOS en una máquina virtual es una gran manera de probarlo, y la reproducibilidad de Nix significa que podemos copiar fácilmente una configuración de trabajo de nuestra VM a hardware dedicado más adelante. Cubriremos cómo instalar la imagen de NixOS en una VM usando VirtualBox, pero si estás siguiendo con hardware dedicado, el resto de la guía es esencialmente la misma.

### VirtualBox

Descarga el archivo ISO de tu elección desde la [fuente oficial](https://nixos.org/download). Usaremos la versión recomendada de GNOME, pero no hay diferencia si eliges Plasma o minimal en su lugar.

Puedes seguir esta [guía](https://itsfoss.com/install-nixos-vm/#dont-reboot-but-turn-off-the-vm) sobre cómo instalar NixOS en una VM VirtualBox. A continuación se muestra un resumen de los pasos:

- Abrir VirtualBox
- Haz clic en `Nuevo` en la barra de menú
- Pon un nombre a tu VM
- Elige la imagen ISO que acabas de descargar
- Selecciona `Linux` como tipo de ISO
- Elige `Other Linux (64-bit)` para la versión
- Haz clic en «Siguiente
- (Recomendado) Elige al menos 4GB de RAM
- (Recomendado) Elige al menos 2-4 núcleos de procesador
- (Recomendado) Elige al menos 30GB para esta instalación
- Si todo parece correcto, haz clic en `Finish` y VirtualBox creará una máquina virtual NixOS para ti.

- Ejecuta el instalador con la configuración que prefieres.
- En la fase de `Instalación`, puede parecer que se ha atascado en el 46%. No te preocupes, deja que el instalador haga lo suyo y compruébalo más tarde.

- En el último paso al completar el instalador, **no reinicie** sino apague la VM. De lo contrario, el instalador se cargará de nuevo.
- Para apagar la VM, selecciona la opción `Cerrar` del **menú Archivo** y selecciona `Apagar la máquina`.

- Cambiar el orden de arranque en VirtualBox
  - Para cambiar el orden de arranque en la VM de NixOS, abre la configuración de esa VM
  - En ajustes, selecciona `Sistema` y allí encontrarás el orden de arranque
  - Aquí, selecciona `Hard Disk` y usa la **flecha arriba** junto a las opciones para que sea la primera opción de arranque.
  - Pulsa `OK` para guardar los cambios realizados.
  - Alternativamente, puedes eliminar la imagen ISO que añadimos para iniciar la instalación

## Primer vistazo a NixOS

Primero echemos un vistazo a nuestro entorno recién instalado y familiaricémonos con él.

Abre una consola y navega al directorio `/etc/nixos` y mira lo que hay allí

```bash
cd /etc/nixos
ls
```

Debería ver un archivo llamado `configuration.nix` y un archivo `hardware-configuration.nix`. El `hardware-configuration.nix` está adaptado a tu sistema específico y probablemente no es algo con lo que queramos jugar, así que lo ignoraremos en el resto de esta guía.

Por otro lado, `configuration.nix` define nuestro sistema hasta ahora, echemos un vistazo al `configuration.nix` autogenerado.

```bash
sudo nano configuration.nix
```

Aquí podemos ver algunas cosas que podemos cambiar, como el nombre de host (hostname).

También vemos que los paquetes instalados se definen en dos lugares. Uno para el usuario, y el otro para los paquetes de todo el sistema.

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

Nota: cambia `username` por tu nombre de usuario.

Sugerencia: para encontrar paquetes para instalar, un buen recurso es [mynixos.com](https://mynixos.com)

Como ejemplo, vamos a añadir `vim`, `wget` y `git`, a los paquetes del sistema.

```nix
# configuration.nix

environment.systemPackages = with pkgs; [
    vim
    wget
    git
];
```

Una vez que tenemos algunos paquetes en nuestro bloque de paquetes de usuario y/o en el bloque de paquetes del sistema, podemos sincronizar el estado del sistema con el estado del archivo de configuración.

Para ello, guarda el archivo y ejecuta el siguiente comando

```bash
sudo nixos-rebuild switch
```

La parte `nixos-rebuild` le dice a NixOS que reconstruya con nuestros nuevos paquetes instalados. La parte `switch` le dice a NixOS que «cambie» al sistema recién construido.

Puedes notar que hay un montón de referencias en la salida del comando a algo llamado `/nix/store`. Esto es básicamente donde vivirán todos los programas que hayas instalado.

Intenta editar un archivo con `vim` y ahora debería estar instalado.

## Channels -> Flakes

Hasta ahora hemos estado usando channels (canales) para instalar nuestros paquetes. Pero la mayoría de la gente en la comunidad Nix está usando algo llamado **flakes**.

Los flakes tienen algunas ventajas que hacen las cosas mucho más fáciles.

Tanto los canales como los flakes gestionan los paquetes instalados en un sistema. La diferencia es que en el enfoque flake, hay un archivo llamado `flake.lock` que mantiene un registro de las versiones exactas de todos los paquetes explícitamente. Esto significa que si hacemos un seguimiento de `flake.lock` utilizando un gestor de versiones como git, entonces podemos tener una máquina del tiempo literal de lo que sucede en el sistema. En caso de que algo se rompa en el sistema, podemos volver a una versión anterior en un momento, simplemente revirtiendo nuestro repositorio git a esa versión anterior.

Así que los flakes están muy guay. El primer paso para empezar a usar flakes es habilitar la capacidad de usar flakes en nuestro archivo `configuration.nix`.

```bash
sudo vim configuration.nix
```

Al final del archivo y antes de la llave de cierre, añade la siguiente línea a tu configuración.

```nix
# configuration.nix

nix.settings.experimental-features = [ "nix-command" "flakes" ];
```

Guarda tu archivo de configuración y reconstruye de nuevo con `sudo nixos-rebuild switch`.

## Usando flakes

Preferimos crear un nuevo directorio en el directorio personal del usuario llamado `dotfiles` pero puedes elegir llamarlo como quieras.

```bash
mkdir ~/dotfiles
cd ~/dotfiles
```

Lo primero que vamos a hacer antes de inicializar nuestro flake es copiar los archivos `configuration.nix` y `hardware-configuration.nix` de `/etc/nixos`.

```bash
cp /etc/nixos/configuration.nix .
cp /etc/nixos/hardware-configuration.nix .
```

A continuación, crearemos nuestro archivo `flake.nix` utilizando nuestro editor de texto favorito.

```bash
vim flake.nix
```

Un archivo básico `flake.nix` tiene tres partes. La descripción, las inputs (entradas) y las outputs (salidas).

```nix
# flake.nix

{
    description = "my nix flake";

    inputs = {};

    outputs = {};
}
```

Las inputs contienen algunos repos de git, por ejemplo nixpkgs o nix-bitcoin. Estos le dicen a nuestro sistema dónde encontrar los paquetes que queremos instalar.

Las outputs contienen la configuración del sistema construida y en funcionamiento.

### Inputs

Para añadir nixpkgs como entrada a nuestro flake, sólo tenemos que decirle a Nix la url de dónde encontrarlo.

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

También hay una forma abreviada de reescribir lo anterior, que nos da funcionalmente el mismo resultado. Dado que nixpkgs es un repositorio especial en NixOS, no necesitamos especificar github delante de él.

```nix
# flake.nix

{
    # ...

    inputs = {
        nixpkgs.url = "nixpkgs/nixos-unstable";
    };

    # ...
}
```

### Outputs

Ahora que hemos añadido algunas inputs, podemos hacer uso de ellas en nuestras outputs.

Vamos a crear nuestra configuración NixOS en nuestras outputs utilizando las inputs que hemos añadido anteriormente.

```nix
# flake.nix

{
    # ...

    outputs = { self, nixpkgs, ... }:
    let
        lib = nixpkgs.lib;
    in {
        nixosConfigurations = {
            hostname = lib.nixosSystem {
                system = "x86_64-linux";
                modules = [ ./configuration.nix ];
            };
        };
    };

}
```

Nota: asegúrate de cambiar `hostname` por tu propio nombre de host.

Ahora podemos reconstruir nuestro sistema usando nuestro recién creado flake. Guarda `flake.nix` y sal. Ejecuta el siguiente comando para decirle a `nixos-rebuild` que use el flake en el directorio actual.

```bash
sudo nixos-rebuild switch --flake .
```

Es probable que tarde un poco en ejecutarse la primera vez, esto se debe a que NixOS está bajando el repositorio de nixpkgs. En el futuro se ejecutará mucho más rápido.

Después de que la reconstrucción se haya completado, echa un vistazo dentro de tu directorio `dotfiles` de nuevo. Deberías ver un nuevo archivo llamado `flake.lock`. Este archivo mantiene un registro de las versiones exactas de los paquetes que se instalan.

## nix-bitcoin

### flake.nix

Ahora que tenemos una configuración básica de NixOS funcionando, podemos añadir nix-bitcoin a nuestra configuración usando el enfoque flake.

Echemos un vistazo al [ejemplo flake](https://github.com/fort-nix/nix-bitcoin/blob/master/examples/flakes/flake.nix) en el repositorio nix-bitcoin.

Así que primero tenemos que añadir nix-bitcoin a nuestras inputs flake.

```nix
# flake.nix

{
  # ...

  inputs = {
    nixpkgs.url = "nixpkgs/nixos-unstable";
    nix-bitcoin.url = "github:fort-nix/nix-bitcoin/release";
  };

  # ...
}
```

Entonces podremos incluirlo en nuestros outputs.

```nix
# flake.nix

{
    # ...

    outputs = {
      self,
      nixpkgs,
      nix-bitcoin,
      ... }:
    let
        lib = nixpkgs.lib;
    in {
        nixosConfigurations = {
            hostname = lib.nixosSystem {
                system = "x86_64-linux";
                modules = [
                    ./configuration.nix
                    nix-bitcoin.nixosModules.default
                    # Optionally enable the secure-node preset
                    # to enhance security and privacy.
                    (nix-bitcoin + "/modules/presets/secure-node.nix")
                    {
                      # Automatically generate all secrets required by services.
                      # The secrets are stored in /etc/nix-bitcoin-secrets
                      nix-bitcoin.generateSecrets = true;

                      # When using nix-bitcoin as part of a larger NixOS
                      # configuration, setting the follow enables interactive
                      # access to nix-bitcoin features (like bitcoin-cli) for
                      # your system's main user
                      nix-bitcoin.operator = {
                        enable = true;
                        name = "FIXME";
                      };
                    }
                ];
            };
        };
    };

}
```

Nota: cambia `nix-bitcoin.operator.name` por tu nombre de usuario real.

Reconstruye de nuevo con `sudo nixos-rebuild switch --flake .`.

Nota: como hemos activado el preajuste de nodo seguro (secure node preset), hemos desactivado `sudo`. Utiliza `doas` en lugar de `sudo` a partir de ahora. `doas` es una alternativa más segura que `sudo`. [Ver más](https://lobste.rs/s/efsvqu/heap_based_buffer_overflow_sudo_cve_2021#c_c6fcfa) [nix-bitcoin FAQ](https://github.com/fort-nix/nix-bitcoin/blob/master/docs/faq.md)

### Añadir servicios

Ahora que nuestro sistema NixOS sabe dónde coger sus paquetes nix-bitcoin, empecemos a añadir algunos servicios.

Sugerencia: puedes ver una lista de servicios de ejemplo en [examples](https://github.com/fort-nix/nix-bitcoin/blob/master/examples/configuration.nix) proporcionado por nix-bitcoin.

Hay varias maneras de hacerlo. Por ejemplo, puedes añadirlos directamente en el flake, o puedes añadirlos a tu archivo `configuration.nix`. Vamos a tomar un enfoque _modularizado_ en su lugar. Esto significa que haremos un archivo de configuración separado para cada servicio y los importaremos individualmente a nuestro archivo `configuration.nix`. Utilizar un enfoque modular tiene varias ventajas. Al separar nuestra configuración por servicios individuales, evitamos que la configuración principal se sature y sea difícil de leer. También hace que sea más fácil de solucionar los problemas de las configuraciones individuales sin tocar otros servicios, ya que podemos simplemente desactivar un servicio si empieza a tener problemas sin afectar a otros servicios.

Para empezar, vamos a crear un nuevo directorio dentro de nuestro directorio `dotfiles` llamado `system/bitcoin` donde guardaremos nuestros archivos nix relacionados con bitcoin. Puedes llamarlo como quieras, sólo asegúrate de importar la ruta correcta más adelante.

```bash
mkdir system
mkdir system/bitcoin
```

Ahora vamos a escribir nuestro archivo `bitcoind.nix` para configurar bitcoind.

```bash
vim system/bitcoin/bitcoind.nix
```

```nix
# bitcoind.nix

{config, ...}: {
  services.bitcoind = {
    enable = true;
    prune = 0;
    txindex = true;
    zmqpubrawtx = "tcp://127.0.0.1:28333";
    zmqpubrawblock = "tcp://127.0.0.1:28332";
    listen = true;
    address = "0.0.0.0";
    # Listen to RPC connections on all interfaces
    rpc.address = "0.0.0.0";
    # Allow RPC connections from external addresses
    rpc.allowip = [
      "10.10.0.0/24" # Allow a subnet
      "10.50.0.3" # Allow a specific address
      "0.0.0.0/0" # Allow all addresses
    ];
  };
  networking.firewall.allowedTCPPorts = [
    config.services.bitcoind.port
    config.services.bitcoind.rpc.port
  ];
  # Set this to announce the onion service address to peers.
  # The onion service allows accepting incoming connections via Tor.
  nix-bitcoin.onionServices.bitcoind.public = true;
}
```

Nota: cambia `rpc.allowip` a tu red específica

Y ahora lo importamos a nuestro `configuration.nix`.

```nix
# configuration.nix

{ pkgs, ... }: {
    imports = [
        ./hardware-configuration.nix
        ./system/bitcoin/bitcoind.nix
    ];

    # ...
}
```

Reconstruye el sistema. Recuerda que ahora usamos `doas` en lugar de `sudo`.

```bash
doas nixos-rebuild switch --flake .
```

Después de la reconstrucción, deberíamos tener un servicio bitcoind funcionando. Comprobémoslo ejecutando

```bash
doas systemctl status bitcoind.service
```

Comprobemos también si nuestro usuario tiene acceso interactivo a comandos como `bitcoin-cli`.

```bash
bitcoind --version
bitcoin-cli getblockchaininfo
```

Para seguir los registros en directo, utiliza el siguiente comando

```bash
doas journalctl -fu bitcoind.service
```

Para detener el servicio, ejecuta

```bash
doas systemctl stop bitcoind.service
```

Para iniciarlo de nuevo, ejecuta

```bash
doas systemctl start bitcoind.service
```

El directorio de datos de bitcoind está instalado en `/var/lib/bitcoind` por nix-bitcoin. Vamos a echar un vistazo dentro de este directorio. Dado que está fuera del directorio personal de nuestro usuario habitual, primero tenemos que convertirnos en root.

```bash
doas su
cd /var/lib/bitcoind
ls -al
```

Observa que estos archivos son propiedad del usuario `bitcoin`.

Prueba a echar un vistazo a nuestro archivo `bitcoin.conf`.

```bash
cat bitcoin.conf
```

Refleja la configuración que hemos establecido en `bitcoind.nix`. Bien.

Por último, echemos un vistazo a donde nix-bitcoin está almacenando nuestros secretos, como nuestra contraseña rpc. Aún como superusuario, navega a `/etc/nix-bitcoin-secrets`.

```bash
cd /etc/nix-bitcoin-secrets
ls -al
```

Podemos ver que nix-bitcoin ha generado automáticamente varios archivos de contraseñas para nosotros, tal y como le dijimos en nuestro `flake.nix`.

### Bonus: migrar desde un nodo existente

Puede que ya tengas una instancia de bitcoind con una cadena de bloques totalmente sincronizada y no quieras sincronizar la cadena de nuevo. La buena noticia es que basta con copiar la cadena de bloques del nodo existente.

1. Detener `bitcoind` en ambos nodos

```bash
doas systemctl stop bitcoind.service
```

2. Copia el directorio de datos en el nodo nix-bitcoin

```bash
# Important: Add a trailing slash to the source path
rsync root@existing-bitcoin-node:/path/to/existing/bitcoind-datadir/ /var/lib/bitcoind
```

3. Arreglar permisos en el nodo nix-bitcoin

```bash
doas chown -R bitcoin: /var/lib/bitcoind
```

4. Iniciar `bitcoind

```bash
doas systemctl start bitcoind.service
```

Puedes utilizar el mismo flujo de trabajo para otros servicios. Ver [source](https://github.com/fort-nix/nix-bitcoin/blob/master/docs/configuration.md#migrate-existing-services-to-nix-bitcoin) para más servicios.
