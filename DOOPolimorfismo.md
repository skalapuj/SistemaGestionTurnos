# Polimorfismo

El polimorfismo es un principio clave dentro del paradigma de la programación orientada a objetos. 
El término proviene del griego y significa "muchas formas", lo cual refleja su esencia: 
la capacidad de un mismo método o interfaz de comportarse de diferentes maneras según el contexto. 
En la práctica, esto significa que distintas clases pueden implementar un mismo método de forma 
distinta, permitiendo que el mismo código se ejecute de forma dinámica en función del tipo de objeto.

Este principio permite escribir código más flexible, extensible y mantenible. 
Por ejemplo, si se define una interfaz Figura con un método dibujar(), distintas clases como Círculo, 
Cuadrado o Triángulo pueden implementar ese método de forma específica. Lo interesante es que el código
que usa estas clases no necesita saber cuál es el tipo exacto de figura: simplemente llama al método 
dibujar() y confía en que el objeto actuará correctamente. Esto mejora el desacoplamiento y
facilita la reutilización del código.

El polimorfismo es especialmente útil cuando se trabaja con colecciones de objetos de tipos distintos
que comparten una misma interfaz o clase base. Permite trabajar a nivel de abstracción y extender 
funcionalidades sin modificar el código existente, lo que lo convierte en una herramienta esencial 
en el diseño de sistemas robustos y escalables.

Relación con **los principios SOLID**:

- **Sustitución de Liskov (LSP): El polimorfismo es una condición necesaria para
cumplir este principio. Las subclases deben poder reemplazar a las clases base
sin alterar el comportamiento esperado.

- **Abierto/Cerrado (OCP)**: Gracias al polimorfismo, se pueden agregar nuevas
implementaciones (nuevas clases que extiendan una interfaz) sin modificar el
código existente, respetando el OCP.

- **Segregación de Interfaces (ISP)**: El polimorfismo se apoya en interfaces bien
definidas. Al dividir interfaces en partes específicas, se permite que las clases
solo implementen lo necesario, y aún así participen en estructuras polimórficas.

Relación con **patrones de diseño**:

- **Strategy**: Utiliza el polimorfismo para permitir la intercambiabilidad de
algoritmos sin modificar el código del cliente. Cada estrategia es una implementación
diferente de una misma interfaz.

- **Factory Method**: Usa polimorfismo para crear objetos sin especificar su clase
exacta. El método devuelve un objeto que cumple con una interfaz común, y el
cliente puede usarlo sin saber su tipo específico.

- **Command**: Aplica polimorfismo para encapsular una acción como objeto. Cada
comando implementa una interfaz común, y se puede invocar dinámicamente sin conocer
los detalles de cada clase.

# Ejemplo en el proyecto
![Polimorfismo aplicada en el proyecto](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/Polimorfismo.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1pjZ2Du1KBko4W0Dypi45qEIGGOryO95w/view?usp=sharing)

El diseño aplica el principio de polimorfismo mediante el uso de la interfaz INotificador,
que define un único método: notificar(). Las clases AdapterEmail y AdapterSMS implementan
esta interfaz, cada una adaptando su propio servicio (ServicioEmail y ServicioSMS respectivamente). 
Esto permite que el sistema interactúe con cualquier tipo de notificador sin necesidad de conocer 
su implementación concreta.

La clase Sistema declara una variable de tipo INotificador. Gracias a esto,
puede asignarse cualquier objeto que implemente esta interfaz, ya sea un adaptador de SMS,
email u otro medio que se agregue en el futuro. Esto permite que el comportamiento del 
método notificar() varíe en tiempo de ejecución según el tipo de adaptador utilizado,
sin modificar el código del sistema.


# Ejemplo de Código
```
INotificador notificador = new EmailAdapter();
notificador.notificar("Turno confirmado", paciente.getTelefono());
```
Aunque notificador es de tipo INotificador, puede contener cualquier implementación (Email, SMS, etc.).
Esto permite cambiar el comportamiento sin modificar el código consumidor.
