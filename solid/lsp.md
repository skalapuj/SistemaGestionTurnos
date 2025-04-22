# Principio de Sustitución de Liskov (LSP)

Propósito y Tipo del Principio SOLID: El principio de Liskov dice que los objetos de una subclase deben poder sustituir a objetos de su superclase sin romper la aplicación. Es decir, si una clase A hereda de B, A debe poder ser usada donde sea que se espera una B.

Las subclases deben poder ser sustituidas por sus clases padre sin alterar el comportamiento del sistema. En el sistema original, las acciones de Médico y Recepcionista podían confundirse al no diferenciarse correctamente sus responsabilidades de turno.

Con LSP, garantizamos que métodos como agendarTurno() se comporten de manera coherente sin importar si lo ejecuta un médico o una agenda, al respetar contratos definidos.

## Motivación
Si un Médico implementaba su propia lógica de turnos que no respetaba la de Agenda, podía romper la coherencia del sistema. Ahora, delega en Agenda, asegurando consistencia y posibilidad de sustitución sin errores.

Un ejemplo del mundo real podría ser un auto este puede ser reemplazado por un taxi (una subclase), ambos deberían tener comportamiento similar al conducir. Pero si el taxi obliga a llevar pasajeros todo el tiempo, se rompe el principio.

## Estructura de Clases

![Diagrama LSP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/LSP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1YZ-R9Oghfyldl_mYomTvstuVfv3PY7A5/view?usp=sharing)

Tanto Médico como Agenda respetan la interfaz común ITurnoManager. Esto garantiza que cualquier clase que implemente esa interfaz puede ser utilizada de forma intercambiable.
