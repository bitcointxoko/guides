### ¿Qué es Cashu?
[Cashu](https://cashu.space/) es un protocolo de Ecash de código abierto para Bitcoin que ofrece transacciones
instantáneas de tarifa cero con una privacidad casi perfecta, creado por nostr:npub12rv5lskctqxxs2c8rf2zlzc7xx3qpvzs3w4etgemauy9thegr43sf485vg. 

En la siguiente tabla se compara Cashu y Bitcoin on-chain, sacada de la presentación [Nuts and Bolts](https://nuts-and-bolts.gandlaf.com/) de nostr:npub1cj6ndx5akfazux7f0vjl4fyx9k0ulf682p437fe03a9ndwqjm0tqj886t6 en la Conferencia Bitcoin Bangkok 2023.

| Cashu | Bitcoin (on-chain) |
|--|--|
| No Ledger | Distributed Ledger |
| Bearer Token | UTXO |
| Blinded Transactions | Public Transactions|
| Centralised | Decentralised |
| Trusted | Trustless |
| Ephemeral Transactions| Eternal Transactions |

Como podemos ver, Cashu sacrifica la confianza y la descentralización en favor de la
privacidad. Esto tiene mucho sentido cuando se trata de soluciones de custodia, ya que
el usuario ya utiliza un servicio centralizado en el que tiene que confiar. Las soluciones de
custodia tradicionales tienen una privacidad horrible, ya que ese custodio conoce los
fondos que posee un usuario y con quién está transaccionando. Permitiendo ataques y
censura a los usuarios. Los registros de los datos también se pueden convertir en un
honeypot.

Por el contrario, los mints de Cashu pueden actuar como custodios que no saben
quienes son sus usuarios, cuántos fondos tienen ni con quién interactúa. Esta casa de la
moneda (mint) solo tiene como único registro una lista de secretos gastados que no son
reutilizables y sin forma de asociarlos con los usuarios.

![](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/onchain-ark-lightning-ecash.jpeg)

Algunos casos de uso serían vales ya centralizados y custodiados por un tercero; uso
para pagar por un recurso como APIs, relays de nostr o mixnets; sistemas
integrados que reemplazan el modelo cuenta y saldo; y servicios de intercambio/mezcla
para desligar depósitos y retiros. 
### Historia
Ecash fue concebido por primera vez por David Chaum en 1982 como un protocolo de
transmisión de valor electrónico utilizando firmas ciegas. Cashu es una implementación
de Ecash que utiliza la [variante](https://cypherpunks.venona.com/date/1996/03/msg01848.html) de David Wagner de Chaumian blinding de 1996 creada
por nostr:npub12rv5lskctqxxs2c8rf2zlzc7xx3qpvzs3w4etgemauy9thegr43sf485vg.
### Terminología
Para ayudar a comprender como funciona Cashu, vamos a tratar primero alguna
terminología esencial. 
#### Mint
Los Mint en Cashu es el custodio de los fondos de los usuarios. Su labor es acuñar y
quemar tokens y prevenir el doble gasto.

El mint de Cashu corre un nodo Lightning, por lo que puede enviar y recibir pagos
Lightning. Incluyendo el intercambio con otros Mints. Sin embargo, todavía puedes
realizar transacciones con tokens ecash, incluso si el nodo Lightning está oﬄine. A
diferencia de Lightning, el destinatario tampoco necesita estar en linea para recibirlo.
Esta casa de la moneda o mint no sabe quién es el usuario, cuantos fondos tiene ni con
quienes está realizando transacciones.

Sin embargo, desde que el mint es el custodio de los fondos de los usuarios, deberías
elegir un mint en el que confíes y del que conozcas al operador.

Utiliza montos pequeños o canjea los tokens de inmediato. 
#### Token
Un token cashu es esencialmente un conjunto de datos firmado por el mint. El usuario
guarda esos tokens en su billetera. Dado que esos tokens ecash son solo texto, pueden
ser enviadas por cualquier protocolo basado en texto. Como nostr, mail, sms, etc.

Cashu utiliza un sistema que se basa en monedas con denominaciones fijas.

La denominación de los billetes fíat son una analogía. Por ejemplo, en el Euro los billetes
son de 5, 10, 20, 50, 100…

En Cashu, los tokens están denominados en potencias de 2. Por ejemplo, 1, 2, 4, 8, 16,
32, 64, 128 sats, así sucesivamente.

El objetivo de usar denominaciones es aumentar el anonimato establecido entre los
usuarios y hacer que sea aún más difícil para los mints asociar las transacciones con las
identidades de los usuarios. 

### ¿Cómo funciona? Explicado como si tuviera 5 años

![mint-request](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/mint-request.jpeg)

Alice quiere acuñar nuevos tokens Cashu. Así que se dirige al mint de Bob, y dice: “¡Oye!
Quiero acuñar nuevos tokens de Cashu".

![mint-request-response](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/mint-request-response.jpeg)

Bob responde diciendo: "Vale, págame y envíame un secreto ciego". El secreto ciego
significa que Alice conoce el secreto, pero Bob no puede verlo.

![blinding](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/blinding.jpeg)

Alice genera un secreto y luego lo ciega para que Bob no sepa cuál es el secreto.

![mint](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/mint.jpeg)

Ella le paga a Bob y le envía su comprobante de pago y su secreto ciego.

![signing](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/signing.jpeg)

![mint-response](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/mint-response.jpeg)

Cuando Bob está conforme con el pago, firma el secreto ciego de Alice y le devuelve el
secreto ciego firmado. Una vez firmado por Bob, en el futuro puede tener la seguridad de
que el token es válido.

![unblinding](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/unblinding.jpeg)

Alice quiere pagarle a Carol. Ella le envía a Carol su secreto junto con una llave para
descifrar el secreto ciego firmado.

Carol quiere canjear su token. Así que ella va a la casa de la moneda, Bob, y le muestra el
secreto y la clave que Alice le dio.

![verification](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/verification.jpeg)

Bob nunca ha visto el secreto antes y tampoco sabe que fue Alice quien lo generó, ya
que Alice lo ofuscó antes de enviárselo. Pero puede verificar que lo firmó antes, por eso
puede tratarlo como un gasto valido del token. Ahora firma un nuevo token para Carol, o
le devuelve los sats y añade el secreto a una lista de secretos gastados. Si alguien trata
de reclamar con el mismo secreto otra vez, Bob lo rechazará porque es un gasto doble.

#### ¿Cómo sabe el mint (Bob) qué cantidad de sats darle a Carol?
Anteriormente hemos mencionado que los tokens Cashu están denominados en
potencias de 2 (1, 2, 4, 8, 16, 32...), algo así como billetes fíat.

Bob, la casa de la moneda, tiene una clave privada distinta que usa para firmar cada
denominación. Por ejemplo, tiene una clave privada única para tokens con denominación
de 1 sat, otra para los de denominación 2 sats, otra para los de 8 y así sucesivamente…

De esta manera, cuando Carol viene a Bob para canjear tokens, Bob sabe con qué clave
privada ha firmado el token antes y, por lo tanto, a qué denominación pertenecen los
tokens.

#### ¿Qué pasa con el cambio?
En Cashu no hay cambio. Solo tienes que decirle al mint que destruya los tokens
antiguos y que acuñe nuevos tokens del mismo importe exacto.

Para ver esto, digamos que Alice tiene dos tokens que suman 10 sats. Un token de 8 sats
y otro de 2 sats.

Ella quiere enviar 9 sats a Carol. Así que va al mint y le dice a Bob que divida su token de
2 sats en dos tokens de 1 sat. Ahora puede enviar 9 sats a Carol en forma de una ficha
de 8 sats y una ficha de 1 sat, y guardar la otra ficha de 1 sat para Ella.

#### Lightning para la interconexion
¿Qué pasa cuando Alice quiere pagarle a David, que no confía en el mint de Bob pero
conoce a Erin y usa el mint de Erin?

Alice cambia sus tokens en el mint de Bob, dando instrucciones a Bob para que derrita
los tokens o los convierta de nuevo en sats Lightning. El mint de Bob luego envía una
transacción Lightning al mint de Erin. El mint de Erin luego acuña nuevos tokens con
David utilizando los sats Lightning que acaba de recibir del mint de Bob.

![lightning-mints](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/cashu/lightning.jpeg)

### ¿Qué es lo siguiente para Cashu?
#### Ecash programable
Podemos establecer condiciones de gasto al ecash, siendo el mint quien las aplica. Esto
puede desbloquear potentes contratos inteligentes sin llegar a la cadena base ni a la red
Lightning, que pueden permitir pagos públicos, pagos oﬄine y de alta frecuencia. 
#### Plan de prueba de pasivos para los mints
El llamado Proof of Liabilities de Calle (PoL) en Cashu, se trata de una especie de sistema
de auditoria que le dificulta a los custodios atacar a los usuarios mediante la introducción
del concepto de epochs (épocas). En este esquema, el mint custodio rota de forma
regular el conjunto de claves privadas que utilizan en cada epoch y publica listas
auditables de tokens acuñados y quemados en el último epoch. Combinado con un
esquema de prueba de reservas en el que las reservas se mantienen en un multifirma on-
chain, un custodio deshonesto no puede reducir sus pasivos sin arriesgarse a ser
descubierta por los usuarios. Para profundizar sobre este aspecto consulta el [artículo completo](https://gist.github.com/callebtc/ed5228d1d8cbaade0104db5d1cf63939). 
### Prueba Cashu
Puedes probar Cashu a través de nuestra guías para [Nutstash] y [eNuts]. Únicamente
necesitas una cartera Lightning y un teléfono u ordenador.
### Referencias
- [Cashu.space](https://docs.cashu.space/)
- [Learn about Cashu](https://docs.cashu.space/resources/learn)
- [Cashu en los medios](https://docs.cashu.space/resources/media)
- [Entrevista](https://www.youtube.com/watch?v=zdtRT7phXBo) con calle de nostr:npub1yn3hc8jmpj963h0zw49ullrrkkefn7qxf78mj29u7v2mn3yktuasx3mzt0
### Ver también
- [Video](https://youtube.com/watch?v=riTRD0BdMDI&si=0H2IzuXQiOkPR9UX) de nostr:npub1rxysxnjkhrmqd3ey73dp9n5y5yvyzcs64acc9g0k2epcpwwyya4spvhnp8
- [Soporte Cashu](https://docs.cashu.space/contribute)
- [NUTs](https://github.com/cashubtc/nuts) - - Notación, uso y terminología, las especificaciones del protocolo para Cashu
- [X-Cashu](https://github.com/cashubtc/xcashu) - HTTP 402: Se requiere pago con Cashu
- [Proxnut](https://github.com/gandlafbtc/proxnut) - Proteger o monetizar los recursos web con el uso de tokens
- [Prueba de Pasivos para Cashu](https://gist.github.com/callebtc/ed5228d1d8cbaade0104db5d1cf63939)
- [Fedimint](https://fedimint.org/) - implementación de ecash federado
