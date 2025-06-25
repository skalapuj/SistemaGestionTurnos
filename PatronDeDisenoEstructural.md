# Anexo - Aplicación de Patrón de Diseño estructural - Adapter

Los patrones de diseño estructurales se enfocan en cómo las clases y objetos se componen para formar estructuras más grandes y flexibles. Su objetivo es facilitar el diseño de software robusto mediante la organización óptima de las relaciones entre los componentes del sistema, respetando principios fundamentales como bajo acoplamiento y alta cohesión.

En particular, se relacionan con los principios SOLID al favorecer:
- S (Responsabilidad Única): al separar la lógica de coordinación del sistema del comportamiento específico de los objetos.
- O (Abierto/Cerrado): permiten extender comportamientos sin modificar el código existente.
- D (Inversión de Dependencias): las clases de alto nivel dependen de abstracciones, no de implementaciones concretas.
  
<br>

**Propósito y Tipo del Patrón** 

*Patrón:* Adapter

*Tipo:* Estructural

*Propósito:* El patrón Adapter permite adaptar una interfaz existente a otra esperada por el cliente. Se utiliza cuando necesitamos que clases con interfaces incompatibles trabajen juntas sin modificar su código.

En nuestro sistema, el módulo de notificaciones necesitaba integrarse al sistema de turnos, pero su interfaz no era directamente compatible con las necesidades del sistema.

# Motivación

El Sistema de Turnos necesita enviar notificaciones (email o SMS) a los usuarios (pacientes o médicos) luego de ciertas acciones: asignación, cancelación o confirmación de un turno.
Sin embargo, los servicios de mensajería (por ejemplo, ServicioSMS o ServicioEmail) no tienen la misma interfaz que el Sistema.

En lugar de modificar estos servicios (violando el principio OCP), creamos un Adapter que traduce la interfaz esperada.

**Clases implicadas**
- Sistema:	Cliente que requiere enviar notificaciones.
- Notificador (interface esperada):	Define el método notificar(mensaje, destino).
- ServicioSMS, ServicioEmail:	Servicios concretos con sus propias interfaces.
- AdapterSMS, AdapterEmail:	Adaptadores concretos que convierten la interfaz de los servicios al formato esperado.
  
# Estructura de Clases

![Boceto inicial del Diseño de clases](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/Adapter.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1E_WYLEu-et60SvIdg-0SEVojTBThMb3x/view?usp=sharing)
