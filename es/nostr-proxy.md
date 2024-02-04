Conectarse a muchos relays nostr puede agotar rápidamente la batería y el ancho de banda, especialmente si utilizas nostr en tu teléfono. Conectarse a los relays a través de un proxy nostr puede reducir el consumo de ancho de banda y de batería, además de ofrecer la ventaja adicional de ocultar tu dirección IP real a los relays. 

### ¿Cómo funciona?

Un proxy nostr se conecta a un grupo de relays. Obtiene y publica eventos en esos relays. La aplicación cliente sólo necesita abrir una conexión websocket hacia el proxy para acceder a todos los relays a los que el proxy está conectado.

![bouncer](https://github.com/Yonle/bostr/blob/master/img/how_it_works.png?raw=true)
*Imagen por cortesía de nostr:npub1x3azxuysp5vmfer4vgs4jn5tmfcx4ew8sh0qnev7gczljxsr7jwqa3g4el 2023*

Como el cliente sólo abre una conexión en lugar de muchas, ahorra ancho de banda y batería.

Como el proxy se conecta a los relays en nombre del cliente, la dirección IP del proxy se expone a los relays en lugar de la del cliente. (Aunque sigue siendo necesario confiar en el proveedor del proxy).

### Cómo utilizarlo

Un proxy nostr puede ser fácilmente autoalojado. Echa un vistazo a este [repo](https://github.com/Yonle/bostr/) por nostr:npub1x3azxuysp5vmfer4vgs4jn5tmfcx4ew8sh0qnev7gczljxsr7jwqa3g4el para instrucciones de auto-alojamiento. 

Para los que no tenemos recursos para autoalojarnos, Bitcoin Txoko alberga una [instancia comunitaria](https://bostr.bitcointxoko.com).

Como puedes ver, está conectado a algunos de los relays más populares. 

Para utilizarlo, sólo tienes que añadir

```
wss://bostr.bitcointxoko.com
```

a tu lista de relays. 

También puedes eliminar los relays redundantes ahora que ya no necesitas conexiones directas con ellos. 

Ya está. ¡Feliz zapping y nos vemos en nostr!

---
El servicio comunitario bostr.bitcointxoko.com se distribuye con el siguiente aviso de copyright.

Copyright 2023 Yonle [yonle@lecturify.net](mailto:yonle@lecturify.net)

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
    
2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
    
3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
    

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

---
La siguiente información no está actualizada. La instancia de la comunidad nproxy ya no se mantiene. Utilízala bajo tu propia responsabilidad. Muchas gracias a nostr:npub1gzuushllat7pet0ccv9yuhygvc8ldeyhrgxuwg744dn5khnpk3gs3ea5ds por su corrección.

*Un proxy nostr puede ser fácilmente autoalojado. Echa un vistazo a este [repo](https://github.com/Dolu89/nostr-proxy) por nostr:npub1txukm7xckhnxkwu450sm59vh2znwm45mewaps4awkef2tvsgh4vsf7phrl para instrucciones de auto-alojamiento.* 

*Para los que no tenemos recursos para autoalojarnos, Bitcoin Txoko alberga una [instancia comunitaria](https://nproxy.bitcointxoko.com).*

*Para utilizarlo, sólo tienes que añadir*

```
wss://nproxy.bitcointxoko.com
```

*a tu lista de relays.* 
