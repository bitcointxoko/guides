Nostr Wallet Connect (NWC) te permite conectar fácilmente tu billetera Lightning a una aplicación Nostr, por ejemplo, para zaps con un solo clic.

## Nostr Wallet Connect (NWC)

Nostr Wallet Connect es como un puente entre tu billetera Lightning y las aplicaciones Nostr. Esencialmente, funciona en tres sencillos pasos.

![nwc-flowchart](https://loratu.bitcointxoko.com/3ca8bd26a7b1b0be82778673ccebc9f6b40945f03e307a92d8f671f4937c2fb9.webp)

1. **Configura la conexión**: Genera una cadena de conexión con tu monedero. Esta cadena de conexión contiene una clave pública, información de relay y un secreto. Esta cadena de conexión se pega en la aplicación Nostr que deseas usar.

2. **Mensaje a través de retransmisiones**: Cuando quieres hacer un pago en la aplicación Nostr, por ejemplo, para enviar un zap, la aplicación envía una solicitud al relay cifrada con el secreto del paso anterior. Tu billetera escucha en el mismo relay y recoge la solicitud.

3. **Pago**: Después de recibir la solicitud, la billetera realiza el pago. Esto se puede hacer automáticamente o requerir aprobación.

Para obtener más información sobre NWC, puedes consultar [NIP-47](https://nips.nostr.com/47) o la [documentación](https://nwc.dev) del desarrollador.

## Configuración

Ahora que entendemos cómo funciona, configuremos algunas aplicaciones Nostr para usar nuestra billetera Lightning a través de NWC con la extensión de NWC Service Provider en LNbits.

0. **Habilita la extensión**: En la sección Extensiones de la barra lateral, habilita la extensión del NWC Service Provider. Después de habilitarla, ábrela.
1. **Selecciona una billetera**: Es una buena idea crear una billetera solo para NWC si quieres separarla de tu billetera principal. Puedes hacerlo fácilmente seleccionando "+ Añadir una nueva billetera" en la barra lateral.
2. **Añade una conexión**: Haz clic en el "+" y podrás configurar los ajustes de tu conexión, o simplemente dejarlos por defecto y añadir una descripción para que puedas identificar la conexión más tarde. Una vez que estés satisfecho con los ajustes, haz clic en "Conectar".
3. **Emparejamiento**: Ahora puedes emparejar la aplicación Nostr pegando la cadena de conexión ("Pairing URL") o escaneando el código QR con una aplicación compatible.

¡Eso es todo! Pruébalo enviando un zap.
