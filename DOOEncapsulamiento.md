# Encapsulamiento

El encapsulamiento se refiere a la práctica de ocultar los detalles internos de una clase, 
exponiendo solo aquello que es necesario para su uso externo. Esta idea se basa en proteger
el estado interno del objeto, impidiendo que otras partes del sistema accedan o modifiquen
sus datos directamente. En su lugar, se define una interfaz pública, a través de métodos 
específicos, que controla cómo se accede y modifica ese estado.

La importancia del encapsulamiento en el diseño orientado a objetos radica en que favorece
la modularidad, mejora la seguridad del sistema y facilita su mantenimiento. Al ocultar 
la complejidad interna y proteger los datos, se reduce el riesgo de errores provocados 
por cambios no controlados. Esto permite que los objetos sean tratados como “cajas negras”,
lo que promueve un diseño más claro, predecible y desacoplado.

Por ejemplo, una clase CuentaBancaria puede tener atributos como el saldo marcados como 
privados, y exponer métodos públicos como depositar() o retirar(). De esta forma, se evita 
modificar el saldo directamente y se garantiza que los cambios ocurran solo bajo ciertas 
condiciones definidas dentro de la clase.

Relación con **los principios SOLID**:

- **Responsabilidad Única (SRP)**: Al encapsular datos y comportamientos relacionados
en una sola clase, se facilita que cada clase tenga una única responsabilidad clara y bien definida.

- **Abierto/Cerrado (OCP)**: El encapsulamiento permite que las clases sean cerradas para modificación
- pero abiertas a extensión, ya que se puede extender su comportamiento sin alterar el código interno.

- **Segregación de Interfaces (ISP)**: Está relacionado porque ambas ideas apuntan a exponer solo lo
- necesario. Encapsular bien significa no revelar información o métodos que no deberían ser utilizados
- externamente.

Relación con **patrones de diseño**:

- **Facade**: Encapsula múltiples subsistemas complejos detrás de una única interfaz simplificada,
haciendo más fácil su uso y reduciendo la dependencia externa.

- **Builder**: Encapsula la construcción de un objeto complejo, permitiendo su creación paso a
paso sin exponer la lógica interna al cliente.

- **Proxy**: Usa encapsulamiento para controlar el acceso a otro objeto, ya sea para añadir lógica
adicional o para restringir su uso directo.

# Ejemplo en el proyecto
![Encapsulamiento aplicada en el proyecto](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/Encapsulamiento.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1sh5tADlobsEZqvXHOZyjEqnH_QohUjDI/view?usp=sharing)

El atributo teléfono del médico representa información sensible que no debe ser accesible 
directamente por otras clases del sistema. En lugar de permitir un acceso directo, el sistema gestiona 
el uso del teléfono mediante el SistemaNotificaciones, que es el único autorizado para acceder o 
utilizar ese dato a través de una interfaz o colaboración controlada.


# Ejemplo de Código
```
class Medico {
    private String nombre;
    private String telefono;

    public void notificar(String mensaje, SistemaNotificaciones sistema) {
        sistema.enviarMensaje(this.telefono, mensaje);
    }
}
```

En este ejemplo, la clase Medico no expone el atributo telefono públicamente, 
sino que controla el acceso al dato permitiendo que otra clase (SistemaNotificaciones) 
lo utilice solo mediante un método propio (notificar()).

Así, si en el futuro el método de contacto cambia (por ejemplo, a una app en lugar de SMS),
la lógica está encapsulada y solo se modifica en una parte del sistema. Esto demuestra 
encapsulamiento aplicado correctamente.
