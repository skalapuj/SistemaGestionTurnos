# Principio de Segregación de Interfaces (ISP)

Este principio indica que una clase no debería verse obligada a implementar métodos que no usa. 
En otras palabras, las interfaces grandes deben dividirse en interfaces más específicas.

## Motivación
Si una clase implementa una interfaz que contiene métodos innecesarios, su diseño se vuelve rígido y difícil de mantener.

Un ejemplo de la vida real es un control remoto tiene botones. Ahora bien, el control del aire acondicionado tiene botones diferentes al de la TV. 
Si les exigimos tener todos los mismos botones, terminaríamos con un control lleno de funciones inútiles como "encender canal" en un 
aire acondicionado.

## Estructura de Clases
En el diseño actual, si decidís crear interfaces como `ITurnoOperable`, `IMedicoRegistrable`, `IPacienteRegistrable`, cada clase podría implementar solo las operaciones que le corresponden.

![Diagrama ISP](./imagenes/solid/ISP.png)
[Ver diagrama en detalle]()
