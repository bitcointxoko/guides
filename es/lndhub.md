LNDhub te permite importar fácilmente una billetera en aplicaciones compatibles. Si bien puedes guardar tu billetera Bitcoin Txoko LNbits en tu teléfono como una
aplicación web progresiva (PWA), una aplicación nativa como [Zeus](https://zeusln.app/) o [BlueWallet](https://bluewallet.io/) ofrece
una mejor experiencia de usuario así como un mayor nivel de seguridad. Con [Alby](https://getalby.com/),
también puedes importar la billetera a la extensión de tu navegador para facilitar los pagos Lightning en la web y para los zaps de Nostr. Por suerte para nosotros, todas estas billeteras hablan un lenguaje común llamado [LNDhub](https://github.com/BlueWallet/LndHub/tree/master). 

En esta guía cubriremos cómo importar la billetera a tu navegador y a tu móvil. Si quieres usar tu billetera tanto en el navegador como en tu móvil, empieza con [la configuración de Alby](#Alby), ya que uno de los pasos te permitirá importar fácilmente tu billetera también a Zeus. Pero si sólo te interesa utilizar la billetera en tu móvil, puedes pasar directamente a [la sección de Zeus](#Zeus).

### Alby

nostr:nprofile1qqsyv47lazt9h6ycp2fsw270khje5egjgsrdkrupjg27u796g7f5k0s8jq7y6 es una extensión de navegador que lleva Lightning y Nostr a tu navegador. Utilizando el
protocolo [WebLN](https://www.webln.dev/), esta extensión puede detectar facturas LN en paginas web y pagarlas,
así como posibilita iniciar sesión en sitios web con Lightning. También puedes fijar
presupuestos para tus sitios favoritos de Lightning. Por otro lado también puedes utilizarla
para firmar en Nostr utilizando [NIP-07](https://github.com/nostr-protocol/nips/blob/master/07.md), lo cual es mucho más seguro que ingresar tu clave
privada en clientes web.

#### ¿Qué necesito?
- Un navegador web que soporte extensiones Chrome o Firefox
- Acceso a tu billetera LNbits. Si todavía no tienes una billetera LNbits, dirígete a [nuestra página de billeteras](https://bitcointxoko.com) y crea una
- (Opcional) Un dispositivo móvil para configurar Zeus

#### 1. Habilita la extensión LNDhub en tu LNbits wallet
Dirígete a tu billetera LNbits. Haz clic en `Extensiones` y habilita la
extensión `LNDhub`. Una vez se haya habilitado, dirígete a la página de extensión de
LNDhub.

#### 2. Instala la extensión Alby
Dirígete a [getalby.com](https://getalby.com/) y instala la extensión
desde el store de extensiones del navegador. Configura tu contraseña de
desbloqueo y guárdala en un lugar seguro.

#### 3. Importar a Alby
![alby-config](https://cdn.satellite.earth/2074a44ea548ce28368d0aba2d54eafdc698159c5ee0956afa87fa155e3b511d.webp)
(Esta es una billetera de prueba. No hay fondos en ella. ¡No muestres a nadie tu URI de exportación real!)

En la siguiente pantalla, elige `Conectar` y luego elige `LNDhub`. Vuelve a tu extensión
LNDhub y copia la URL de conexión. Pégala en el campo `URI de exportación de
LNDhub`. Pulsa continuar. ¡Ahora deberías haber estado conectado a tu billetera de LNbits
con LNDhub!

💡 Puedes elegir entre la URL de la factura (Invoice URL) y la URL de administración (Admin URL). Le dan a Alby
diferentes permisos para interactuar con tu cartera de LNbits.

- La URL de factura te permite crear facturas y recibir pagos
- La URL de administración también te permite enviar pagos

#### 4. Configurar Zeus con Alby (opcional)
![alby-export](https://cdn.satellite.earth/8807b296bb8bd6086a795616cc49068a17d93df450d0a65ce3818e5539eb6a09.webp)

Ahora que ya has conectado tu LNbits con Alby, también puedes importarlo de una
manera sencilla a Zeus con Alby. Abre la extensión, haz cilc en el
nombre de tu billetera y navega a la configuración de la cuenta. En `Wallet Settings` > `General` se encuentra la
opción de conectar tu billetera móvil. Al pulsar conectar, se mostrará un código QR para
escanear desde Zeus.

Si no tienes instalada Zeus con anterioridad, dirígete a [zeusln.app](https://zeusln.app/) y descarga la
aplicación de Zeus para tu sistema operativo móvil.

Una vez tengas descargado Zeus, entra en `Configuración` > `Añadir un nuevo nodo`. Aquí
puedes escanear el código QR que te muestra Alby para importar la billetera.

Voilà! Ahora tienes el poder de Lightning al alcance de la mano ¿Ya te sientes como un dios?

### Zeus
nostr:nprofile1qqsrf5h4ya83jk8u6t9jgc76h6kalz3plp9vusjpm2ygqgalqhxgp9g84ctjf es una formidable aplicación de código abierto que permite conectar tu propio nodo
a tu dispositivo movil. Es compatible con todas las principales implementaciones de
nodos Lightning, como LND, CLN y Eclair, así como conexiones a través de Tor y
clearnet. Recientemente también han anunciado su propio LSP (Lightning Service
Provider). 

### ¿Qué necesito?
- Teléfono Android o iOS
- Otro dispositivo en el que puede acceder a tu billetera LNbits (para mostrar el código QR para escanear)
- Acceso a tu billetera LNbits. Si todavía no tienes una billetera LNbits, dirígete a [nuestra página de billeteras](https://bitcointxoko.com) y crea una
  
#### 1. Descarga Zeus
Puedes descargar la aplicación Zeus para tu sistema operativo [aquí](https://zeusln.app/).

#### 2. Habilita la extensión LNDhub en tu billetera LNbits
Dirígete a tu billetera LNbits. Haz clic en `Extensiones` y habilita la
extensión `LNDhub`. Una vez habilitada, abre la pagina de la extensión LNDhub.

#### 3. Importar a Zeus
Ve a `Configuración` > `Añadir un nuevo nodo en Zeus`.

Escanea la cartera que quieras instalar.

💡 Puedes elegir entre la URL de la factura (Invoice URL) y la URL de administración (Admin URL). 
- La URL de la factura te da permiso para generar facturas y recibir pagos.
- La URL de administración también te permite enviar pagos.

Una vez que hayas escaneado el código QR, todos los campos en Zeus deberían
rellenarse automáticamente. También puedes añadir un apodo para tu billetera.

![zeus-config](https://cdn.satellite.earth/3be62f55d32460b7aa33d58fd9c25f3260e379ddde60fa1fe2c99016915da8b3.webp)

¡Ahora puedes guardar la configuración del nodo y controlar la billetera desde tu teléfono!

#### Extra
Zeus también ofrece funciones interesantes como temas personalizados, conversiones de precios, modo acechador y verificación biométrica. Estos temas están más allá del alcance de esta guía, ¡juega en la aplicación y
descubre todas esas características por ti mismo!
