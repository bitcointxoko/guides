## ¿Qué es Blossom?

nostr:nevent1qqspttj39n6ld4plhn4e2mq3utxpju93u4k7w33l3ehxyf0g9lh3f0qpzpmhxue69uhkummnw3ezuamfdejsygzenanl0hmkjnrq8fksvdhpt67xzrdh0h8agltwt5znsmvzr7e74ywgmr72

[Blossom](https://github.com/hzrd149/blossom) significa _Blobs Simply Stored on Media Servers_ (Blobs Simplemente Almacenados en Servidores de Medios). _Blobs_ son fragmentos de datos binarios, como archivos pero sin nombres. En lugar de nombres, se identifican por su hash [sha256](https://es.wikipedia.org/wiki/SHA-2). La ventaja de usar hashes sha256 en lugar de nombres es que los hashes son IDs universales que se pueden calcular a partir del archivo mismo utilizando el algoritmo de hash sha256.

💡 archivo -> sha256 -> hash

Blossom es, por lo tanto, un conjunto de puntos finales HTTP que permiten a los usuarios almacenar y recuperar blobs almacenados en servidores utilizando su identidad nostr.

## ¿Por qué Blossom?

Como mencionamos hace un momento, al usar claves nostr como su identidad, Blossom permite que los datos sean "propiedad" del usuario. Esto simplifica enormemente la cuestión de "qué es spam" para el alojamiento de servidores. Por ejemplo, en nuestro Blossom solo permitimos cargas por miembros de la comunidad verificados que tengan un [NIP-05](nips.nostr.com/5) con nosotros.

Los usuarios pueden cargar en múltiples servidores de blossom, por ejemplo, uno alojado por su comunidad, uno de pago, otro público y gratuito, para establecer redundancia de sus datos. Los blobs pueden ser [espejados](https://github.com/hzrd149/blossom/blob/master/buds/04.md) entre servidores de blossom, de manera similar a cómo los relés nostr pueden transmitir eventos entre sí. Esto mejora aún más la resistencia a la censura de blossom.

A continuación se muestra una breve tabla de comparación entre torrents, Blossom y servidores CDN centralizados. (Suponiendo que hay muchos seeders para torrents y se utilizan múltiples servidores con Blossom).

|                                                                 | Torrents | Blossom | CDN Centralizado |
| --------------------------------------------------------------- | -------- | ------- | ---------------- |
| Descentralizado                                                 | ✅       | ✅      | ❌               |
| Resistencia a la censura                                        | ✅       | ✅      | ❌               |
| ¿Puedo usarlo para publicar fotos de gatitos en redes sociales? | ❌       | ✅      | ✅               |

## ¿Cómo funciona?

Blossom utiliza varios tipos de eventos nostr para comunicarse con el servidor de medios.

| kind  | descripción                     | BUD                                                                |
| ----- | ------------------------------- | ------------------------------------------------------------------ |
| 24242 | Evento de autorización          | [BUD01](https://github.com/hzrd149/blossom/blob/master/buds/01.md) |
| 10063 | Lista de Servidores de Usuarios | [BUD03](https://github.com/hzrd149/blossom/blob/master/buds/03.md) |

### kind:24242 - Autorización

Esto es esencialmente lo que ya describimos al usar claves nostr como IDs de usuario. En el evento, el usuario le dice al servidor que quiere cargar o eliminar un archivo y lo firma con sus claves nostr. El servidor realiza algunas verificaciones en este evento y luego ejecuta el comando del usuario si todo parece estar bien.

### kind:10063 - Lista de Servidores de Usuarios

Esto es utilizado por el usuario para anunciar a qué servidores de medios está subiendo. De esta manera, cuando el cliente ve esta lista, sabe dónde cargar los archivos del usuario. También puede cargar en múltiples servidores definidos en la lista para asegurar redundancia. En el lado de recuperación, si por alguna razón uno de los servidores en la lista del usuario está fuera de servicio, o el archivo ya no se puede encontrar allí, el cliente puede usar esta lista para intentar recuperar el archivo de otros servidores en la lista. Dado que los blobs se identifican por sus hashes, el mismo blob tendrá el mismo hash en cualquier servidor de medios. Todo lo que el cliente necesita hacer es cambiar la URL por la de un servidor diferente.

Ahora, además de los conceptos básicos de cómo funciona Blossom, también hay otros tipos de eventos que hacen que Blossom sea aún más interesante.

| kind  | descripción           |
| ----- | --------------------- |
| 30563 | Unidades Blossom      |
| 36363 | Listado de Servidores |
| 31963 | Reseña de Servidores  |

### kind:30563 - Unidades Blossom

Este tipo de evento facilita la organización de blobs en carpetas, como estamos acostumbrados con los discos en la nube (piensa en Google Drive, iCloud, Proton Drive, etc.). El evento contiene información sobre la estructura de carpetas y los metadatos de la unidad.

### kind:36363 y kind:31963 - Listado y Reseña

Estos tipos de eventos permiten a los usuarios descubrir y reseñar servidores de medios a través de nostr. kind:36363 es un listado de servidores que contiene la URL del servidor. kind:31963 es una reseña, donde los usuarios pueden calificar servidores.

## ¿Cómo lo uso?

### Encuentra un servidor

Primero necesitarás elegir un servidor Blossom donde cargarás tus archivos. Puedes navegar por los públicos en [blossomservers.com](https://blossomservers.com/). Algunos de ellos son de pago, otros pueden requerir que tus claves nostr estén en una lista blanca.

Luego, puedes ir a la URL de su servidor y probar a cargar un archivo pequeño, como una foto. Si estás satisfecho con el servidor (es rápido y aún no te ha fallado), puedes agregarlo a tu Lista de Servidores de Usuarios. Cubriremos brevemente cómo hacer esto en noStrudel y Amethyst (pero solo necesitas hacer esto una vez, una vez que tu lista actualizada esté publicada, los clientes pueden simplemente recuperarla de nostr).

### noStrudel

1. Encuentra Relays en la barra lateral, luego elige Servidores de Medios.
2. Agrega un servidor de medios, o mejor aún, varios.
3. Publica tu lista de servidores. ✅

### Amethyst

1. En la barra lateral, encuentra Servidores de Medios.
2. Bajo Servidores Blossom, agrega tus servidores de medios.
3. Firma y publica. ✅

Ahora, cuando vayas a hacer una publicación y adjuntar una foto, por ejemplo, se cargará en tu servidor blossom.

### Unidad Blossom

Como mencionamos anteriormente, podemos publicar eventos para organizar nuestros blobs en carpetas. Esto puede ser excelente para compartir archivos con tu equipo, o simplemente para mantener las cosas organizadas.

Para probarlo, ve a [blossom.hzrd149.com](https://blossom.hzrd149.com/) (o nuestra instancia comunitaria en [blossom.bitcointxoko.com](https://blossom.bitcointxoko.com)) e inicia sesión con tu método preferido.

Puedes crear una nueva unidad y agregar blobs desde allí.

### Bouquet

Si usas múltiples servidores para darte redundancia, Bouquet es una buena manera de obtener una visión general de todos tus archivos. Úsalo para cargar y navegar por tus medios en diferentes servidores y sincronizar blobs entre ellos.

### Cherry Tree

nostr:nevent1qvzqqqqqqypzqfngzhsvjggdlgeycm96x4emzjlwf8dyyzdfg4hefp89zpkdgz99qyghwumn8ghj7mn0wd68ytnhd9hx2tcpzfmhxue69uhkummnw3e82efwvdhk6tcqyp3065hj9zellakecetfflkgudm5n6xcc9dnetfeacnq90y3yxa5z5gk2q6

Cherry Tree te permite dividir un archivo en fragmentos y luego cargarlos en múltiples servidores blossom, y más tarde reensamblarlos en otro lugar.

## Conclusión

Blossom aún está en desarrollo, pero ya hay muchas cosas interesantes que puedes hacer con él para hacerte a ti y a tu comunidad más soberanos. ¡Pruébalo!

Si deseas mantenerte al día sobre el desarrollo de Blossom, sigue a nostr:nprofile1qyghwumn8ghj7mn0wd68ytnhd9hx2tcpzfmhxue69uhkummnw3e82efwvdhk6tcqyqnxs90qeyssm73jf3kt5dtnk997ujw6ggy6j3t0jjzw2yrv6sy22ysu5ka y dale un gran zap por su excelente trabajo.

## Referencias

- [hzrd149/blossom en GitHub](https://github.com/hzrd149/blossom)
- [Unidad Blossom](https://github.com/hzrd149/blossom-drive/blob/master/docs/drive.md)
