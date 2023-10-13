### ¿Qué es una dirección Lightning o Lightning address?
Una dirección Lightning es una dirección que visualmente se asemeja a una dirección de correo
electrónico legible para los humanos, por ejemplo usuario@dominio.com pero que en realidad te
permite recibir pagos en bitcoin instantáneos y económicos, sin la necesidad de tener un nodo en linea en tu dispositivo ni tener que generar facturas de forma manual cada vez que alguien te
quiere hacer un pago.

¿Suena bien no?

### ¿Y cómo funciona?
Funciona utilizando el [protocolo de pago LNURL](https://github.com/lnurl/luds/blob/legacy/lnurl-pay.md), una capa en la parte superior de Lightning Network.

![Aquí se muestra un sencillo esquema de lo que ocurre en segundo plano.](https://camo.githubusercontent.com/268abc621585b68fbf1229eab51c3c9344870ec3f227a1ff237c7423ba3ba28e/68747470733a2f2f692e696d6775722e636f6d2f444956357138712e706e67)Aquí se muestra un sencillo esquema de lo que ocurre en segundo plano.

En resumen, cuando otro usuario quiere pagarte usando tu dirección Lightning (Lightning
Address), tu billetera convierte la dirección Lightning en una solicitud de pago LNURL. Luego se
utiliza esa solicitud de pago LNURL exitosa para obtener una factura BOLT11.

💡 Dirección Lightning -> LNURLp -> Factura BOLT 11.

### Suena bien, pero ¿cuál es el problema?
Por el momento, la mayoría de las implementaciones de Lightning Address son custodia, porque
se necesita un dominio para que Lightning Address funcione. Debido a que es de custodia, el
custodio puede atacarte en cualquier momento y monitorear tus transacciones.

Tienes que confiar en el propietario del dominio para no cambiar el registro de tu dirección
Lightning. Y no funciona si el servidor LNURL no está en línea.

Bitcoin Txoko ofrece una sencilla solución de Lightning Address respaldada por [LNbits](https://lnbits.com/). Esto
también es custodio, así que por favor mantén solo una pequeña cantidad en tu billetera Bitcoin
Txoko y ve retirando a tu billetera de autocustodia a medida que recibas más sats.

### Estoy listo, ¿qué necesito para empezar?
¡Todo lo que necesitas es un teléfono móvil o un ordenador y una conexión a Internet!

### 1. Creando tu cartera
Si aún no lo has hecho, ve a https://bitcointxoko.com y añade una nueva cartera. Puedes elegir el
nombre que quieras.

⚠️ ¡Asegúrate de guardar el enlace en tu cartera para poder acceder a él más tarde! Una buena
manera de hacer esto es guardarlo en su administrador de contraseñas, como [Bitwarden](https://bitwarden.com/). 
### 2. Activar extensiones
Hace falta la extensión **LNURLp** para que las direcciones Lightning funcionen.

Ve a *Extensiones* en la barra de herramientas y activa **LNURLp**.

### 3. Creando tu enlace de pago
Vaya a la extensión LNURLp y haz clic en *Nuevo enlace de pago*.

Elige la cartera que has creado.

Para la descripción del artículo, puedes escribir lo que quieras.

Elige un nombre de usuario de tu dirección Lightning. Tu dirección Lightning se verá como username@bitcointxoko.com. 

Desmarque *Cantidad fija* y cambie el valor mínimo a 1 y el valor máximo a 500000.

⚠️ También puedes cambiar el valor máximo a algo más alto, pero es más probable que los
pagos más grandes fallen debido a la limitada capacidad del canal de entrada del nodo Lightning
Bitcoin Txoko. Así que recomendamos mantenerlo en 500000 sats.

Ahora abre *Opciones avanzadas* y comprueba *Habilitar nostr zaps* en la parte inferior, para que
puedas usar tu Lightning Address para recibir zaps.

Las demás opciones avanzadas son opcionales, puedes configurarlas si quieres o dejarlas en
blanco.

![Al final debería verse algo así.](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/lnaddress-config.jpeg)
Al final debería verse algo así.

Cuando hayas comprobado que todo es correcto, sigue adelante y haz clic en *Crear enlace de
pago*.

### Probando
Puedes probar si tu nueva dirección Lightning funciona yendo a otra cartera, pulsando en *Enviar* y escribiendo tu dirección Lightning como destino, y luego enviándote una pequeña cantidad de
sats.

Vuelve a tu billetera Bitcoin Txoko y comprueba si has recibido tu propio pago. Es posible que
tengas que actualizar la página.

Si todo funcionó correctamente, ¡enhorabuena! 🥳

Si no es así, háznoslo saber. Siempre estamos aquí para ayudar.

### Próximos pasos

#### Nostr zaps
Puedes añadir tu dirección Bitcoin Txoko Lightning a tu perfil de nostr y usarla para recibir zaps.
En la mayoría de los clientes, esto se hace yendo a Perfil -> Editar -> Dirección Lightning y
cambiando la dirección Lightning.

#### LNDhub
Puede importar su billetera LNbits como un LNDhub en su teléfono utilizando una aplicación
como [Zeus](https://zeusln.app/) o [BlueWallet](https://bluewallet.io/), en lugar de visitar el enlace de la billetera cada vez que desee
comprobar su saldo o realizar un pago. Echa un vistazo a nuestra [guía] sobre cómo hacer esto.

#### Código QR
También puedes compartir o imprimir tu código QR LNURLp para que la gente pueda escanearlo
fácilmente con sus teléfonos. ¡Muy útil si estás introduciendo en bitcoin a tu comerciante local
favorito para que pueda recibir propinas Lightning!

Simplemente comparte el enlace a tu página compartida, o imprime el código QR como PDF
yendo a Ver enlace -> Imprimir.
