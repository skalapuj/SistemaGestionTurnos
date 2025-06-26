# Anexo - Aplicación de Patrón de Diseño de comportamiento - Observer
Los patrones de comportamiento se centran en cómo los objetos interactúan entre sí, y cómo se distribuyen las responsabilidades entre ellos. Buscan mejorar la comunicación entre los componentes del sistema promoviendo la flexibilidad, la desacoplación y el cumplimiento de los principios SOLID, especialmente:
- O (Abierto/Cerrado): permite añadir nuevas notificaciones o reacciones sin modificar clases existentes.
- L (Sustitución de Liskov): todos los observadores se pueden intercambiar mientras mantengan el contrato.
- D (Inversión de Dependencias): los emisores (como el sistema) dependen de interfaces abstractas para notificar.
  
<br>

**Propósito y Tipo del Patrón** 

*Patrón:* Observer

*Tipo:* Estructural

*Propósito:* Este patrón permite notificar automáticamente a uno o varios objetos (observadores) cuando ocurre un evento en el sistema. Se usa en nuestro caso para informar a los médicos o pacientes sobre acciones relevantes, como la confirmación o cancelación de un turno.

# Motivación

Cuando un turno era confirmado o cancelado, el sistema debía comunicarse directamente con los pacientes o médicos, lo que causaba un acoplamiento entre el Turno o Sistema y los canales de comunicación, como email, SMS o teléfono. Este enfoque dificultaba la incorporación de nuevos tipos de notificación sin tener que modificar el código existente, lo que incrementaba la complejidad y el riesgo de errores.

Para resolver este problema, se implementó el patrón Observer, que permite desacoplar el origen del evento del destino. Así, cuando ocurre un evento en el sistema, este notifica a las instancias observadoras, como el SistemaNotificaciones. Estas observadoras son las encargadas de tomar la acción correspondiente, como enviar un email o SMS. Con este enfoque, se pueden agregar nuevas formas de notificación sin necesidad de alterar la lógica principal del sistema, facilitando la extensión y el mantenimiento del sistema en el futuro.

**Clases nuevas**
- SObservador (interface): define el método actualizar(...).
- SistemaNotificaciones: implementa el observador y maneja las notificaciones.
- Sujeto: es la clase Sistema, que mantiene la lista de observadores.
  
# Estructura de Clases

![Boceto inicial del Diseño de clases](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/Observer__.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/19Zo5Gaqe7a0Lhcvcn8F8MlGl2Xe6xIOl/view?usp=sharing)
