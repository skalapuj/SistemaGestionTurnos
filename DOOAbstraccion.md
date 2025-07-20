# Abstracción

Este principio consiste en identificar las características esenciales de un objeto 
del mundo real, ignorando los detalles irrelevantes para el contexto del sistema que
se está desarrollando. En otras palabras, la abstracción permite centrarse en el "qué hace"
un objeto, sin necesidad de conocer el "cómo lo hace". Esto facilita la comprensión, el 
mantenimiento y la reutilización del código, ya que promueve una separación clara entre 
la interfaz y la implementación.

Su importancia en el diseño orientado a objetos radica en que permite modelar sistemas 
complejos de manera más comprensible, reduciendo la complejidad y mejorando la organización
del código. Al definir clases abstractas o interfaces, los desarrolladores pueden establecer
contratos que deben cumplir las clases derivadas, lo cual ayuda a mantener la coherencia y 
facilita la extensión del sistema sin necesidad de modificar estructuras existentes.

La abstracción se relaciona de forma directa con varios principios del diseño orientado a 
objetos, especialmente dentro del marco de los principios **SOLID**:

- **Principio de Sustitución de Liskov (LSP)**: Establece que los objetos de una subclase deben
poder sustituir a los de su superclase sin afectar el correcto funcionamiento del programa.
Esto sólo es posible si las abstracciones están correctamente definidas, ya que garantizan
que las subclases respeten el comportamiento esperado.

- **Principio de Segregación de Interfaces (ISP)**: Propone que las interfaces deben ser específicas
y limitadas a lo necesario, evitando imponer a las clases la implementación de métodos que no
utilizan. Es una aplicación directa de la abstracción, ya que se enfoca en exponer únicamente
lo esencial.

Además, la abstracción también es un componente clave en muchos **patrones de diseño** ampliamente utilizados:

- **Factory Method**: Abstrae el proceso de creación de objetos, permitiendo que las subclases decidan
qué clase instanciar. Promueve la desacoplación entre la lógica del programa y los detalles de instanciación.

- **Strategy**: Permite encapsular algoritmos en clases independientes que son intercambiables.Gracias a la
abstracción, el cliente puede cambiar de estrategia sin modificar su propio código, mejorando la flexibilidad
y la reutilización.


# Ejemplo en el proyecto
![Abstracción aplicada en el proyecto](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/Abstraccion.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1kBxbsnr3r6BuCaIunxNGp-uEiJD17HcO/view?usp=sharing)

En el diagrama de clases, Turno abstrae la relación entre Paciente y Medico para centralizar 
la lógica de asignación y gestión de disponibilidad. Esto permite separar la lógica de interfaz 
(recepcionista/sistema) de la lógica de negocio.


# Ejemplo de Código
```
public class Turno {
    public enum EstadoTurno {
        DISPONIBLE,
        PENDIENTE,
        CONFIRMADO,
        CANCELADO,
        ATENDIDO
    }

    private LocalDateTime fechaHora;
    private EstadoTurno estado;
    private Paciente paciente;
    private String motivo;
    private String observaciones;
    private boolean turnoConfirmado;

    public Turno(LocalDateTime fechaHora, Paciente paciente, String motivo) {
        this.fechaHora = fechaHora;
        this.paciente = paciente;
        this.motivo = motivo;
        this.estado = EstadoTurno.DISPONIBLE;
        this.turnoConfirmado = false;
    }

    public void confirmar() {
        turnoConfirmado = true;
        estado = EstadoTurno.CONFIRMADO;
    }

    public void cancelar() {
      LocalDateTime ahora = LocalDateTime.now();
      long horasRestantes = java.time.Duration.between(ahora, fechaHora).toHours();
  
      if (horasRestantes >= 12) {
          estado = EstadoTurno.DISPONIBLE;
          turnoConfirmado = false;
          paciente = null; 
          motivo = null;
          observaciones = null;
      } else {
          estado = EstadoTurno.CANCELADO;
          turnoConfirmado = false;
      }
    }

    public void asignar(Paciente paciente, String motivo) {
      if (estado != EstadoTurno.DISPONIBLE) {
          throw new IllegalStateException("El turno no está disponible para asignar.");
      }
  
      this.paciente = paciente;
      this.motivo = motivo;
      this.estado = EstadoTurno.PENDIENTE;
  }

   public void atender(Paciente paciente, String motivo, String observaciones) {
      if (estado != EstadoTurno.CONFIRMADO) {
          throw new IllegalStateException("Solo se pueden atender turnos confirmados.");
      }
  
      this.paciente = paciente;
      this.motivo = motivo;
      this.observaciones = observaciones;
      this.estado = EstadoTurno.ATENDIDO;
  }
}
```

La clase Turno representa una abstracción del evento clínico de atención entre paciente y 
médico. No se incluyen detalles irrelevantes como cómo se crea el usuario o cómo se imprime el 
comprobante: se abstrae el turno como unidad funcional.
