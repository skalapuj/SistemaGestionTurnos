# Herencia

Este principio representa la capacidad de una clase para adquirir los atributos y 
comportamientos (métodos) de otra clase. Este principio permite construir jerarquías 
entre clases, donde una clase "hija" puede extender a una clase "padre", reutilizando 
su lógica y ampliando o modificando su comportamiento. Gracias a la herencia, se 
puede evitar la duplicación de código, facilitando la creación de estructuras más organizadas,
coherentes y fáciles de mantener.

En el diseño orientado a objetos, la herencia permite establecer relaciones de tipo "es un", 
lo que ayuda a modelar de forma más natural situaciones del mundo real. Por ejemplo, si tenemos una clase Animal, 
podemos crear clases como Perro o Gato que heredan sus propiedades y métodos comunes, y agregar o sobrescribir 
comportamientos específicos. Sin embargo, es importante aplicar la herencia de forma cuidadosa, 
ya que un mal uso puede derivar en sistemas rígidos y difíciles de escalar.

Relación con los **principios SOLID**:

- **Principio de Responsabilidad Única (SRP)**:La herencia puede contribuir al SRP si se utiliza para dividir
responsabilidades entre clases base y subclases, aunque mal aplicada puede generar clases que asumen demasiadas tareas.

- **Principio de Sustitución de Liskov (LSP)**: Es crucial en el uso de la herencia. Las subclases deben
poder sustituir a la clase base sin alterar el funcionamiento esperado. Si se rompe esta regla, el diseño se vuelve inconsistente.

- ** Principio de Abierto/Cerrado (OCP)**: La herencia permite que una clase base permanezca cerrada a modificaciones
pero abierta a extensiones mediante subclases. Es uno de los usos más clásicos de este principio.

Relación con **patrones de diseño**:

- **Template Method**: Se basa directamente en la herencia. Define un esqueleto de algoritmo en una clase base
 y permite que las subclases reemplacen ciertos pasos del mismo.

- **Decorator**: Aunque no usa herencia en sentido clásico, este patrón se suele aplicar para evitar herencias
profundas. Utiliza composición para extender funcionalidades de forma flexible. Sería la alternativa directa
a la herencia.

- **Strategy**: Fomenta la composición sobre herencia para permitir la intercambiabilidad de comportamientos.
Es útil cuando se desea evitar la rigidez de jerarquías complejas.

# Ejemplo en el proyecto
![Herencia aplicada en el proyecto](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/Herencia.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/13OzMmIAZ_IDrMf5udAkcUZeAkJ-onxCQ/view?usp=sharing)

EmailAdapter y SMSAdapter heredan de la interfaz INotificador para poder intercambiarse sin cambiar el cliente que las utiliza.

# Ejemplo de Código
```
interface INotificador {
    void notificar(String mensaje, String destino);
}

class EmailAdapter implements INotificador {
    public void notificar(String mensaje, String destino) {
        // Enviar email
    }
}
```

EmailAdapter y SMSAdapter heredan de la interfaz INotificador para poder intercambiarse sin cambiar el cliente que las utiliza.
