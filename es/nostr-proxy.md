Conectarse a muchos relays nostr puede agotar rápidamente la batería y el ancho de banda, especialmente si utilizas nostr en tu teléfono. Conectarse a los relays a través de un proxy nostr puede reducir el consumo de ancho de banda y de batería, además de ofrecer la ventaja adicional de ocultar tu dirección IP real a los relays. 

### ¿Cómo funciona?

Un proxy nostr se conecta a un grupo de relays. Obtiene y publica eventos en esos relays. La aplicación cliente sólo necesita abrir una conexión websocket hacia el proxy para acceder a todos los relays a los que el proxy está conectado.

Como el cliente sólo abre una conexión en lugar de muchas, ahorra ancho de banda y batería.

Como el proxy se conecta a los relays en nombre del cliente, la dirección IP del proxy se expone a los relays en lugar de la del cliente. (Aunque sigue siendo necesario confiar en el proveedor del proxy).

### Cómo utilizarlo

Un proxy nostr puede ser fácilmente autoalojado. Echa un vistazo a este [repo](https://github.com/Dolu89/nostr-proxy) por nostr:npub1txukm7xckhnxkwu450sm59vh2znwm45mewaps4awkef2tvsgh4vsf7phrl para instrucciones de auto-alojamiento. 

Para los que no tenemos recursos para autoalojarnos, Bitcoin Txoko alberga una [instancia comunitaria](https://nproxy.bitcointxoko.com).

![nostr-proxy](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/nostr-proxy/nostr-proxy.png)

Como puedes ver, está conectado a algunos de los relays más populares. 

Para utilizarlo, sólo tienes que añadir

```
wss://nproxy.bitcointxoko.com
```

a tu lista de relays. 

También puedes eliminar los relays redundantes ahora que ya no necesitas conexiones directas con ellos. 

Ya está. ¡Feliz zapping y nos vemos en nostr!
