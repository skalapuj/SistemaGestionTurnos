# Principio de Responsabilidad Única (SRP)

Propósito y Tipo del Principio SOLID: El Principio de Responsabilidad Única (Single Responsibility Principle) establece que una clase debe tener una, y solo una, razón para cambiar. Es decir, debe encargarse únicamente de una responsabilidad dentro del sistema. 
Este principio pertenece al grupo de principios orientados a mejorar la **cohesión** interna de una clase. Al dividir responsabilidades, el código se vuelve más comprensible, más fácil de mantener y menos propenso a errores al hacer modificaciones.

En nuestro diseño inicial, varias clases (como Recepcionista o Médico) asumían múltiples responsabilidades que no les correspondían directamente, como notificar al paciente o manejar turnos.

Este principio ayuda a distribuir responsabilidades específicas en clases más enfocadas, facilitando el mantenimiento y la evolución del sistema.

## Motivación

En el modelo original, la clase Recepcionista gestionaba tanto el registro de pacientes como la coordinación de turnos, envío de confirmaciones y notificaciones. Esto volvía complejo modificar la lógica de turnos sin afectar el resto.

Al aplicar SRP, delegamos el envío de mensajes a SistemaNotificaciones, la gestión de turnos a Agenda, y el registro de pacientes a Recepcionista, dividiendo claramente sus motivos de cambio.

Un ejemplo del mundo real aplicado es:
Supongamos que es una clínica pequeña donde la recepcionista tiene que tomar los datos de los pacientes nuevos, organizar los turnos con los médicos, llamar o mandar mensajes recordando los turnos  y, además, gestionar la agenda diaria del consultorio. Si mañana el consultorio decide usar una nueva plataforma para enviar recordatorios, la recepcionista tendría que aprender a usarla y adaptarse, lo que podría hacer que descuide otras tareas, como cargar correctamente los datos de un nuevo paciente. El trabajo se vuelve propenso a errores.
En cambio, si cada una de estas tareas se asigna a personas distintas o a herramientas especializadas, el cambio afecta solo a quien se ocupa de los recordatorios, sin complicar a los demás. Esto permite que cada persona (o sistema) se enfoque en hacer bien una sola cosa.

## Estructura de Clases

![Diagrama SRP](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/solid/SRP.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1n7ld2vgDHjx-63J7MM3WtpFKxPPUGBbj/view?usp=sharing)

Cada clase tiene una única responsabilidad: Recepcionista registra pacientes, Agenda gestiona turnos, y SistemaNotificaciones envía notificaciones. Esto permite mantener y modificar cada módulo de forma independiente.
