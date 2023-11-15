## ¿Qué es Cashu?
[Cashu](https://cashu.space/) es un protocolo de ecash de código abierto para Bitcoin que ofrece transacciones
inmediatas, sin comisiones con una completa privacidad. Visita nuestra descripción para
más detalles.

## eNuts

[eNuts](https://www.enuts.cash/) es un excelente cliente monedero Cashu para tu móvil, disponible tanto para
Android como para iOS (TestFlight). Admite múltiples mints y también enviar sobre nostr.

⚠ eNuts y Cashu todavía están en versión beta. La pérdida de fondos es posible. Lea
sobre los riesgos al instalar la aplicación. Prueba con pequeños montos que no te
importaría perder.

## Pruébalo
Explicaremos la forma de interactuar con un mint (casa de la moneda), recibir y enviar
efectivo, copias de seguridad, retirar a Lightning y el intercambio entre mints, en la parte
final probaremos la funcionalidad de los contactos de nostr

### Instalar
Visita el sitio web de [eNuts](https://www.enuts.cash/) e instala la aplicación idónea para tu sistema operativo.

### Añadir un mint
Para interactuar con el efectivo, antes debes tener acceso a una **casa de la moneda**,
donde se acuñen e intercambian sus tokens de efectivo. La casa de la moneda es el
custodio de tu Bitcoin, pero no sabe quién eres, con quién estás negociando ni cuántos
fondos tienes. Puedes usar para las pruebas.

1. Dirígete a [Txoko Mint](https://bitcointxoko.com/cashu/mint/dMk78c5aR7uhHzcqH3Bwqp) y copia la URL del mint
2. En eNuts, ve a `Opciones` > `Gestión de menta` y pulse el botón `+`. Pega la URL del mint
que has copiado del paso anterior.

💡 Puedes añadir casas adicionales adicionales. Algunos mints públicos se pueden
encontrar en [MintIndex](https://mintindex.gandlaf.com/). Ten en cuenta que algunos de estos mints reservarán una cierta
cantidad de sats para pagar las tarifas de enrutamiento, lo que significa que no puedes
retirar todos tus sats.

### Acuñación de Tokens
Una vez que hayas añadido el mint, eNuts te preguntará automáticamente si quieres
acuñar nuevos tokens de ecash de ese mint.
1. Respuesta `Sí`.
2. Crea una factura por la cantidad que desea acuñar. Prueba una pequeña cantidad, por
ejemplo, 100 sats.
3. Paga la factura con una billetera Lightning. Una vez pagada la factura ya deberías
tener tus tokens de ecash

### Transaccionar con ecash
Estas transacciones son básicamente enviar y recibir blobs de datos. Como tal, puedes
probar estas funcionalidades enviándote y recibiendo a ti mismo.
1. Para enviar efectivo, haz clic en `Enviar` > `Enviar ecash`
2. Si utilizas varios mints, selecciona el mint desde el que quieres enviar. Luego elige
`Copiar y compartir`.
3. Elige una cantidad.
4. Opcionalmente, puedes agregar una nota, haz clic en `Continuar`.
5. Confirma los detalles del pago y crea un token. En este punto, puedes usar la función
de selección de monedas para elegir qué tokens quieres gastar. Ten en cuenta que las
fichas se denominan en 1 sat, 2 sats, 4 sats, 8 sats, 16 sats, y así. Puedes pensar en ellos
como billetes de 10 euros, 20 euros, 50 euros como ejemplo.
6. Copia el token.

En este punto, puedes enviar el token a otra persona o canjearlo en tu propia cartera.
Como solo estamos probando las cosas, haremos esto mas tarde.
1. Para recibir, haz clic en `Recibir` > `Pegar y canjear efectivo`. eNuts debe leer
automáticamente su portapapeles y canjear el token.

💡 Puedes comprobar los tokens de efectivo pendientes en tu historial de transacciones
y reclamarlos si el destinatario aún no los ha canjeado. Para hacer esto, selecciona una
transacción saliente de tu historial de transacciones y luego compruebe si se ha gastado
el token. Si el token está pendiente, puede reclamar el token de vuelta tu billetera.

### Intercambio entre Mints
Es posible que te hayas preguntado si diferentes mentas pueden enviar y recibir fondos
entre sí. La respuesta es sí. Bueno, más o menos. En lugar de enviar tokens de cashu
entre sí, las transacciones entre estas casas vuelven a Lightning, ya que un mint también
es un nodo Lightning. Los tokens de Cashu en sí mismos no son fungibles en todos los
nodos. Para probar esto, puedes añadir otra menta si aún no lo has hecho, por ejemplo,
el mint cashme LNbits o el mint que presenta eNuts por defecto.

💡 Ten en cuenta que algunas mentas reservarán una cierta cantidad de sats para pagar
las tarifas de enrutamiento, lo que significa que no puedes retirar todos tus sats. Para
evitar esto, también puedes crear tu propio mint con tu cartera Bitcoin Txoko LNbits
activando la extensión Cashu.

1. Vaya a `Opciones` > `Gestión de mint` y selecciona el mint del que desea intercambiar.
Luego vaya a `Multimint swap` en `Fondos`.
2. Elige un mint para intercambiar.
3. Elige una cantidad y toca en la tarifa de estimación para estimar las posibles tarifas de
Lightning.
4. Haz clic en `Continuar`.
5. Comprueba los detalles y, opcionalmente, usa la selección de monedas, luego
presione Intercambiar ya.
Ahora, en segundo plano, la casa de la moneda de envío está pagando una factura
Lightning de la casa de la moneda de recepción. Una vez que se liquida la factura, el
token intercambiado debe aparecer en el saldo de su billetera en la casa de la moneda de
recepción.

### Retiro
Cuando quieras convertir tus cashu sats a Lightning sats, puedes hacer retiros.
1. Haga clic en `Enviar` > `Pagar factura Lightning`
2. Seleccione un mint desde el que enviar si utiliza varias.
3. En factura `LN o LNURL`, introduzca una factura, LNURL o dirección Lightning; o
simplemente escanea un código QR.
4. Elije la cantidad y la estimación de comisiones.
5. Comprueba los detalles antes de pulsar `Cash out`.
El mint canjea los tokens de efectivo y paga la factura de Lightning.

### Respaldo (Backups)
La copia de seguridad de los tokens de cashu es probablemente diferente al proceso al
que podrías estar acostumbrado para hacer copias de seguridad de las carteras de
Bitcoin y Lightning. Dado que los fondos están representados por tokens que son solo
blobs de datos, solo estás haciendo una copia de seguridad de estas piezas de datos
cuando haces una copia de seguridad de los tokens de ecash. Esto también significa que
tus copias de seguridad se invalida cada vez que realizas una transacción. Diferentes
clientes de cartera han implementado copias de seguridad de manera diferente y solo
funcionarán con la misma cartera que ha creado la copia de seguridad.

eNuts crea un token de cashu con todos sus fondos en él y a qué moneda pertenecen.

• Para crear una copia de seguridad, ve a `Opciones` > `Seguridad` > `Crear un token de
copia de seguridad`. Copia el token y guárdalo en un lugar seguro.

Alternativamente, puedes hacer una copia de seguridad de cada una de tus mints
individualmente.

• Para ello, ve a `Opciones` > `Gestión de la casa de la moneda` y seleccione la casa de la
moneda de la que desea hacer una copia de seguridad. Ve a `Copia de seguridad de
fondos`, copia el token y guárdalo en un lugar seguro.

Para restaurar, simplemente copie el token de copia de seguridad y abra la aplicación
eNuts. La aplicación debería leer su portapapeles y preguntarle si desea restaurar el
token.

### Nostr
eNuts integra Nostr para que puedas enviar efectivo a tus contactos.

Para usar esta función, ve a `Contactos` y pega tu clave pública de nostr. eNuts luego
extrae tu lista de contactos de los relays. Desafortunadamente, la función de búsqueda
aún no se ha implementado, lo que puede hacer que encontrar el contacto correcto sea
un poco engorroso si tienes muchos.

El destinatario debe recibir un mensaje directo de Nostr tipo 4 que contenga el token
ecash que puede canjear en su billetera.

## Conclusion
¿Te ha resultado útil esta guía? ¡Intenta enviarnos algunos tokens de Cashu a través de
nostr!
