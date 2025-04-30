# Principio de Inversión de Dependencias (DIP)

Propósito y Tipo del Principio SOLID: Este principio dice que las clases de alto nivel no deberían depender de clases de bajo nivel, sino de abstracciones. Además, las abstracciones no deben depender de detalles, los detalles deben depender de las abstracciones.

Las clases de alto nivel no deben depender de clases de bajo nivel, sino de abstracciones. En el diseño original, si Turno enviaba notificaciones (por ejemplo, al confirmar o cancelar), estaba acoplado a SistemaNotificaciones. Aplicando DIP, desacoplamos Turno de cualquier implementación concreta, haciendo que dependa de una interfaz INotificador, lo cual permite una mayor flexibilidad y reutilización.

## Motivación
Antes, si queríamos cambiar el mecanismo de notificación (por ejemplo, de mail a SMS) al confirmar o cancelar un turno, debíamos modificar la lógica interna de Turno. Ahora, con DIP, Turno solo conoce una interfaz genérica. Esto permite cambiar la forma de notificación sin afectar la lógica de negocio ni tocar el código de Turno.

Un ejemplo del mundo real aplicado: Supongamos que cada vez que se confirma un turno, el recepcionista debe llamar al paciente por teléfono. Si la clínica decide cambiar y usar emails o WhatsApp, el recepcionista tiene que aprender todo de nuevo, y su trabajo se ve afectado.

Pero si el recepcionista simplemente dice “enviá la notificación” y hay un sistema que se encarga, no importa cómo se envíe. Pueden cambiar de SMS a email sin afectar la rutina del recepcionista. Así, el trabajo depende de una abstracción (“avisar al paciente”) y no de una herramienta concreta.



## Estructura de Clases

![Diagrama DIP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/DIP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/10mhzdkJHe9eqo5AO0FDkHjT-gnnmv-w6/view?usp=sharing)

La clase Turno depende de la abstracción INotificador para enviar notificaciones cuando cambia su estado. Esto permite inyectar diferentes estrategias de notificación (email, SMS, push, etc.) sin modificar la clase.
