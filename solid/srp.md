# Principio de Responsabilidad Única (SRP)

El Principio de Responsabilidad Única (Single Responsibility Principle) establece que una clase debe tener una, y solo una, razón para cambiar. Es decir, debe encargarse únicamente de una responsabilidad dentro del sistema. 
Este principio pertenece al grupo de principios orientados a mejorar la **cohesión** interna de una clase. Al dividir responsabilidades, el código se vuelve más comprensible, más fácil de mantener y menos propenso a errores al hacer modificaciones.

## Motivación

Cuando una clase realiza múltiples tareas, los cambios que afectan a una de sus funciones pueden tener consecuencias inesperadas en las demás. Esto vuelve el sistema difícil de mantener, poco confiable y muy propenso a errores. 

Un claro ejemplo del mundo real podría ser una persona que en una empresa debe atender llamadas, llevar la contabilidad, limpiar la oficina y dar soporte técnico. Si algo cambia, como una nueva ley contable, esta persona tendrá que aprender eso nuevo, 
y podría afectar también su tiempo para hacer limpieza o atender clientes. Todo se mezcla. En cambio, si cada una de esas tareas la hace una persona distinta (una recepcionista, un contador, un personal de limpieza y un técnico), cada uno puede concentrarse en
su responsabilidad sin interferencias. Si hay un cambio en el sistema contable, solo el contador necesita adaptarse.

Ese es el espíritu del SRP: cada parte del sistema debe tener **una sola razón para cambiar**.

## Estructura de Clases

En nuestro sistema, este principio se aplica separando bien las tareas:

- El **Recepcionista** se encarga únicamente de asignar turnos.
- La **Agenda** solo se ocupa de guardar y mostrar los turnos.
- El **Sistema de Notificaciones** solamente se encarga de enviar mensajes.

Así, si cambia la forma de enviar notificaciones (por ejemplo, se pasa de SMS a WhatsApp), solo se modifica esa parte del sistema, sin afectar a quienes gestionan turnos o agendas.

![Diagrama SRP](./imagenes/solid/srp.png)
[Ver diagrama en detalle]()
