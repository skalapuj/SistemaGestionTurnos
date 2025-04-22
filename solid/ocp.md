# Principio de Abierto/Cerrado (OCP)

Propósito y Tipo del Principio SOLID: El Principio Abierto/Cerrado establece que una entidad de software (como una clase, módulo o función) debe estar abierta a la extensión, pero cerrada a la modificación. Esto significa que se puede agregar nuevo comportamiento sin modificar el código existente. Este principio ayuda a mantener el código estable y predecible cuando el sistema crece.

En nuestro sistema, la lógica para enviar notificaciones se encontraba dispersa y no permitía nuevos canales sin alterar código existente. Al aplicar OCP, encapsulamos la lógica de envío en SistemaNotificaciones, permitiendo nuevos canales (Email, SMS, etc.) mediante extensión.

## Motivación

Antes, si queríamos añadir otro tipo de notificación, debíamos modificar el código de varias clases. Esto es riesgoso y propenso a errores. Ahora, extendiendo SistemaNotificaciones con nuevas estrategias de envío (por ejemplo, NotificadorEmail, NotificadorSMS), el sistema crece sin tocar clases existentes.

Un ejemplo del mundo real podría ser en una cafetera automática. Inicialmente solo hace café. 
Luego querés que haga capuchino o té. Si tenés que abrirla y cambiar los circuitos cada vez que agregás una bebida, es un caos. 
Mejor es diseñarla con "módulos de bebida" intercambiables. Así podés agregar funciones sin modificar el cuerpo de la cafetera.

## Estructura de Clases

![Diagrama OCP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/OCP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/11jWMnbvvoTs6F9Jyj6gsnQP2EkqqNA4N/view?usp=sharing)

Ahora podemos agregar nuevos canales de notificación sin modificar SistemaNotificaciones, simplemente creando nuevas clases que extiendan el comportamiento.

