# Principio de Inversión de Dependencias (DIP)

Propósito y Tipo del Principio SOLID: Este principio dice que las clases de alto nivel no deberían depender de clases de bajo nivel, sino de abstracciones. Además, las abstracciones no deben depender de detalles, los detalles deben depender de las abstracciones.

Las clases de alto nivel no deben depender de clases de bajo nivel, sino de abstracciones. En el diseño original, si Turno enviaba notificaciones (por ejemplo, al confirmar o cancelar), estaba acoplado a SistemaNotificaciones. Aplicando DIP, desacoplamos Turno de cualquier implementación concreta, haciendo que dependa de una interfaz INotificador, lo cual permite una mayor flexibilidad y reutilización.

## Motivación
Antes, si queríamos cambiar el mecanismo de notificación (por ejemplo, de mail a SMS) al confirmar o cancelar un turno, debíamos modificar la lógica interna de Turno. Ahora, con DIP, Turno solo conoce una interfaz genérica. Esto permite cambiar la forma de notificación sin afectar la lógica de negocio ni tocar el código de Turno.

Un ejemplo del mundo real es un auto este no debería depender directamente de una marca específica de motor. 
En lugar de eso, el motor debe seguir una interfaz estándar. Así, si cambiás de proveedor de motor, no tenés que rediseñar todo el auto.

## Estructura de Clases

![Diagrama DIP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/DIP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/10mhzdkJHe9eqo5AO0FDkHjT-gnnmv-w6/view?usp=sharing)

La clase Turno depende de la abstracción INotificador para enviar notificaciones cuando cambia su estado. Esto permite inyectar diferentes estrategias de notificación (email, SMS, push, etc.) sin modificar la clase.
