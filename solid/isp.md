# Principio de Segregación de Interfaces (ISP)

Propósito y Tipo del Principio SOLID: Este principio indica que una clase no debería verse obligada a implementar métodos que no usa. 
En otras palabras, las interfaces grandes deben dividirse en interfaces más específicas.

Ninguna clase debe depender de métodos que no utiliza. En el sistema inicial, algunas clases como Paciente o Recepcionista podían estar forzadas a implementar o conocer métodos que no les competen directamente. Aplicando ISP, cada clase interactúa solo con las interfaces necesarias, dividiendo responsabilidades más específicas.

## Motivación
SistemaNotificaciones tenía métodos que no todos necesitaban. Al segregar interfaces, podemos tener INotificadorPaciente y INotificadorMedico, permitiendo que cada clase consuma solo lo que requiere.

Un ejemplo del mundo real aplicado: Pensemos en un sistema interno que obliga a todos los empleados a seguir el mismo procedimiento para notificar, revisar agendas, contactar pacientes, actualizar administración, enviar recordatorios. Pero no todos necesitan hacer todo eso. Un médico solo quiere consultar su agenda. Una recepcionista quiere avisar por mensaje. Y un administrador solo necesita registros.

Si el sistema estuviera dividido en partes específicas para cada rol, cada persona usaría solo lo necesario. Eso reduce confusión, errores y tiempo perdido en tareas irrelevantes. Cada uno ve y hace solo lo que le corresponde.

## Estructura de Clases

![Diagrama ISP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/ISP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1GAsA2FYICQ9wchku-feGIHMyq2pqSZHh/view?usp=sharing)

Paciente y Médico solo dependen de la interfaz que necesitan. Esto evita acoplamientos innecesarios y mejora la escalabilidad.
