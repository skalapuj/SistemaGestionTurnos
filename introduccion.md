# Introducción 

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
  1. El recepcionista ingresa los datos del paciente.
  2. El sistema valida la información.
  3. Se registra al paciente en la base de datos.
- **Precondiciones**: El recepcionista debe estar autenticado.
- **Postcondiciones**: El paciente queda registrado en el sistema.

### Asignación de Turno
- **Actores involucrados**: Recepcionista, médico y paciente.
- **Descripción breve**: Permite asignar un turno a un paciente con un médico.
- **Flujo principal de eventos**:
  1. El recepcionista selecciona un paciente y un médico.
  2. El sistema muestra la disponibilidad de ese médico.
  3. Se asigna el turno disponible al paciente y se guarda en el sistema.
  4. Se envia un mail notificando al paciente.
  5. Se bloquea ese turno en el calendario de este médico.
- **Precondiciones**: El médico debe estar registrado y tener disponibilidad.
- **Postcondiciones**: El turno queda registrado y el paciente notificado.

### Confirmación de Turno
- **Actor involucrado**: Paciente.
- **Descripción breve**: Permite confirmar un turno previamente asignado.
- **Flujo principal de eventos**:
  1. El paciente recibe la notificación de turno.
  2. Confirma el turno a través del sistema.
  3. El sistema actualiza el estado del turno a "confirmado".
- **Precondiciones**: El turno debe existir y estar pendiente de confirmación.
- **Postcondiciones**: El estado del turno se actualiza en el sistema.

### Cancelación de Turno
- **Actores involucrados**: Paciente, recepcionista y médico.
- **Descripción breve**: Permite cancelar un turno asignado.
- **Flujo principal de eventos**:
  1. El paciente solicita la cancelación del turno.
  2. El recepcionista verifica y confirma la cancelación.
  3. El sistema actualiza el estado del turno a "cancelado".
  3. Se le disponibiliza ese turno al médico.
- **Precondiciones**: El turno debe existir para algún médico y ser de ese paciente.
- **Postcondiciones**: El turno queda marcado como cancelado en el sistema y el
- médico pasa a tener disponible ese turno.

### Consulta de Historial de Turnos
- **Actores involucrados**: Paciente y Recepcionista.
- **Descripción breve**: Permite consultar el historial de turnos de un paciente.
- **Flujo principal de eventos**:
  1. El Recepcionista o médico accede al sistema.
  2. Busca el paciente por DNI o nombre.
  3. El sistema muestra todos los turnos anteriores y futuros.
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
