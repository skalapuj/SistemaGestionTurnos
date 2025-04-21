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
  1. El recepcionista accede al sistema con sus credenciales.
  2. Navega al módulo de “Gestión de pacientes”.
  3. Selecciona la opción "Registrar nuevo paciente".
  4. El sistema muestra un formulario para completar.
  5. El paciente dicta sus datos (nombre completo, DNI, fecha de nacimiento, teléfono, email).
  6. El recepcionista ingresa los datos en el formulario.
  7. El sistema valida que el DNI no esté duplicado y que el mail/teléfono tengan formato válido.
  8. Si hay errores, el sistema notifica y permite corregir.
  9. Si todo está correcto, el recepcionista hace clic en "Guardar".
  10. El sistema almacena al paciente en la base de datos y muestra mensaje de éxito.
  11. El sistema registra al recepcionista como responsable del alta.
  12. El paciente queda habilitado para solicitar turnos.
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
  1. El sistema envía una notificación al paciente sobre el turno pendiente.
  2. El paciente accede al enlace recibido por mail o mensaje.
  3. El sistema solicita autenticación del paciente o verificación del DNI.
  4. El sistema muestra todos los turnos pendientes del paciente.
  5. El paciente selecciona el turno que desea confirmar.
  6. Visualiza los detalles: fecha, hora, médico, motivo.
  7. El sistema muestra botón "Confirmar turno".
  8. El paciente confirma.
  9. El sistema actualiza el estado del turno a "Confirmado".
  10. El sistema notifica al médico y al recepcionista.
  11. El paciente recibe mensaje de confirmación por email o SMS.
- **Precondiciones**: El turno debe existir y estar pendiente de confirmación.
- **Postcondiciones**: El estado del turno se actualiza en el sistema.

### Cancelación de Turno
- **Actores involucrados**: Paciente, recepcionista y médico.
- **Descripción breve**: Permite cancelar un turno asignado.
- **Flujo principal de eventos**:
  1. El paciente decide cancelar un turno y contacta al centro de salud.
  2. El recepcionista o el sistema muestra los turnos activos del paciente.
  3. Se selecciona el turno a cancelar.
  4. El sistema verifica que el turno no haya pasado ni esté en curso.
  5. El sistema solicita confirmación del paciente.
  6. El paciente o el recepcionista confirma la cancelación.
  7. El sistema actualiza el estado del turno a "Cancelado".
  8. El turno se libera en la agenda del médico.
  9. El sistema envía notificaciones al médico, paciente y recepcionista.
  10. El sistema registra quién realizó la cancelación y en qué fecha/hora.
  11. El sistema muestra un mensaje indicando que el turno fue cancelado exitosamente.
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
  8. Si no hay turnos, el sistema muestra un mensaje informativo.
  9. El recepcionista puede volver al menú principal.
- **Precondiciones**: El paciente debe estar registrado.
- **Postcondiciones**: Se presenta el historial de turnos en pantalla.

## Boceto inicial del Diseño de clases
![Boceto inicial del Diseño de clases](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/Boceto%20inicial%20del%20Dise%C3%B1o%20de%20clases.png)
[Ver diagrama en detalle](https://drive.google.com/file/d/1n2TsOCuJ0kxj4p1C9c2sEuaTvZG4F68J/view?usp=sharing)
|Clase|Descripción|
|-----|-----------|
|Médico|Representa a los profesionales de la salud que atienden pacientes. Contiene su información personal (nombre, matrícula, especialidad, teléfono) y métodos para gestionar sus turnos (agendarlos, atenderlos o consultarlos).|
|Paciente|Representa a los pacientes del centro de salud. Almacena sus datos personales y el historial de turnos. Puede solicitar o cancelar turnos.|
|Recepcionista|Es el encargado de registrar pacientes, asignar turnos, consultar disponibilidad de médicos y enviar confirmaciones.|
|Turno|Representa un turno médico. Incluye la fecha y hora, estado (pendiente, confirmado, cancelado), médico asignado, paciente, motivo y observaciones.|
|Agenda|Contenedor de turnos que permite gestionar la disponibilidad de cada médico. Puede consultarse o modificarse según los cambios en los turnos.|
|Sistema Notificaciones|Gestiona el envío de notificaciones automáticas a pacientes y médicos cuando un turno es confirmado, cancelado o modificado. Justifica su existencia ya que abstrae la lógica de envío, puede manejar distintos medios (email, SMS) y registrar intentos de entrega, errores o logs de comunicación. También permite la escalabilidad si se integran más canales en el futuro.|


