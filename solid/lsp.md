# Principio de Sustitución de Liskov (LSP)

El principio de Liskov dice que los objetos de una subclase deben poder sustituir a objetos de su superclase sin romper la aplicación. 
Es decir, si una clase A hereda de B, A debe poder ser usada donde sea que se espera una B.

## Motivación
El mal uso de herencia puede generar errores sutiles y difíciles de encontrar si una subclase no cumple con las expectativas del comportamiento definido en su clase padre. 

Un claro ejemplo del mundo real podría ser un auto este puede ser reemplazado por un taxi (una subclase), ambos deberían tener comportamiento similar al conducir. Pero si el taxi obliga a llevar pasajeros todo el tiempo, se rompe el principio.

## Estructura de Clases
En tu sistema, si decidieras que `Turno` tuviera subtipos como `TurnoPresencial` y `TurnoVirtual`, ambos deberían respetar las mismas reglas para `confirmar()`, `cancelar()` y `atender()` sin alterar el uso esperado.

![Diagrama LSP](./imagenes/solid/LSP.png)
[Ver diagrama en detalle]()
