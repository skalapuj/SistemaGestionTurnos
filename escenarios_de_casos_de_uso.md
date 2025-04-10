# Escenarios de casos de uso 
- Caso de uso 1 - Registrar Nuevo Paciente

|                            |                                                                                   |
|----------------------------|-----------------------------------------------------------------------------------|
| **Nombre del caso de uso** | Registrar Nuevo Paciente                                                          |
| **ID Única**               | 1                                                                                 |
| **Área**                   | Sistema de gestión de turnos                                                      |
| **Actor(es)**              | Recepcionista, paciente                                                           |
| **Descripción**            | Permite registrar a un nuevo paciente en el sistema con sus datos personales.     |
| **Activar Evento**         | El recepcionista, autenticado, ingresa al sistema y selecciona “Registrar nuevo paciente”, tras ser contactado por un nuevo paciente.     |
| **Tipo de señal**          | TRUE - Externa                                                                    |

|Pasos desempeñados (ruta principal)                                   | Información para los pasos                         |
|----------------------------------------------------------------------|----------------------------------------------------|
| 1 . El recepcionista accede a la opción “Registrar paciente”.        | Menú principal                                     |
| 2 . Se ingresan los datos del paciente.                              | Nombre, DNI, email, teléfono, dirección, etc.      |
| 3 . Se abre formulario con campos obligatorios.                      |	Nombre, apellido, DNI, email, teléfono, etc.       |
| 4. Se completan los datos del paciente.	                             | Ingreso manual                                     |
| 5. El sistema valida los datos.	                                     | Validación de formato y duplicados                 |
| 6. Si hay errores, se muestran advertencias.	                        | Alertas visibles                                   |
| 7. Se corrigen los errores y se envía el formulario.                 |	Confirmación                                       |
| 8. Se verifica si ya existe un paciente con ese DNI.                 | Consulta a la base de datos                        |
| 9. Si el DNI ya existe, se muestran advertencias.	                   | Alertas visibles                                   |
| 10. El sistema guarda al paciente.		                                 | Registro en base de datos                          |
| 11. Se muestra mensaje de éxito.		                                   | Mensaje tipo “Paciente registrado con éxito”       |

|                          |                                                                              |
|--------------------------|------------------------------------------------------------------------------|
| **Precondiciones**       | El recepcionista debe estar logueado.                                        |
| **Poscondiciones**       | El paciente queda registrado correctamente.                                  |
| **Suposiciones**         | El sistema de validación funciona y la base de datos también.                |
| Reunir requerimientos    | Permite tener un registro centralizado y verificado de los pacientes.        |
|  Aspectos sobresalientes | ¿Qué ocurre si ya hay un paciente con el mismo DNI?                          |
| Prioridad                | Alta                                                                         |
| Riesgo                   | Bajo                                                                         |

- Caso de uso 2 - Asignación de Turno

|                            |                                                                            |
|----------------------------|----------------------------------------------------------------------------|
| **Nombre del caso de uso** | Asignación de Turno                                                        |
| **ID Única**               | 2                                                                          |
| **Área**                   | Sistema de gestión de turnos                                               |
| **Actor(es)**              | Recepcionista, Médico, Paciente                                            |
| **Descripción**            | Permite al recepcionista asignar un turno a un paciente con un médico.     |
| **Activar Evento**         | El recepcionista selecciona “Asignar Turno” tras consultar con el paciente.|
| **Tipo de señal**          | TRUE - Externa                                                             |

|Pasos desempeñados (ruta principal)                                        | Información para los pasos                         |
|---------------------------------------------------------------------------|----------------------------------------------------|
| 1 . El recepcionista inicia el proceso seleccionando “Asignar Turno”.     | Menú principal del sistema                         |
| 2 . Se busca al paciente por DNI o nombre.                                | Campo de búsqueda                                  |
| 3 . El sistema muestra los datos del paciente.                            | Datos personales (nombre, contacto, historial)     |
| 4 . Se selecciona el médico por nombre o especialidad.                    | Lista desplegable o buscador                       |
| 5 . El sistema muestra la disponibilidad del médico.                      | Agenda, días y horarios libres                     |
| 6 . Se elige una fecha y hora disponibles para el turno.                  | Calendario interactivo                             |
| 7 . Se ingresan el motivo de consulta y observaciones (opcional).         | Campo de texto                                     |
| 8 . El sistema verifica que no haya conflictos con la agenda del médico.  | Validación automática                              |
| 9 . Se revisan todos los datos antes de confirmar.                        | Vista previa del turno                             |
|10 . Se guarda el turno en el sistema.                                     | Registro del turno en la base de datos             |
|11 . El sistema bloquea ese horario en la agenda del médico.               | Actualización de la agenda                         |
|12 . El sistema muestra un mensaje de éxito.                               | Ventana emergente o mensaje en pantalla            |
|13 . Se envía una notificación al paciente por correo electrónico o SMS.   | Sistema externo de notificaciones                  |

|                          |                                                                                  |
|--------------------------|----------------------------------------------------------------------------------|
| **Precondiciones**       | Médico y paciente deben estar registrados. El médico debe tener disponibilidad. El recepcionista tiene que estar logueado en el sistema. |
| **Poscondiciones**       | El turno queda registrado y el paciente notificado. Agenda actualizada.          |
| **Suposiciones**         | El sistema de notificaciones funciona. El recepcionista tiene permisos.          |
| Reunir requerimientos    | Permite agendar turnos médicos de forma eficiente, asegurando disponibilidad y comunicación inmediata con el paciente.                       |
|  Aspectos sobresalientes | ¿Se permite modificar un turno confirmado? ¿Qué ocurre si falla la notificación? |
| Prioridad                | Alta                                                                             |
| Riesgo                   | Medio - Alto                                                                     |

- Caso de uso 3 - Cancelación de Turno

|                            |                                                               |
|----------------------------|---------------------------------------------------------------|
| **Nombre del caso de uso** | Cancelación de Turno                                          |
| **ID Única**               | 4                                                             |
| **Área**                   | Sistema de gestión de turnos                                  |
| **Actor(es)**              | Paciente, Recepcionista                                       |
| **Descripción**            | Permite cancelar un turno previamente asignado.               |
| **Activar Evento**         | El paciente o recepcionista elige cancelar un turno activo.   |
| **Tipo de señal**          | TRUE - Externa                                                |

| Pasos desempeñados (ruta principal)                            | Información para los pasos                                 |
|----------------------------------------------------------------|------------------------------------------------------------|
| 1. El usuario inicia sesión en el sistema.                     | Accede con sus credenciales como paciente o recepcionista  |
| 2. Accede a la opción “Mis Turnos” o “Buscar Turno”.           | Menú principal o buscador                                  |
| 3. Se selecciona el turno a cancelar.                          | Lista de turnos futuros asignados                          |
| 4. Se visualizan los detalles del turno.                       | Fecha, médico, especialidad, estado actual                 |
| 5. El usuario hace clic en “Cancelar turno”.                   | Botón visible en la vista de detalle del turno             |
| 6. El sistema solicita confirmación.                           | Mensaje: “¿Está seguro que desea cancelar el turno?”       |
| 7. El usuario confirma la cancelación.                         | Clic en “Sí, cancelar”                                     |
| 8. El sistema cambia el estado del turno a “Cancelado”.        | Actualiza base de datos                                    |
| 9. Se libera la franja horaria en la agenda del médico.        | Se marca como disponible                                   |
| 10. El paciente y el médico son notificados de la cancelación. | Email o SMS informando la cancelación                      |
| 11. Se muestra mensaje de éxito.                               | Notificación en pantalla                                   |

|                             |                                                                        |
|-----------------------------|------------------------------------------------------------------------|
| **Precondiciones**          | Turno existente, en estado “Asignado” o “Confirmado”.                  |
| **Poscondiciones**          | El turno queda cancelado y la agenda del médico actualizada.           |
| **Suposiciones**            | El sistema de notificaciones funciona correctamente.                   |
| **Reunir requerimientos**   | Facilitar reprogramación, evitar ausencias no avisadas.                |
| **Aspectos sobresalientes** | ¿Hay penalización por cancelar cerca de la fecha?                      |
| **Prioridad**               | Alta                                                                   |
| **Riesgo**                  | Bajo-Medio                                                             |

- Caso de uso 4 - Confirmación de Turno

|                            |                                                                         |
|----------------------------|-------------------------------------------------------------------------|
| **Nombre del caso de uso** | Confirmación de Turno                                                   |
| **ID Única**               | 3                                                                       |
| **Área**                   | Sistema de gestión de turnos                                            |
| **Actor(es)**              | Paciente                                                                |
| **Descripción**            | Permite que el paciente confirme la asistencia a un turno asignado.     |
| **Activar Evento**         | El paciente recibe la notificación del turno asignado.                  |
| **Tipo de señal**          | TRUE - Externa                                                          |

| Pasos desempeñados (ruta principal)                        | Información para los pasos                                          |
|------------------------------------------------------------|---------------------------------------------------------------------|
| 1. El sistema envía al paciente una notificación del turno.| Email o SMS con los detalles del turno                              |
| 2. El paciente accede al sistema mediante el enlace.       | Login rápido desde el enlace o la app                               |
| 3. En el panel, selecciona el turno pendiente de confirmar.| Sección de “Mis Turnos”                                             |
| 4. Se visualizan los detalles del turno.                   | Fecha, hora, médico, especialidad                                   |
| 5. Se presiona el botón “Confirmar asistencia”.            | Botón destacado debajo del detalle del turno                        |
| 6. El sistema solicita confirmación del paciente.          | “¿Desea confirmar su asistencia?”                                   |
| 7. El paciente acepta la confirmación.                     | Clic en “Sí, confirmar”                                             |
| 8. El sistema actualiza el estado del turno a “Confirmado”.| Base de datos y vista para médico y recepcionista actualizada       |
| 9. Se muestra mensaje de confirmación.                     | “Turno confirmado correctamente”                                    |
| 10. Se registra la hora y fecha de la confirmación.        | Para seguimiento administrativo                                     |

|                             |                                                                       |
|-----------------------------|-----------------------------------------------------------------------|
| **Precondiciones**          | El turno debe estar previamente asignado y en estado “Pendiente”.     |
| **Poscondiciones**          | El turno queda en estado “Confirmado” en el sistema.                  |
| **Suposiciones**            | El paciente accede dentro del tiempo límite para confirmar.           |
| **Reunir requerimientos**   | Permitir al personal saber si el paciente asistirá.                   |
| **Aspectos sobresalientes** | ¿Se puede cancelar luego de confirmar? ¿Hasta cuánto tiempo antes?    |
| **Prioridad**               | Media                                                                 |
| **Riesgo**                  | Bajo                                                                  |
 
- Caso de uso 5 - Consulta de Historial de Turnos

|                            |                                                                  |
|----------------------------|------------------------------------------------------------------|
| **Nombre del caso de uso** | Consulta de Historial de Turnos                                  |
| **ID Única**               | 5                                                                |
| **Área**                   | Sistema de gestión de turnos                                     |
| **Actor(es)**              | Paciente, Médico, Recepcionista                                  |
| **Descripción**            | Permite consultar el historial de turnos de un paciente.         |
| **Activar Evento**         | El usuario accede a la opción “Ver Historial de Turnos”.         |
| **Tipo de señal**          | TRUE - Externa                                                   |

| Pasos desempeñados (ruta principal)                           | Información para los pasos                                     |
|---------------------------------------------------------------|----------------------------------------------------------------|
| 1. El usuario inicia sesión en el sistema.                    | Según su rol (paciente, médico o recepcionista)                |
| 2. Se accede al módulo de historial de turnos.                | Desde el menú principal                                        |
| 3. Se realiza búsqueda del paciente.                          | Por DNI o nombre                                               |
| 4. El sistema lista todos los turnos pasados.                 | Incluye fecha, médico, especialidad, estado                    |
| 5. Se puede filtrar por fechas, médicos o estados del turno.  | Ej: últimos 6 meses, solo “realizados”, por especialidad       |
| 6. Se selecciona un turno para ver más detalles.              | Diagnóstico, notas, duración, motivo de consulta               |
| 7. El sistema muestra el detalle completo del turno.          | Información médica y administrativa                            |
| 8. Se puede imprimir o exportar el historial.                 | Botones “Descargar PDF” o “Imprimir”                           |

|                             |                                                                            |
|-----------------------------|----------------------------------------------------------------------------|
| **Precondiciones**          | Paciente debe tener historial cargado en el sistema.                       |
| **Poscondiciones**          | Visualización de los turnos, sin alteración de la información.             |
| **Suposiciones**            | Los datos están correctamente almacenados.                                 |
| **Reunir requerimientos**   | Permitir seguimiento médico, control administrativo y estadístico.         |
| **Aspectos sobresalientes** | ¿Qué rol tiene acceso a qué nivel de detalle?                              |
| **Prioridad**               | Media                                                                      |
| **Riesgo**                  | Bajo                                                                       |
