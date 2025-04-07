# Anexo - Introducción al Diseño Orientado a Objetos

## Paradigma Orientado a Objetos
La Programación Orientada a Objetos (POO) es un paradigma de programación basado
en la creación y manipulación de objetos, los cuales representan entidades del 
mundo real y contienen datos (atributos) y funcionalidades (métodos). 
Este enfoque es importante porque permite crear sistemas más organizados, facilita 
la reutilización, el mantenimiento y favorece la escalabilidad del software.

## Fundamentos de POO
- **Encapsulamiento**: <br> 
Protege los datos dentro de los objetos y restringe 
el acceso desde el exterior. Proteger los datos de acceso no autorizado.
Por ejemplo, un objeto `Paciente` que tiene atributos privados como `nombre` 
y `documento` estos atributos están **encapsulados** puesto que estan ocultos y solo
se accede indirectamente a ellos através de los métodos `obtenerNombre()` y
`obtenerDocumento()`.
  - clase `Paciente`:
    - Métodos:   `obtenerNombre()`, `obtenerDocumento()`.
    - Atributos:
      - Privados: `nombre`, `documento`.
      - Público: `colorDePelo`.
        
- **Herencia**:<br>
Facilita la creación de nuevas clases basadas en otras existentes, 
evitando la duplicación de código. Por ejemplo, una `Médico` y una `Asistente` pueden
heredar de una clase común `Persona`.
  - clase `Persona`:
    - Métodos:   `obtenerNombre()`, `obtenerDocumento()`.
    - Atributos: `nombre`, `documento`, `fechaDeNacimiento`.
  - Subclase `Médico`:
    - Método:   `atender()`.
    - Atributos: `matrícula`, `especialidad`.
  - Subclase `Recepcionista`:
    - Método:   `agendarTurno()`.
    - Atributo: `funciónAdministrativa` .

- **Polimorfismo**: <br>
Permite que un método tenga diferentes comportamientos según el objeto que lo
llama. Por ejemplo, el método `enviarNotificacion()`puede enviar un correo a un
 `Paciente` y un mensaje de texto a un `Medico`.
  - clase `Notificador`:
    - Método:   `enviarNotificacion()`.
  - Subclase `Médico`:
    - Método:   `enviarNotificacion()`.
  - Subclase `Paciente`:
    - Método:   `enviarNotificacion()`.

- **Abstracción**: <br>
Permite representar entidades del mundo real destacando solo
los detalles importantes. Por ejemplo, un `Turno` puede tener un método
 `confirmar()` sin mostrar cómo se implementa la notificación. Solo se muestra
 la interfaz pública del método, lo que es un ejemplo de abstracción, ya que
se ocultan los detalles complejos de la implementación.
- clase `Turno`:
    - Métodos:   `confirmar()`, `cancelar()`.
    - Atributos: `fechaHora`, `estado`, `médico`, `paciente`, `Motivo`.
        
## Requisitos iniciales del sistema
:one: Registrar pacientes y profesionales de la salud.<br>
:two: Asignar turnos según la disponibilidad de los profesionales.<br>
:three: Llevar un historial de turnos realizados por cada paciente.<br>
:four: Enviar notificaciones cuando un turno es confirmado, cancelado o modificado.<br>
:five: Proteger la información de contacto de los pacientes y médicos.<br>

## Casos de Uso

### Registro de Paciente
- **Actores involucrados**: Recepcionista y paciente.
- **Descripción breve**: Permite registrar un nuevo paciente en el sistema.
- **Flujo principal de eventos**:
  1. El recepcionista accede al sistema mediante su usuario y contraseña.
  2. Selecciona la opción "Registrar nuevo paciente".
  3. El sistema muestra un formulario con campos obligatorios: nombre, apellido, DNI, fecha de nacimiento, teléfono, email.
  4. El recepcionista completa todos los campos con los datos proporcionados por el paciente.
  5. El sistema valida los datos ingresados (formato correcto de email, teléfono, y que el DNI no esté duplicado).
  6. Si hay errores, muestra mensajes de advertencia y permite corregirlos.
  7. Una vez validados los datos, el recepcionista confirma el registro.
  8. El sistema guarda al paciente en la base de datos.
  9. El sistema muestra un mensaje de éxito indicando que el paciente fue registrado correctamente.
- **Precondiciones**: El recepcionista debe estar autenticado.
- **Postcondiciones**: El paciente queda registrado en el sistema.

### Asignación de Turno
- **Actores involucrados**: Recepcionista, médico y paciente.
- **Descripción breve**: Permite asignar un turno a un paciente con un médico.
- **Flujo principal de eventos**:
  1. Selecciona la opción "Asignar turno".
  2. Busca al paciente por DNI o nombre.
  3. El sistema muestra los datos del paciente.
  4. Selecciona al médico por especialidad o nombre.
  5. El sistema muestra los días y horarios disponibles del médico.
  6. El recepcionista elige una fecha y hora disponible.
  7. Opcionalmente se ingresa el motivo de la consulta y observaciones.
  8. El sistema verifica que no haya conflictos con otros turnos.
  9. Si está todo correcto, se guarda el turno y se lo asigna al paciente.
  10. El sistema muestra un mensaje de éxito indicando que el turno fue asignado correctamente.
  11. El sistema envía una notificación al paciente por correo electrónico o mensaje de texto.
  12. El turno queda bloqueado en el calendario del médico.
- **Precondiciones**: El médico debe estar registrado y tener disponibilidad.
- **Postcondiciones**: El turno queda registrado y el paciente notificado.

### Confirmación de Turno
- **Actor involucrado**: Paciente.
- **Descripción breve**: Permite confirmar un turno previamente asignado.
- **Flujo principal de eventos**:
  1. El paciente recibe una notificación de turno pendiente por correo electrónico o mensaje.
  2. Ingresa al sistema o accede al enlace recibido para confirmar.
  3. Visualiza los detalles del turno (fecha, hora, médico, motivo).
  4. Hace clic en "Confirmar turno".
  5. El sistema actualiza el estado del turno a "Confirmado".
  6. El paciente recibe una confirmación por el mismo medio.
- **Precondiciones**: El turno debe existir y estar pendiente de confirmación.
- **Postcondiciones**: El estado del turno se actualiza en el sistema.

### Cancelación de Turno
- **Actores involucrados**: Paciente, recepcionista y médico.
- **Descripción breve**: Permite cancelar un turno asignado.
- **Flujo principal de eventos**:
  1. El paciente decide cancelar un turno y contacta al centro de salud.
  2. Si se comunica telefónicamente, el recepcionista busca el turno en el sistema.
  3. Se verifica que el turno pertenece al paciente, que está vigente y que aún puede ser cancelado.
  4. Se solicita una confirmación final de cancelación.
  5. El sistema actualiza el estado del turno a "Cancelado".
  6. El turno cancelado se libera en la agenda del médico.
  7. El sistema envía una notificación al paciente.
  8. El sistema muestra un mensaje de éxito indicando que el turno fue cancelado correctamente.
- **Precondiciones**: El turno debe existir para algún médico y ser de ese paciente.
- **Postcondiciones**: El turno queda marcado como cancelado en el sistema y el
- médico pasa a tener disponible ese turno.

### Consulta de Historial de Turnos
- **Actores involucrados**: Paciente y Recepcionista.
- **Descripción breve**: Permite consultar el historial de turnos de un paciente.
- **Flujo principal de eventos**:
  1. El recepcionista inicia sesión en el sistema.
  2. Selecciona la opción "Historial de turnos".
  3. Ingresa el DNI o nombre del paciente.
  4. El sistema busca y muestra los datos del paciente.
  5. Se listan todos los turnos anteriores y los próximos, con su estado (confirmado, cancelado, pendiente), fecha, hora, profesional y motivo.
  6. El recepcionista puede aplicar filtros por fecha, estado o profesional.
  7. El sistema permite exportar o imprimir el historial si es necesario.
- **Precondiciones**: El paciente debe estar registrado.
- **Postcondiciones**: Se presenta el historial de turnos en pantalla.

## Boceto inicial del Diseño de clases
![Boceto inicial del Diseño de clases](https://github.com/user-attachments/assets/d9c232c2-1af8-4271-b686-596d03e0a2ff)

|Clase|Descripción|
|-----|-----------|
|Médico|Representa a los médicos dentro del sistema. Contiene su información personal y métodos para gestionar turnos.|
|Paciente|Representa a los pacientes, con datos personales y su historial de turnos.|
|Recepcionista|Se encarga de gestionar pacientes y turnos.|
|Turno|Representa un turno médico, con su fecha, estado, médico y paciente asignado.|
|Agenda|Es un contenedor de turnos para un médico que le permite a la recepcionista el gestinar los turnos.|
|Sistema Notificaciones|Se encarga de enviar notificaciones a médicos y a clientes|

[Boceto de Diseño de Clases](diagramas/BocetoinicialdelDiseñodeclases.uxf)
