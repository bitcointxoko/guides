¿Eres un comerciante que busca comenzar a aceptar Bitcoin en tu negocio? ¿O eres un Bitcoiner apasionado que quiere incorporar empresas locales? ¿O tal vez no te importa Bitcoin y sólo quieres utilizar un procesador de pagos rápido y económico o montar una tienda web sencilla? Si la respuesta a cualquiera de estas preguntas es afirmativa, entonces esta guía es para ti. Puedes montar una tienda en el  [BTCPay Server](https://btcpayserver.org/) alojado por Bitcoin Txoko y empezar a vender tus bienes y servicios por Bitcoin en menos de diez minutos, de forma gratuita.
## ¿Qué necesito?
Si tienes un teléfono móvil o un ordenador con acceso a Internet y una cuenta de correo electrónico, ¡estás listo!
## Crear una cuenta
Crear una cuenta BTCPay Server en Bitcoin Txoko es gratis. Navega a [btcpay.bitcointxoko.com](https://btcpay.bitcointxoko.com) para registrar una cuenta. Revisa tu bandeja de entrada para recibir un correo electrónico de bitcointxoko@gmail.com que contiene el enlace de confirmación.
## Crear tu primera tienda
Al hacer clic en el enlace de confirmación accederá a la página de creación de la tienda. Asigna un nombre a tu tienda y elige la moneda predeterminada y una fuente de precios preferida. Por ejemplo, puedes elegir EUR y Kraken, que es la fuente de precios recomendada. BTCPay Server convertirá el precio de tus bienes o servicios de EUR a Bitcoin utilizando la fuente de precios en el momento de la compra.
## Configurar una billetera
Para comenzar a aceptar pagos, primero debes vincular una billetera a tu tienda. A menos que esperes transacciones frecuentes de grandes cantidades (más de 500 EUR), te recomendamos configurar una billetera Lightning y omitir la billetera Bitcoin (en cadena) por ahora. Siempre puedes configurarla más tarde si la necesitas. 

💡 Lightning es la red de liquidación de pagos ideal para aceptar pagos de Bitcoin porque ofrece liquidación instantánea y tarifas bajas en comparación con las transacciones en cadena. 

La forma más sencilla de conectar una billetera Lightning es usar LNDhub porque no necesita correr tu propio nodo Lightning. Si aún no tienes una billetera LNDhub, no temas, Bitcoin Txoko ofrece billeteras LNDhub gratuitas y tardas menos de cinco minutos en configurarlas. Consulta nostr:naddr1qqxnzd3exuerqdfkxccnyv3cqgs9n8m87l0hd9xxqwndqcmwzh4uvyxmwlw0637kuhg98pkcy8ana2grqsqqqa28nkyu7t guía sobre cómo obtener tu propia billetera LNDhub y regresa cuando estés listo.

![connect](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/btcpay/connect.png)

Con tu billetera LNDhub lista, 
- ve a tu cuenta BTCPay, busca `Wallets` en la barra lateral y selecciona `Lightning`.
- Elige `Use custom node`. 
- Copia la URL admin de LNDhub y pégala en la configuración de conexión.
- Prueba la conexión de tu billetera.
- Si todo salió bien, deberías recibir el mensaje `Connection to the Lightning node successful, but no public address has been configured`. Puedes ignorar la parte acerca de que no se ha configurado ninguna dirección pública; esto solo se aplica si estás corriendo tu propio nodo.
- Haz clic en `Save` una vez que hayas probado con éxito la conexión de la billetera.
- Después de hacer clic en `Save`, desactiva `Enable LNURL` en la sección `LNRUL`. No olvides hacer clic en `Save` nuevamente después de realizar cambios. 
- (Opcional) En este punto, también recomendamos marcar la casilla junto a `Display Lightning payment amounts in Satoshis`, ya que es más fácil de leer. Un satoshi es la unidad divisible más pequeña de Bitcoin; hay 100 millones de satoshis en un Bitcoin. 

![config](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/btcpay/config.png)

💡 El proceso de configuración es similar si utilizas tu propio nodo Lightning. Solo asegúrase de proporcionar la cadena de conexión correcta para la implementación de tu nodo.
## Crear un Punto de Venta (Point of Sale)
Si has llegado a este paso, date una palmadita en la espalda porque la parte aburrida ya terminó. ¡Ahora puedes crear tu Punto de Venta (Point of Sale, PoS) y comenzar a aceptar tu primer pago de Bitcoin a través de BTCPay!

Para crear tu Punto de Venta, 
- Ve a `Plugins` > `Point of Sale`. 
- Dale un nombre a tu Punto de Venta y dale a `Create`. 

Cubriremos un par de cosas simples que puede hacer con tu aplicación PoS. Dado que BTCPay tiene muchas funciones, en esta guía solo cubriremos los conceptos básicos para ayudarte a comenzar.

💡 Recuerda que puedes crear múltiples Puntos de Venta dentro de BTCPay Server, cada uno para su uso.
### Keypad (Teclado)
![keypad](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/btcpay/keypad.png)

Para una demostración sencilla, primero repasaremos el PoS con estilo de teclado.

- Asigna un nombre a tu PoS y un título para mostrar. 
- Elige `Keypad` en `Choose Point of Sale Style`. 
- Presiona `Save` en la esquina superior derecha y luego `View` para comprobarlo. 

Los pagos se recibirán en la billetera LNDhub que configuraste anteriormente. Experimenta generando facturas y las opciones `Discount` y `Tip`. Si tienes un teléfono que lo admite (es decir, no un iPhone), también puedes permitir que tus clientes paguen con tarjetas NFC como BoltCard (consulta nostr:naddr1qqxnzd3e8qcr2wfn8qcrgwf4qgs9n8m87l0hd9xxqwndqcmwzh4uvyxmwlw0637kuhg98pkcy8ana2grqsqqqa28qjzxr4). Genial, ¿no?

💡 Puedes guardar el Keypad PoS como una aplicación web progresiva (PWA) en tu teléfono para acceder fácilmente. En la mayoría de los navegadores móviles, esta opción se llama "Instalar aplicación" o "Agregar a la pantalla de inicio". 
### Lista de productos con cesta (Product list with cart)
![product-list-with-cart](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/btcpay/product-list-with-cart.png)

También es posible crear una app de Punto de Venta con productos específicos, cada uno con su propio precio. Puedes utilizar esta función para configurar una caja sencilla, un sistema de autopago para el cliente o una tienda web.

- Para crear una nueva aplicación de Punto de Venta, simplemente regresa a la barra lateral y selecciona `Point of Sale` nuevamente. 
- Esta vez, en `Choose Point of Sale Style`, elige `Product list with cart`. La opción "con cesta" permite al cliente comprar varios artículos a la vez. 
- Crea tus propios productos o ve directamente a `Save` y `View` para ver los productos de muestra.
## Conclusión
En esta guía cubrimos los pasos básicos para comenzar a aceptar Bitcoin en tu negocio usando BTCPay Server. BTCPay Server es un [proyecto de código abierto](https://github.com/btcpayserver/btcpayserver) que está en constante evolución. Hay muchas más características y funcionalidades dentro de BTCPay Server que puedes explorar y usar, como la integración de Shopify, el crowdfunding, las divisiones de pagos automáticas y conversión a fiat o altcoins. También puedes personalizar tu tienda a tu gusto con temas, apariencia de pago personalizada, administración de usuarios, notificaciones por correo electrónico y mucho más. Si deseas aprovechar al máximo BTCPay Server, te recomendamos que consideres [configurar tu propia instancia de BTCPay Server](https://docs.btcpayserver.org/Deployment/). Consulta su [documentación](https://github.com/btcpayserver/btcpayserver) y [videos](https://www.youtube.com/@BTCPayServer) para obtener más información.

Si aún tienes preguntas y dudas, ¡háznoslo saber! Nos encantaría ayudar a responder cualquier pregunta relacionada. 

Bitcoin Txoko es una comunidad abierta. Todos nuestros servicios se financian mediante donaciones y tiempo voluntario. Si esta guía te ha resultado útil, considera unirte a nuestras quedadas o hacer una [donación](https://fund.bitcointxoko.com/) para ayudar a mantener nuestros servidores en funcionamiento. ¡Gracias de antemano!
