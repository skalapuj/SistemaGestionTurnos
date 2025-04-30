# Principio de Responsabilidad Única (SRP)

Propósito y Tipo del Principio SOLID: El Principio de Responsabilidad Única (Single Responsibility Principle) establece que una clase debe tener una, y solo una, razón para cambiar. Es decir, debe encargarse únicamente de una responsabilidad dentro del sistema. 
Este principio pertenece al grupo de principios orientados a mejorar la **cohesión** interna de una clase. Al dividir responsabilidades, el código se vuelve más comprensible, más fácil de mantener y menos propenso a errores al hacer modificaciones.

En nuestro diseño inicial, varias clases (como Recepcionista o Médico) asumían múltiples responsabilidades que no les correspondían directamente, como notificar al paciente o manejar turnos.

Este principio ayuda a distribuir responsabilidades específicas en clases más enfocadas, facilitando el mantenimiento y la evolución del sistema.

## Motivación

En el modelo original, la clase Recepcionista gestionaba tanto el registro de pacientes como la coordinación de turnos, envío de confirmaciones y notificaciones. Esto volvía complejo modificar la lógica de turnos sin afectar el resto.

Al aplicar SRP, delegamos el envío de mensajes a SistemaNotificaciones, la gestión de turnos a Agenda, y el registro de pacientes a Recepcionista, dividiendo claramente sus motivos de cambio.

Un ejemplo del mundo real aplicado es:
Supongamos que es una una clínica pequeña donde la recepcionista se encarga de todo: anotar datos de pacientes nuevos, coordinar turnos con los médicos, llamar para recordar citas, y además revisar la agenda diaria. Si un día cambian la herramienta para enviar recordatorios, la recepcionista no solo tiene que aprender algo nuevo, sino que puede equivocarse al cargar pacientes o retrasarse en asignar turnos. Lo mismo si falta la recepcionista por enfermedad y no hay una tarea claramente asignada: todo se vuelve caótico.
En cambio, si cada tarea está claramente dividida —una persona para la agenda, otra para notificaciones, otra para recibir pacientes— cada rol puede adaptarse a sus propios cambios sin impactar al resto. Así se reducen los errores y se trabaja con más claridad.

## Estructura de Clases

![Diagrama SRP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/SRP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1n7ld2vgDHjx-63J7MM3WtpFKxPPUGBbj/view?usp=sharing)

Cada clase tiene una única responsabilidad: Recepcionista registra pacientes, Agenda gestiona turnos, y SistemaNotificaciones envía notificaciones. Esto permite mantener y modificar cada módulo de forma independiente.
