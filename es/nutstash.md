## ¿Qué es Cashu?
Cashu es un protocolo de ecash de código abierto para Bitcoin que ofrece transacciones instantáneas sin comisiones con una privacidad casi perfecta. Consulta nostr:naddr1qqxnzd3e8y6rvdpe8qur2v3cqgs9n8m87l0hd9xxqwndqcmwzh4uvyxmwlw0637kuhg98pkcy8ana2grqsqqqa28f238dz para obtener más detalles.

## Nutstash
[Nutstash](https://nutstash.app/) es una increíble billetera web de Cashu desarrollada por nostr:npub1cj6ndx5akfazux7f0vjl4fyx9k0ulf682p437fe03a9ndwqjm0tqj886t6 que implementa la mayoría de los NUTs, así como el envío y recepción a través de Nostr. También puedes instalarla como una Progressive Web App (PWA) en tu teléfono.

⚠️ Tanto Nutstash como Cashu todavía están en fase beta. Existe la posibilidad de perder fondos. Lee sobre los riesgos antes de usar la aplicación. Haz pruebas con pequeñas cantidades con las que te sientas cómodo perdiendo.

## Pruébalo
Vamos a explicar cómo interactuar con una mint, recibir y enviar ecash, hacer copias de seguridad, convertir a Lightning y hacer intercambios entre mints, y al final probaremos la funcionalidad de los contactos de Nostr.

### Añadir un mint
Para interactuar con ecash, primero necesitas tener acceso a una mint, donde se crean y canjean tus tokens de ecash.

1. Ve a [Txoko Mint](https://bitcointxoko.com/cashu/mint/dMk78c5aR7uhHzcqH3Bwqp).
2. Abre la mint en Nutstash.
💡 Puedes añadir mints adicionales en Nutstash yendo a `Mint`, pegando la URL de la mint y presionando `Add Mint` ("Añadir Mint"). Algunas mints públicas se pueden encontrar en [MintIndex](https://mintindex.gandlaf.com/). Ten en cuenta que algunas mints reservarán una cierta cantidad de sats para pagar las tarifas de enrutamiento, lo que significa que no podrás retirar todos tus sats.


### Crear tokens
Puedes financiar tu billetera de ecash tanto recibiendo ecash directamente como creando nuevos tokens de ecash pagando una factura de Lightning.

1. En la pestaña `Mint`, elige la mint en la que quieres crear nuevos tokens y presiona `Mint`.
2. Elige una cantidad. Prueba con una cantidad pequeña, como 100 sats.
3. Crea la factura y págala desde una billetera de Lightning. Una vez que se haya pagado la factura, deberías tener tokens de ecash.

### Realizar transacciones con ecash
Realizar transacciones con ecash implica básicamente enviar y recibir bloques de datos. Por lo tanto, puedes probar estas funcionalidades enviando y recibiendo a ti mismo.
1. Para enviar ecash, ve a `Wallet` > `Send`.
2. Selecciona la mint desde la que quieres enviar.
3. Elige una cantidad. Opcionalmente, utiliza la selección de monedas.
4. Haz clic en enviar tokens.
5. Copia el token.
En este punto, puedes enviar el token a otra persona o canjearlo en tu propia billetera. Dado que solo estamos probando las cosas, haremos lo último.

1. Para recibir ecash, haz clic en `Wallet` > `Receive`.
2. Pega el token de cashu.
3. Haz clic en `Receive`.
💡 Puedes verificar los tokens de ecash pendientes y reclamarlos si el destinatario aún no los ha canjeado. Para hacer esto, ve a la pestaña `Wallets` y busca `Tokens`. Asegúrate de que la columna `Pending` esté marcada. Debería haber una lista de tokens pendientes, haz clic en el botón de actualización para verificar su estado. Si no han sido reclamados, puedes copiar y canjear el token.

### Intercambio de múltiples mints
Es posible que te hayas preguntado si diferentes mints pueden enviar y recibir entre sí. La respuesta es sí. Bueno, más o menos. En lugar de enviar tokens de cashu entre sí, las transacciones entre mints se realizan a través de Lightning. Para probar esto, puedes agregar otra mint si aún no lo has hecho, por ejemplo, la [mint de LNbits](https://legend.lnbits.com/cashu/mint/4gr9Xcmz3XEkUNwiBiQGoC).

💡 Ten en cuenta que algunas mints reservarán una cierta cantidad de sats para pagar las tarifas de enrutamiento, lo que significa que no podrás retirar todos tus sats. Para evitar esto, también puedes crear tu propia mint con tu billetera Bitcoin Txoko LNbits activando la extensión de Cashu. Bitcoin Txoko no requiere reservas, por lo que puedes retirar todos tus sats.

1. Ve a la pestaña `Mint` y agrega una nueva mint si aún no lo has hecho.
2. Una vez que tengas varias mints, tendrás la opción de `Inter-Mint Swap`. Abre la opción y lee la advertencia.
3. Si deseas continuar, elige una mint de la que quieres hacer el intercambio y una mint a la que quieres hacer el intercambio.
4. Elige una cantidad.
5. Confirma la cantidad (`Confirm amount`), verifica las tarifas estimadas de enrutamiento y procede con el intercambio (`Swap`).
En segundo plano, la mint que envía está pagando una factura de Lightning a la mint que recibe. Una vez que se haya liquidado la factura, el token intercambiado debería aparecer en el saldo de tu billetera en la mint que recibe.

### Convertir a lightning 
Cuando quieras convertir tus sats de cashu de nuevo a sats de Lightning, puedes convertir o "derretir" tus tokens de cashu.

1. Haz clic en `Pay` o toca el ícono de la cámara para escanear un código QR.
2. Ingresa o escanea una factura.
3. Opcionalmente, utiliza la selección de monedas.
4. Presiona `Pay`.
La mint funde los tokens de cashu y paga la factura de Lightning.

### Copias de seguridad
Hacer copias de seguridad de los tokens de Cashu es probablemente diferente al proceso que estás acostumbrado a hacer para respaldar las billeteras de Bitcoin y Lightning. Dado que los fondos están representados por tokens que son simplemente bloques de datos, solo estás respaldando estos datos cuando haces una copia de seguridad de los tokens de Cashu. Esto también significa que tus copias de seguridad cambiarán cada vez que realices una transacción y necesitarás hacer una nueva copia de seguridad después de cada transacción.

Los diferentes clientes de billeteras han implementado las copias de seguridad de manera diferente y solo funcionarán con la misma billetera que ha creado la copia de seguridad. Nutstash utiliza un archivo JSON como copia de seguridad, que también incluye tu historial de transacciones junto con los tokens que has agregado.

1. Para descargar la copia de seguridad en formato JSON, ve a `Settings` ("Configuración") > `Backup Tokens` ("Copia de seguridad de tokens"), descarga el archivo JSON y guárdalo en un lugar seguro.
2. Para restaurar la copia de seguridad, ve a `Settings` ("Configuración") > `Restore` ("Restaurar"). Lee la advertencia. Los datos actuales de tu billetera se sobrescribirán.

### Nostr
Dado que puedes enviar tokens de Cashu a través de cualquier protocolo basado en texto, Nostr es una excelente opción para Cashu. Nutstash facilita el envío de tokens de Cashu a través de Nostr.

Primero, necesitas conectar un firmante externo de Nostr a Nutstash para que Nutstash pueda cifrar y firmar mensajes directos utilizados para enviar tokens de ecash. Para hacer esto,

1. Ve a la pestaña `Settings` ("Configuración") y encuentra la sección `Nostr`.
2. Activa `Nostr`.
3. Puedes configurar (`Configure`) los retransmisores manualmente o permitir que Nutstash lea tu lista de retransmisores después de completar el siguiente paso.
4. Activa `Use external key` ("Usar clave externa"). Debes tener instalada una extensión de firmante de Nostr en tu navegador. Algunas buenas opciones son [nos2x](https://chromewebstore.google.com/detail/nos2x/kpgefcfmnafjgpblomihpgmejjdanjjp), [Alby](https://getalby.com/#alby-extension) y [Nostore](https://apps.apple.com/es/app/nostore/id1666553677) (para Safari en iOS).
5. Una vez que Nutstash detecte tu extensión de firmante, permítele leer tu lista de retransmisores y clave pública.
6. Si permites que Nutstash descifre los mensajes, buscará tokens de Cashu en tus mensajes directos. Una vez encontrados, aparecerán en la pestaña `Wallet` en la bandeja de entrada (`Inbox`). Allí podrás canjearlos en tu billetera.

Para enviar Cashu a través de Nostr,

1. Ve a `Send` ("Enviar").
2. Elige un mint.
3. Elige una cantidad. Opcionalmente, utiliza la selección de monedas.
4. Presiona `Send` ("Enviar").
5. En `Send via Nostr` ("Enviar a través de Nostr"), ingresa una dirección de Nostr en formato npub, hexadecimal o NIP-05. Alternativamente, escanea el código QR del perfil de alguien.
6. Presiona `Send via Nostr` ("Enviar a través de Nostr") y firma el mensaje tipo 4 con tu firmante externo.
7. Informa al destinatario que revise su bandeja de entrada, ¡deberían tener algunos Cashu esperándolos allí!

## Conclusión
¿Encontraste útil esta guía? ¡Intenta enviarnos algunos tokens de Cashu a través de Nostr!
