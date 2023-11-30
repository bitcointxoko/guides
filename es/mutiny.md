[Mutiny Wallet](https://www.mutinywallet.com/) es un monedero Bitcoin y Lightning de autocustodia de código abierto que funciona tanto en el navegador como para aplicaciones nativas en Android e iOS (TestFlight, de pago). No solo es probablemente la forma más cómoda de enviar zaps de autocustodia de un solo toque en nostr, sino también la forma más sencilla de incorporar nuevos usuarios a la autocustodia de Bitcoin. En esta guía nos sumergiremos en cómo el equipo de Mutiny ha hecho esto posible usando la magia que es nostr. 

⚠️ Mutiny Wallet es un software beta. Utilice monedas signet para probarlo y no deposite más fondos de los que esté dispuesto a perder.

## Ejecutar Mutiny
### Web
Mutiny puede ejecutar un nodo Lightning en un navegador web. ¿Cómo funciona? Una explicación sencilla es que un nodo Lightning se compone de varias partes, incluyendo el sincronizador de chismes, el explorador de bloques, la máquina de estados y el firmante. Mutiny separa estas partes de forma que sólo el firmante se almacena localmente, mientras que las otras partes se acceden remotamente a través de la API.

Para ejecutar Mutiny en tu navegador, simplemente navega hasta https://app.mutinywallet.com. A continuación, puedes guardar la página como una Progressive Web App para facilitar el acceso. En la mayoría de los navegadores, esta opción se llama "Instalar aplicación" o "Añadir a la pantalla de inicio".

Alternativamente, puedes probar [Mutiny autoalojado por Bitcoin Txoko](https://mutiny.bitcointxoko.com), pero algunas características como gifting y contactos nostr no funcionan todavía. Puedes seguir este [tema](https://github.com/MutinyWallet/mutiny-deploy/issues/5) en GitHub para actualizaciones.

Si decides utilizar Bitcoin Txoko, ten en cuenta que sólo estamos ejecutando el frontend, el proxy websockets para conectar con la Red Lightning y el [Versioned Storage Service (VSS)](https://github.com/lightningdevkit/vss-server) para almacenar los estados Lightning. Para el sincronizador de chismes y el explorador de bloques, te recomendamos que utilices los que Mutiny proporciona por defecto. Para añadirlos,
- Ve a `Settings` > `Servers`.
- En `Esplora`, escribe` https://mutiny.mempool.space/api`
- En `RGS`, pega `https://scorer.mutinywallet.com/v1/rgs/snapshot/`
- Los demás campos deberían rellenarse por defecto, incluido el LSP.
- Pulse Guardar.
### Android
El APK de Mutiny para Android puede descargarse directamente desde [GitHub](https://github.com/MutinyWallet/mutiny-web/releases). Recomendamos utilizar [Obtainium](https://github.com/ImranR98/Obtainium) para gestionar tus aplicaciones Android, consulta nuestra [Guía].

### iOS (TestFlight)
Mutiny Wallet está disponible de forma gratuita, pero también puedes pagar para desbloquear funciones y apoyar su desarrollo suscribiéndote a Mutiny+.

Para suscribirte a Mutiny+ primero necesitas tener al menos 10500 sats en el saldo Lightning de tu cartera Mutiny. Cubriremos la financiación de tu cartera más adelante en esta guía. Después de haber financiado el monedero, ve a `Settigs` > `Mutiny+` para suscribirte. Una vez que hayas pagado tu suscripción, haz clic en el enlace de acceso a la beta de iOS en la pestaña Mutiny+ para obtener una invitación TestFlight.

## Financiar tu billetera
La forma más sencilla de empezar a realizar transacciones con tu billetera Mutiny es recibir un pago Lightning. Se abrirá automáticamente un canal para ti en este proceso desde el LSP [Voltage Flow 2.0](https://amboss.space/node/03aefa43fbb4009b21a4129d05953974b7dbabbbfb511921410080860fca8ee1f0). Para ello, pulsa `Receive`, lee atentamente el aviso sobre el tamaño mínimo del canal y las tarifas de configuración y, a continuación, establece una cantidad a recibir. Paga la factura y debería tener un canal funcionando en cuestión de minutos.

También puedes enviar fondos on-chain a tu cartera Mutiny y abrir un canal tú mismo. Una vez confirmado el saldo en la cadena, aparecerá un botón de intercambio. Al hacer clic en él, podrá cambiarlo por Lightning.

💡 Con Mutiny no estás encerrado en el uso de un único nodo. Puedes conectar Mutiny a otro nodo en lugar del LSP Voltage Flow 2.0 predeterminado. Para conectarte al nodo de tu elección, ve a `Settings` > `Admin Page`. Primero conecta tu nodo como un peer bajo `Connect Peer` pegando la dirección del nodo siguiendo el formato `pubkey@address`, después abra un canal (`Open Channel`) al nodo introduciendo `Pubkey` y `Amount`. El canal deberá alcanzar 6 confirmaciones antes de poder ser utilizado.

## Respaldo
Ya puedes empezar a realizar transacciones con Mutiny una vez hayas cargado el monedero en tu navegador o app, pero lo más prudente sería asegurar tus fondos haciendo una copia de seguridad.

El proceso es sencillo. Haz clic en Copia de seguridad en la página principal y escribe las 12 palabras. Opcionalmente puedes añadir una contraseña para encriptar tus palabras semilla.

Si has olvidado tus palabras clave, puedes volver a verlas en Configuración > Copia de seguridad.
## Nostr
### Zaps
¡Zaps con un solo toque! Esto es posible gracias a [NIP-47 Nostr Wallet Connect (NWC)](https://github.com/nostr-protocol/nips/blob/master/47.md).

Para empezar a utilizar Wallet Connect,
- Ve a `Settings` y `Wallet Connections` en `Beta Features`.
- Crea una nueva conexión con `Add Connection`. 
- Dale un nombre para recordar para qué sirve.
- Si quieres la verdadera experiencia de zapping con un solo toque, marca la casilla junto a `Auto Approve` y establece un presupuesto para esta conexión de monedero. De lo contrario, tendrás que volver a Mutiny para aprobar las transacciones pendientes manualmente. 
- Una vez que esté satisfecho con el presupuesto, haz clic en `Create Connection` y se te mostrará un código QR. Puedes escanearlo desde un cliente Nostr en un dispositivo independiente o seleccionar `Open in Nostr Client` para abrirlo en un cliente en el mismo dispositivo. El cliente Nostr debe soportar NWC para que funcione.
	- En Amethyst, puede que tengas que pegar los diferentes campos por separado.

### Contactos
Puedes importar tu npub para ver a quién están haciendo zapping tus contactos. Ve a `Settings` >`Sync Nostr Contacts`. Introduce tu npub de Nostr y en cuestión de segundos podrás ver a tus contactos haciendo zaps.

### Regalos
Mutiny facilita más que nunca el acceso a los precoiners. Si alguien puede acceder a un navegador web, puede recibir sats. Sin excusas. Y lo que es aún mejor, ¡todo el proceso es autocustodiable! ¿La única instrucción que tienes que dar? Escanear el código QR.

Para crear un regalo, debes estar suscrito a Mutiny+. Una vez hecho esto (y realmente deberías hacerlo, es una obviedad), ve a `Gifting` en `Beta Features`. Introduce el nombre del destinatario y selecciona el importe. Después de hacer clic en `Create a gift`, tendrás un código QR y una URL.

Para canjear un regalo, el nuevo usuario sólo tiene que escanear el código QR o abrir el enlace en un navegador. El LSP les abrirá un canal mientras canjean el regalo. Ten en cuenta que tu monedero tiene que estar abierto y en línea para que el destinatario pueda canjear el regalo.

Entre bastidores, todo esto se hace utilizando Nostr Wallet Connect. El código QR contiene la información que el destinatario necesita para crear una factura. El monedero del remitente está a la escucha de la factura desde un relay y la paga en cuanto la ve.

💡 Si eres realmente tacaño y no quieres pagar por Mutiny+, puedes [autoalojar](https://blog.mutinywallet.com/self-hosting-mutiny/) Mutiny. En cualquier caso, te animamos encarecidamente a que apoyes el desarrollo de Mutiny. Puedes hacer zaps aquí: nostr:npub1mutnyacc9uc4t5mmxvpprwsauj5p2qxq95v4a9j0jxl8wnkfvuyque23vg.
### Mutiny+
Mutiny construyó la facturación automática de suscripciones sobre Lightning usando... lo has adivinado, NWC. Una suscripción es un evento NWC, que creará facturas mensualmente. ¿No es genial? Además, se puede cancelar en cualquier momento, simplemente eliminando la conexión del monedero. Puedes leer todo sobre la función de suscripción de Mutiny [aquí](https://blog.mutinywallet.com/solving-subscriptions-on-bitcoin-one-zap-at-a-time/). 
## Migración
Hay dos opciones cuando se trata de migrar tu monedero a otro dispositivo, o migrar del navegador a aplicaciones nativas. Puedes migrar usando el archivo de estado, que es el método recomendado, o puedes usar tu frase semilla de respaldo. Consulta la [guía oficial](https://blog.mutinywallet.com/migrate-mutiny-wallet-to-the-native-apps/) para ver todos los pasos.
## Conclusión
Cuando Nostr se une a Lightning, ocurren cosas maravillosas. Mutiny Wallet lo ha demostrado con zaps de un solo toque, suscripciones y regalos, todo ello funcionando con Nostr Wallet Connect.

Pero eso no es todo lo que ofrece Mutiny. Hay nuevas y emocionantes funciones en preparación, como RedShift y Synthetic USD. Mantente al día sobre Mutiny en [Mutiny Blog](https://blog.mutinywallet.com/).

¿Te ha resultado útil esta guía? Prueba a enviarnos un zap de un solo toque desde tu flamante cartera Mutiny. :)
