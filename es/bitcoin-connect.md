[Bitcoin Connnect](https://bitcoin-connect.com/) es una forma sencilla de conectar billeteras Lightning a sitios web en cualquier navegador mediante WebLN. Esto puede ser especialmente útil en navegadores móviles que no permiten instalar extensiones. 

nostr:nevent1qqs9h5lk24vu4ms9s873d8yvmwzs90h37zn68ck0krj886fe89vgdrcpz4mhxue69uhhyetvv9ujuerpd46hxtnfduhszxthwden5te0wfjkccte9eekummjwsh8xmmrd9skctcpzamhxue69uhkzarvv9ejumn0wd68ytnvv9hxgtcpzamhxue69uhhyetvv9ujuurjd9kkzmpwdejhgtcppemhxue69uhkummn9ekx7mp0qythwumn8ghj7un9d3shjtnwdaehgu3wvfskuep0qywhwumn8ghj7mn0wd68ytnzd96xxmmfdejhytnnda3kjctv9uq3zamnwvaz7tmwdaehgu3wwa5kuef0qyfhwumn8ghj7ur4wfcxcetsv9njuetn9uq3yamnwvaz7tmsw4e8qmr9wpskwtn9wv4drcwx

Bitcoin Connect puede conectar distintos tipos de billeteras Lightning, desde Nostr Wallet Connect (NWC, [NIP-47](https://github.com/nostr-protocol/nips/blob/master/47.md)) hasta el uso de tu propio nodo. 

Anteriormente hemos cubierto cómo utilizar Nostr Wallet Connect para conectar tu billetera Mutiny a sitios web y aplicaciones en la [Guía Mutiny], ahora puedes conectar tu billetera Bitcoin Txoko LNbits a Coracle o Nostrudel utilizando Bitcoin Connect para hacer zaps con un solo toque. ¡Vamos a probarlo!

## Crear una billetera para zaps

Si eres nuevo en Bitcoin Txoko, primero crea una billetera en [bitcointxoko.com](https://bitcointxoko.com). 

Dado que existe un cierto grado de confianza en el sitio web y en que no hay scripts maliciosos de terceros leyendo la conexión desde el almacenamiento o la memoria, sería prudente configurar una billetera independiente para su uso con Bitcoin Connect con su propio presupuesto en lugar de vincular tu billetera principal. Afortunadamente, esto sólo requiere dos clics en LNbits. Simplemente haz clic en `+ Agregar nueva billetera` en la barra de herramientas, dale un nombre a la billetera y créalo. Transfiera un pequeño presupuesto para zapear a la billetera recién creada. 

Una vez que tengas un monedero listo, busca la sección `Documentos de API` y toma nota de tu *admin key*. La necesitaremos más tarde para conectar esta billetera usando Bitcoin Connect. 

![adminkey](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/bitcoin-connect/adminkey.png)⚠️ Esto es sólo una billetera vacía para la demostración. No muestres tu *admin key* a nadie!

💡 Puedes seguir recibiendo zaps en tu dirección Lightning vinculada a tu billetera principal como explicamos en la nostr:naddr1qqxnzd3exuerqdp3xv6ngd3kqgs9n8m87l0hd9xxqwndqcmwzh4uvyxmwlw0637kuhg98pkcy8ana2grqsqqqa28d2sgyz. Esta guía solo se aplica al **envío** de zaps. 

## Coracle

Varias aplicaciones web, especialmente en el ecosistema Nostr, ya han implementado Bitcoin Connect como método de conexión de billeteras, incluyendo [Habla](https://habla.news/), [Snort](https://snort.social/)/[Iris](https://iris.to/) y [Zap.stream](https://zap.stream/), y seguramente le seguirán más. Sin embargo, que yo sepa, [Coracle](https://coracle.social/) y [nostrudel](https://nostrudel.ninja/) son los primeros que permiten utilizar Bitcoin Connect con una billetera [LNbits](https://lnbits.com/). 

Si no estás familiarizado con él, Coracle es un cliente social de Nostr que soporta una amplia gama de NIPs y puede ser instalado como una Progressive Web App (PWA). Una característica destacable es que también soporta Nostr Connect ([NIP-46](https://github.com/nostr-protocol/nips/blob/master/46.md)), que te permite iniciar sesión usando un servidor que firma eventos en tu nombre como [nsecbunker](https://nsecbunker.com/). Esto significa que, emparejado con Bitcoin Connect, puedes utilizarlo sin ninguna extensión, por ejemplo, en navegadores móviles. 

## Probar Bitcoin Connect

1. Navega hasta [coracle.social](https://coracle.social) e inicia sesión con el método que prefieras. 
2. Ve a `Settings` y busca la sección `App Settings`. 
3. Pulsa "Connect Wallet" en la sección Bitcoin Connect. 
4. Elige `LNbits` como método de conexión. Ten en cuenta que también puedes utilizar NWC, como se explica en la [Guía de Mutiny], u otros métodos de conexión. 
5. Introduce la *admin key* que has anotado antes y `https://bitcointxoko.com` como URL de LNbits. Conecta la billetera. 
6. Ahora deberías ver el saldo de tu billetera. Ya estás listo para hacer zaps!

![coracle](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/bitcoin-connect/coracle.png)

💡 Si lo prefiere, puede hacer lo mismo con [nostrudel](https://nostrudel.ninja/). 

## Conclusión

Creemos que la combinación de Bitcoin Connect y Nostr Connect supera un gran obstáculo de experiencia de usuario cuando se trata de utilizar clientes Nostr en móviles. No sólo los usuarios móviles ya no dependen de extensiones complicadas, sino que también permite a los clientes web competir con los clientes nativos, que a menudo se quedan atrás en el desarrollo y carecen de ciertas funcionalidades debido a la censura de la tienda de aplicaciones. 

Esperamos que esta breve guía te haya resultado útil. Si es así, prueba a zapear este artículo con tu billetera recién conectada!
