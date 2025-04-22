# Principio de Abierto/Cerrado (OCP)

El Principio Abierto/Cerrado establece que una entidad de software (como una clase, módulo o función) debe estar abierta a la extensión, pero cerrada a la modificación. Esto significa que se puede agregar nuevo comportamiento sin modificar el código existente.
Este principio ayuda a mantener el código estable y predecible cuando el sistema crece.

## Motivación

Imaginemos que tenés una aplicación para calcular precios de entradas al cine. Si cada vez que se agrega un nuevo tipo de descuento (estudiantes, jubilados, promociones), tenés que modificar la clase CalculadorDePrecios, es probable que termines rompiendo algo.
Con OCP, podés extender el comportamiento sin tocar lo que ya funciona.

Un claro ejemplo del mundo real podría ser en una cafetera automática. Inicialmente solo hace café. 
Luego querés que haga capuchino o té. Si tenés que abrirla y cambiar los circuitos cada vez que agregás una bebida, es un caos. 
Mejor es diseñarla con "módulos de bebida" intercambiables. Así podés agregar funciones sin modificar el cuerpo de la cafetera.

## Estructura de Clases

Aplicamos OCP en la clase `SistemaNotificaciones`. 
En lugar de modificarla cada vez que se necesita enviar una notificación por un nuevo medio (SMS, mail, WhatsApp), 
se puede extender con una clase hija:

![Diagrama OCP](./imagenes/solid/OCP.png)
[Ver diagrama en detalle]()
