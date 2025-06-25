# Anexo - Aplicación de Patrón de Diseño creacional - Singleton

Los patrones creacionales se centran en el proceso de creación de objetos. Su objetivo es controlar cómo y cuándo se instancian los objetos, asegurando una creación flexible, eficiente y controlada, evitando instanciaciones innecesarias o inconsistentes.

Conectan especialmente con principios SOLID como:
- S (Responsabilidad Única): al delegar la responsabilidad de instanciación en una sola clase.
- O (Abierto/Cerrado): se puede modificar la forma de creación sin alterar a los clientes.
- D (Inversión de Dependencias): abstraen el mecanismo de creación para evitar dependencias rígidas.

<br>

**Propósito y Tipo del Patrón** 

*Patrón:* Singleton

*Tipo:* Creacional

*Propósito:* Asegurar que una clase tenga una única instancia global a lo largo del sistema y proporcionar un punto de acceso centralizado a ella. En este proyecto, se aplica a la clase Repositorio, encargada de gestionar toda la información persistida del sistema.

# Motivación

El problema detectado es que el sistema accede de manera frecuente al Repositorio para guardar o consultar información de médicos, agendas, pacientes y turnos. Si se crean múltiples instancias, se pierde integridad y sincronización por lo que se requiere una única fuente de verdad accesible desde cualquier punto del sistema.

**Solución con Singleton:**
La clase Repositorio debe implementarse como un Singleton, garantizando que solo exista una instancia a lo largo del ciclo de vida del sistema, todos los objetos interactúen con la misma instancia y se centralice el acceso a los datos.

**Clases implicadas**

Repositorio: clase Singleton con constructor privado y método getInstancia().

# Estructura de Clases
![Boceto inicial del Diseño de clases](https://github.com/skalapuj/SistemaGestionTurnos/raw/main/imagenes/Singleton.png)

[Ver diagrama en detalle](https://drive.google.com/file/d/1aH-4up_MuFWdYhCWatG87mv3RxKszIga/view?usp=sharing)
