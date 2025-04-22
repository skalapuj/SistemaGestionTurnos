# Principio de Segregación de Interfaces (ISP)

Propósito y Tipo del Principio SOLID: Este principio indica que una clase no debería verse obligada a implementar métodos que no usa. 
En otras palabras, las interfaces grandes deben dividirse en interfaces más específicas.

Ninguna clase debe depender de métodos que no utiliza. En el sistema inicial, algunas clases como Paciente o Recepcionista podían estar forzadas a implementar o conocer métodos que no les competen directamente. Aplicando ISP, cada clase interactúa solo con las interfaces necesarias, dividiendo responsabilidades más específicas.

## Motivación
SistemaNotificaciones tenía métodos que no todos necesitaban. Al segregar interfaces, podemos tener INotificadorPaciente y INotificadorMedico, permitiendo que cada clase consuma solo lo que requiere.

Un ejemplo de la vida real es un control remoto tiene botones. Ahora bien, el control del aire acondicionado tiene botones diferentes al de la TV. 
Si les exigimos tener todos los mismos botones, terminaríamos con un control lleno de funciones inútiles como "encender canal" en un 
aire acondicionado.

## Estructura de Clases

![Diagrama ISP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/ISP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1GAsA2FYICQ9wchku-feGIHMyq2pqSZHh/view?usp=sharing)

Paciente y Médico solo dependen de la interfaz que necesitan. Esto evita acoplamientos innecesarios y mejora la escalabilidad.
