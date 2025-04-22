# Principio de Inversión de Dependencias (DIP)

Este principio dice que las clases de alto nivel no deberían depender de clases de bajo nivel, sino de abstracciones. 
Además, las abstracciones no deben depender de detalles, los detalles deben depender de las abstracciones.

## Motivación
Si una clase como AsignadorDeTurno depende directamente de una clase NotificadorEmail, queda acoplada. Si el sistema cambia (por ejemplo, se reemplaza por SMS), hay que modificar el código principal. Eso es frágil.

Un ejemplo del mundo real es un auto este no debería depender directamente de una marca específica de motor. 
En lugar de eso, el motor debe seguir una interfaz estándar. Así, si cambiás de proveedor de motor, no tenés que rediseñar todo el auto.

## Estructura de Clases

Actualmente `SistemaNotificaciones` podría beneficiarse de este principio si dependiera de una interfaz `INotificador` en lugar de instanciar
directamente un tipo de notificación.

![Diagrama DIP](./imagenes/solid/DIP.png)
[Ver diagrama en detalle]()
