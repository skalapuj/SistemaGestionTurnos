# Principio de Abierto/Cerrado (OCP)

Propósito y Tipo del Principio SOLID: El Principio Abierto/Cerrado establece que una entidad de software (como una clase, módulo o función) debe estar abierta a la extensión, pero cerrada a la modificación. Esto significa que se puede agregar nuevo comportamiento sin modificar el código existente. Este principio ayuda a mantener el código estable y predecible cuando el sistema crece.

En nuestro sistema, la lógica para enviar notificaciones se encontraba dispersa y no permitía nuevos canales sin alterar código existente. Al aplicar OCP, encapsulamos la lógica de envío en SistemaNotificaciones, permitiendo nuevos canales (Email, SMS, etc.) mediante extensión.

## Motivación

Antes, si queríamos añadir otro tipo de notificación, debíamos modificar el código de varias clases. Esto es riesgoso y propenso a errores. Ahora, extendiendo SistemaNotificaciones con nuevas estrategias de envío (por ejemplo, NotificadorEmail, NotificadorSMS), el sistema crece sin tocar clases existentes.

Un ejemplo del mundo real aplicado es: Supongamos que la clínica empezó usando solo llamadas telefónicas y correos electrónicos para avisar sobre los turnos. Con el tiempo, los pacientes prefieren recibir mensajes por WhatsApp o incluso por redes sociales como Instagram. Si cada vez que quieren sumar un nuevo medio hay que enseñar a todo el personal cómo usarlo y cambiar todos los pasos, es un lío.

En cambio, si usan un sistema central que puede integrar nuevos canales sin que el personal cambie su forma de trabajar, simplemente se agrega un nuevo método y listo. Así se adapta el sistema sin tener que modificar lo que ya funciona.

## Estructura de Clases

![Diagrama OCP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/OCP1.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/11jWMnbvvoTs6F9Jyj6gsnQP2EkqqNA4N/view?usp=sharing)

Ahora podemos agregar nuevos canales de notificación sin modificar SistemaNotificaciones, simplemente creando nuevas clases que extiendan el comportamiento.

