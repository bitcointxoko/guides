Una BoltCard es una tarjeta que contiene una LNURLw grabada. Puedes recargarla con
sats y utilizarla como si fuera una tarjeta de crédito en comercios u otros usuarios que
aceptan esta tecnología.

![This is how it works behind the scenes. ](https://boltcard.org/img/Boltcard-flow.jpg)  
Esto es lo que pasa por detrás durante el proceso

### ¿Qué necesito?
- Una tarjeta NFC NTAG424 DNA
- A continuación dejamos algunos enlaces donde puedes encontrar estas tarjetas,
algunos ofrecen diseños personalizados
- [Bitcoin Txoko](https://shop.bitcointxoko.com/)
- [NFC cards](https://nfc.cards/en/white-cards/46-nfc-card-ntag424-dna.html)
- [NFC-tag-shop](https://www.nfc-tag-shop.de/en/NFC-Card-PVC-85-6-x-54-mm-NTAG-424-DNA-416-Byte-white/69079)
- [Lasereyes](https://lasereyes.cards/buy-now/)
- Un telefono compatible con NFC (durante nuestras pruebas en dispositivos iPhone no
funcionó de forma correcta por un problema en la obtención del UID de la tarjeta por
parte del navegador)
- Una billetera LNbits

### 1- Habilita la extension BoltCard
En tu telefono con NFC, dirigete al link de tu billetera LNbits. Dentro de `Extensiones` busca y habilita `Bolt Cards`.

### 2- Crea un nuevo registro de cartera
- Abre la extensión de `Bolt Cards` y presiona el botón `+` para crear una nueva tarjeta.
- Selecciona la cartera a la que se conectará. Esta es la cartera desde la que se gastarán
los fondos.
- Puede establecer límites para la transacción máxima y el límite diario como medida de
protección contra los comerciantes maliciosos que agotan su tarjeta.
- Ponle nombre a tu tarjeta.
- Presiona el botón NFC y luego lleva tu tarjeta NFC a tu teléfono para importar el UID de
tu tarjeta.
- Haz clic en crear tarjeta.

![Al final debería verse algo así.](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/boltcard/boltcard-config.png)


### 3- Escribe el registro NFC en la tarjeta.
- Para este paso necesitaras una aplicación para escribir el registro NFC en tu tarjeta,
nosotros hemos utilizado la aplicación oficial de BoltCard ([Android](https://play.google.com/store/apps/details?id=com.lightningnfcapp) | [iOS](https://apps.apple.com/es/app/boltcard-nfc-programmer/id6450968873))
- En LNbits, muestra las credenciales de la clave de la tarjeta, luego escanea el código
QR de la aplicación BoltCard o haz click en Crear enlace y pega la URL de
autenticación en la aplicación BoltCard
- En la aplicación BoltCard, haz click en Escribir tarjeta ahora y acerca la tarjeta NFC al
el teléfono y mantenlo así hasta que el registro se haya escrito en la tarjeta.

¡Eso es todo! Si todo salió bien, deberías tener una BoltCard en funcionamiento. Puedes
probarla tocando contra tu teléfono y abriendo el enlace LNURLw.

⚠ Llevar tu BoltCard contigo significa que llevas dinero real contigo. Si alguien accede a
tu tarjeta puede retirar todos los sats de tu cartera. Toma precauciones y mantén solo
una pequeña cantidad de sats en tu billetera BoltCard para el gastos del día a día.
Comprueba siempre que el comerciante está solicitando el precio correcto. Si es posible,
mantén tu tarjeta en una funda protegida por RFID.

### Próximos pasos  
#### BoltCard habilitada para PoS
Algunas carteras y sistemas de punto de venta (PoS) son compatibles con la BoltCard.
Aquí dejamos una lista de ellos:
- [BoltCard PoS](https://github.com/boltcard/bolt-card-pos)
- [Breez](https://breez.technology/)
- [BTCpayserver](https://btcpayserver.org/)
- [LNbits TPOS](https://github.com/lnbits/tpos) - Sí, puedes convertir tu cartera LNbits en un punto de venta (PoS)
habilitando la extensión TPOS
- [VoltPay](https://voltpay.app/)
- [lipa](https://lipa.swiss/)
- [Blink](https://www.blink.sv/)
- [Wallet of Satoshi](https://www.walletofsatoshi.com/)
- [Blixt Wallet](https://blixtwallet.github.io/)
  
#### Apoyar a BoltCard
También puedes apoyar el esfuerzo de haber creado una biblioteca de código abierto
para programar las tarjetas, puedes hacerlo en [Geyser Fund](https://geyser.fund/project/boltcard).

#### Tarjetas regalo NFC
En esta guía hemos tratado cómo crear una tarjeta de débito Lightning, pero ¿que ocurre
si quieres hacer un regalo en sats y que pueda hacer un retiro a su billetera cuando
quiera? Bueno, eso también es posible mediante tarjetas NFC y LNURLw. Explicaremos
este proceso en una futura guía.

#### ¡No solo tarjetas!
También puedes escribir registros NFC en cualquier etiqueta NFC que lo admita. Un
ejemplo de esto es el [Bolt Ring](https://bitcoin-ring.com/), que ofrece un anillo con capacidad NFC.
