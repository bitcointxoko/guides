### ¿Qué es una dirección Lightning o Lightning address?
Una dirección Lightning es una dirección que visualmente se asemeja a una dirección de correo
electrónico legible para los humanos, por ejemplo usuario@dominio.com pero que en realidad te
permite recibir pagos en bitcoin instantáneos y económicos, sin la necesidad de tener un nodo en linea en tu dispositivo ni tener que generar facturas de forma manual cada vez que alguien te
quiere hacer un pago.

¿Suena bien no?

### ¿Y cómo funciona?
Funciona utilizando el [protocolo de pago LNURL](https://github.com/lnurl/luds/blob/legacy/lnurl-pay.md).

![Aquí se muestra un sencillo esquema de lo que ocurre en segundo plano.](https://blob.satellite.earth/908a8572fe3ec8c5b17bcbae1065b69af15b39958401c87128723f3250122cec)Aquí se muestra un sencillo esquema de lo que ocurre en segundo plano.

En resumen, cuando otro usuario quiere pagarte usando tu dirección Lightning, tu billetera convierte la dirección Lightning en una solicitud de pago LNURL. Luego se utiliza esa solicitud de pago LNURL exitosa para obtener una factura BOLT11.

💡 Dirección Lightning > LNURLp > Factura BOLT 11.

### Suena bien, pero ¿cuál es el problema?
Por el momento, muchas de las implementaciones de Lightning Address son de custodia, porque
se necesita un dominio para que Lightning Address funcione y un nodo que esté siempre en línea para recibir los pagos. Debido a que es de custodia, el custodio puede atacarte en cualquier momento y monitorear tus transacciones.

Tienes que confiar en el propietario del dominio para no cambiar el registro de tu dirección
Lightning. Y no funciona si el servidor LNURL no está en línea.

Bitcoin Txoko ofrece una sencilla solución de Lightning Address respaldada por [LNbits](https://lnbits.com/). Esto
también es de custodia, así que por favor mantén solo una pequeña cantidad en tu billetera Bitcoin
Txoko y ve retirando a tu billetera de autocustodia a medida que recibas más sats.

### Estoy listo, ¿qué necesito para empezar?
¡Todo lo que necesitas es un teléfono móvil o un ordenador y una conexión a Internet!

### 1. Creando tu billetera
Si aún no lo has hecho, navega a https://bitcointxoko.com y crea una nueva billetera. Puedes elegir el
nombre que quieras.

### 2. Activar extensiones
Hace falta la extensión `Pay Links` para que las direcciones Lightning funcionen.

Abre `Extensiones` en la barra de herramientas y activa `Pay Links`.

### 3. Creando tu enlace de pago
- En a la extensión `Pay Links`, haz clic en `New Pay Link`.

- Elige la billetera que has creado.

- Para la descripción del artículo, puedes escribir lo que quieras.

- Elige un nombre de usuario de tu dirección Lightning. Tu dirección Lightning se verá como `username@bitcointxoko.com`. 

- Desmarque `Fixed amount` y cambia el valor mínimo a 1 y el valor máximo a 500000.

⚠️ También puedes cambiar el valor máximo a algo más alto, pero es más probable que los pagos más grandes fallen debido a la limitada capacidad de entrada del [nodo Lightning de Bitcoin Txoko](https://amboss.space/node/03fb64900a7647b4499a88a6c30976333074dad3bb7702d0219bd84dc4ac4a241e). Así que recomendamos mantenerlo en 500000 sats.

- Ahora abre `Advanced options` y cambia `Comment maximum characters` a 799. Este paso no es necesario pero permite más funcionalidades más adelante.

- Marca `Enable nostr zaps` en la parte inferior, para que puedas utilizar tu dirección Lightning para recibir zaps.

- Las demás opciones avanzadas son opcionales, puedes configurarlas si quieres o dejarlas en
blanco.

![Al final debería verse algo así.](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/lnurlp/lnurlp-config.png)

Al final debería verse algo así.

- Cuando hayas comprobado que todo es correcto, sigue adelante y haz clic en `Create Pay Link`.

### Probando
Puedes probar si tu nueva dirección Lightning funciona yendo a otra cartera, pulsando en `Enviar` y escribiendo tu dirección Lightning como destino, y luego enviándote una pequeña cantidad de sats.

Vuelve a tu billetera Bitcoin Txoko y comprueba si has recibido tu propio pago. Es posible que
tengas que actualizar la página.

Si todo funcionó correctamente, ¡enhorabuena! 🥳

Si no es así, háznoslo saber. Siempre estamos aquí para ayudar.

### Próximos pasos

#### Nostr zaps
Puedes añadir tu dirección Bitcoin Txoko Lightning a tu perfil de nostr y usarla para recibir zaps.
Normalmente, esto se hace yendo a `Perfil` > `Editar` > `Dirección Lightning` y
cambiando la dirección Lightning.

#### LNDhub
Puedes importar tu billetera LNbits como un LNDhub en tu teléfono utilizando una aplicación
como [Zeus](https://zeusln.app/) o [BlueWallet](https://bluewallet.io/), en lugar de visitar la billetera en el navegador cada vez que deseas
comprobar tu saldo o realizar un pago. Echa un vistazo a nostr:naddr1qvzqqqr4gupzqkvlvlma7a55ccp6d5rrdc27h3ssmdmael286mjaq5uxmqslk04fqqxnzd3exuerqdfkxccnyv3cs0uvul sobre cómo hacer esto.

#### Código QR
También puedes compartir o imprimir tu código QR LNURLp para que la gente pueda escanearlo
fácilmente con sus teléfonos. ¡Muy útil si estás introduciendo bitcoin a tu comerciante local
favorito para que pueda recibir propinas Lightning!

Simplemente comparte el enlace a tu página compartida, o imprime el código QR como PDF
yendo a `View Link` > `Print`.
