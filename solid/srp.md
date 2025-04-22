# Principio de Responsabilidad Única (SRP)

Propósito y Tipo del Principio SOLID: El Principio de Responsabilidad Única (Single Responsibility Principle) establece que una clase debe tener una, y solo una, razón para cambiar. Es decir, debe encargarse únicamente de una responsabilidad dentro del sistema. 
Este principio pertenece al grupo de principios orientados a mejorar la **cohesión** interna de una clase. Al dividir responsabilidades, el código se vuelve más comprensible, más fácil de mantener y menos propenso a errores al hacer modificaciones.

En nuestro diseño inicial, varias clases (como Recepcionista o Médico) asumían múltiples responsabilidades que no les correspondían directamente, como notificar al paciente o manejar turnos.

Este principio ayuda a distribuir responsabilidades específicas en clases más enfocadas, facilitando el mantenimiento y la evolución del sistema.

## Motivación

En el modelo original, la clase Recepcionista gestionaba tanto el registro de pacientes como la coordinación de turnos, envío de confirmaciones y notificaciones. Esto volvía complejo modificar la lógica de turnos sin afectar el resto.

Al aplicar SRP, delegamos el envío de mensajes a SistemaNotificaciones, la gestión de turnos a Agenda, y el registro de pacientes a Recepcionista, dividiendo claramente sus motivos de cambio.

Un ejemplo del mundo real podría ser una persona que en una empresa debe atender llamadas, llevar la contabilidad, limpiar la oficina y dar soporte técnico. Si algo cambia, como una nueva ley contable, esta persona tendrá que aprender eso nuevo, 
y podría afectar también su tiempo para hacer limpieza o atender clientes. Todo se mezcla. En cambio, si cada una de esas tareas la hace una persona distinta (una recepcionista, un contador, un personal de limpieza y un técnico), cada uno puede concentrarse en
su responsabilidad sin interferencias. Si hay un cambio en el sistema contable, solo el contador necesita adaptarse.

## Estructura de Clases

![Diagrama SRP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/SRP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1n7ld2vgDHjx-63J7MM3WtpFKxPPUGBbj/view?usp=sharing)

Cada clase tiene una única responsabilidad: Recepcionista registra pacientes, Agenda gestiona turnos, y SistemaNotificaciones envía notificaciones. Esto permite mantener y modificar cada módulo de forma independiente.

Así, si cambia la forma de enviar notificaciones (por ejemplo, se pasa de SMS a WhatsApp), solo se modifica esa parte del sistema, sin afectar a quienes gestionan turnos o agendas.
