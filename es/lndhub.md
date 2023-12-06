LNDhub permite importar fácilmente una billetera en aplicaciones compatibles. Si bien puedes guardar tu billetera BitcoinTxoko LNbits en tu teléfono como una
aplicación web progresiva (PWA), una aplicación nativa como [Zeus](https://zeusln.app/) o [BlueWallet](https://bluewallet.io/) ofrece
una mejor experiencia de usuario así como un mayor nivel de seguridad. Con [Alby](https://getalby.com/),
también puedes importar la billetera a la extensión de tu navegador para conseguir una
experiencia web sencilla con Lightning y para los zaps de Nostr. Es posible importar tu
cartera de LNbits a Zeus, BlueWallet o Alby con [LNDhub](https://github.com/BlueWallet/LndHub/tree/master). En esta guía cubriremos cómo
hacerlo con Alby y Zeus. Con la configuración de Alby, uno de los pasos también te
permitirá importar fácilmente tu billetera a Zeus. Pero si solo quieres importar tu billetera
a Zeus, puedes saltar directamente a la sección de Zeus.

### Alby
Alby es una extension que te acerca Lightning y Nostr a tu navegador. Utilizando el
protocolo [WebLN](https://www.webln.dev/), esta extension puede detectar facturas LN en paginas web y pagarlas,
así como posibilita iniciar sesión en sitios web con Lightning. También puedes fijar
presupuestos para tus sitios favoritos de Lightning. Por otro lado también puede utilizarse
para firmar en Nostr utilizando [NIP-07](https://github.com/nostr-protocol/nips/blob/master/07.md), lo cual es mucho mas seguro que ingresar tu clave
privada en clientes web.

#### ¿Qué necesito?
- Un navegador web que soporte extensiones Chrome o Firefox. En Android las
soporta [Kiwi Browser](https://kiwibrowser.com/) 
- Acceso a tu billetera LNbits. Si todavía no tienes una billetera LNbits, dirígete a [nuestra página de billeteras](https://bitcointxoko.com) y crea una. Asegúrate de guardar el enlace de tu billetera para poder volver a ella más tarde.
- Un dispositivo móvil para configurar Zeus

#### 1. Habilita la extensión LNDhub en tu LNbits wallet
En tu navegador, dirígete al enlace de tu cartera. Haz clic en `Extensiones` y habilita la
extension `LNDhub`. Una vez se haya habilitado, dirigente a la pagina de extension de
LNDhub.

#### 2. Instala la extensión Alby
Dirígete a [getalby.com](https://getalby.com/) y haz clic en `Añadir extensión del navegador`. Instala la extensión
desde el store (almacén) de extensiones del navegador. Configura tu contraseña de
desbloqueo y guárdala en un lugar seguro.

#### 3. Importar a Alby
![alby-config](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/lndhub/alby-config.png)
(Esta es una cartera de prueba. no hay fondos en ella. No muestres a nadie tu URI de exportación real!)

En la siguiente pantalla, elige `Conectar` y luego elige `LNDhub`. Vuelve a tu extensión
LNDhub y copia la URL de conexión. Pégalo en el campo `URI de exportación de
LNDhub`. Pulse continuar. ¡Ahora deberías haber estado conectado a tu cartera de LNbits
con LNDhub!

💡 Puedes elegir entre la URL de la factura y la URL de administración. Le dan a Alby
diferentes permisos para interactuar con tu cartera de LNbits.

- La URL de factura te permite crear facturas y recibir pagos
- La URL de administración también te permite enviar pagos

#### 4. Configurar Zeus con Alby (opcional)
![alby-export](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/lndhub/alby-export.png)

Ahora que ya has conectado tu LNbits con Alby, también puedes importarlo de una
manera sencilla a Zeus con Alby. Simplemente debes abrir la extensión, hacer cilc en el
nombre de tu billetera e ir a configuración de la cuenta. En `Cuenta` se encuentra la
opción de conectar tu billetera móvil. Al pulsar conectar, se mostrará un código QR para
escanear desde Zeus.

Si no tienes instalada Zeus con anterioridad, dirígete a [zeusln.app](https://zeusln.app/) y descarga la
aplicación de Zeus para tu sistema operativo móvil.

Una vez tengas descargado Zeus, entra en `Configuración` > `Añadir un nuevo nodo`. Aquí
puedes escanear el código QR que te muestra Alby para importar la cartera.

Voilà! Ya tienes el poder de Lightning en las yemas de tus dedos ¿Ya te sientes como un dios?

### Zeus
Zeus es una formidable aplicación de código abierto que permite conectar tu propio nodo
a tu dispositivo movil. Es compatible con todas las principales implementaciones de
nodos Lightning, como LND, CLN y Eclair, así como conexiones a través de Tor y
clearnet. Recientemente también han anunciado su propio LSP ( Lightning Service
Provider), puedes unirte a la lista de espera [aquí](https://olympusln.com/). 

### ¿Qué necesito?
- Teléfono Android o iOS
- Otro dispositivo en el que puede acceder a su billetera LNbits (para mostrar el código QR para escanear)
- Acceso a tu billetera LNbits. Si todavía no tienes una billetera LNbits, dirígete a [nuestra página de billeteras](https://bitcointxoko.com) y crea una. Asegúrate de guardar el enlace de tu billetera para poder volver a ella más tarde.
  
#### 1. Descarga Zeus
Puedes descargar la aplicación Zeus para tu sistema operativo [aquí](https://zeusln.app/).

#### 2. Habilita la extension LNDhub en su billetera LNbits
Dirigete al enlace de tu cartera desde el navegador. Haz clic en `Extensiones` y habilita la
extension `LNDhub`. Una vez habilitada, ve a la pagina de la extensión LNDhub.

#### 3. Importar a Zeus
Ve a `Configuración` > `Añadir un nuevo nodo en Zeus`.

Escanea la cartera que quieras instalar.

💡 Puedes elegir entre la URL de la factura y la URL de administrador.
- La URL de la factura te da permiso para generar facturas y recibir pagos.
- La URL de administración también te permite enviar pagos.

Una vez que hayas escaneado el código QR, todos los campos en Zeus deberían
rellenarse automáticamente. También puedes añadir un apodo para tu cartera.

![zeus-config](https://github.com/bitcointxoko/guides/blob/main/images/lndhub/zeus-config.png)

¡Ahora puedes guardar la configuración del nodo y controlar la cartera desde tu teléfono!

#### Extra
Zeus también ofrece características interesantes como el modo lurker y la verificación
biométrica. También ofrece la posibilidad de habilitar las conversiones de precios a la
moneda fiduciaria que elijas. También, puedes personalizar la pantalla de la aplicación a
tu gusto. Estos temas están más allá del alcance de esta guía, ¡juega en la aplicación y
descubre todas esas características por ti mismo!
