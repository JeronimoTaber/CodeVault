# ENGLISH
**Encapsulation**

Encapsulation is a fundamental concept in object-oriented programming (OOP) that combines data and the methods that operate on that data into a single unit called an object. It involves bundling data and methods together and restricting direct access to the internal state of an object from outside. The internal state of an object can only be accessed and modified through the methods provided by the object.

The main goal of encapsulation is to hide the internal details of an object and provide a controlled interface for interacting with it. This helps to achieve data abstraction, where the implementation details are hidden and only the essential information is exposed to the external world. Encapsulation provides several benefits, including increased security, code maintainability, and flexibility.

In TypeScript, encapsulation can be achieved through the use of access modifiers. TypeScript provides three access modifiers: `public`, `private`, and `protected`.

- `public` is the default access modifier and allows the member (property or method) to be accessed from anywhere.
- `private` restricts the access to only within the same class. The private members cannot be accessed or modified from outside the class.
- `protected` allows access within the same class and its subclasses. Protected members are not accessible from outside the class hierarchy.

Here's an example in TypeScript that demonstrates encapsulation:

```ts
class Employee {
  private id: number;
  protected name: string;
  public department: string;

  constructor(id: number, name: string, department: string) {
    this.id = id;
    this.name = name;
    this.department = department;
  }

  public getDetails(): string {
    return `ID: ${this.id}, Name: ${this.name}, Department: ${this.department}`;
  }

  protected changeName(newName: string): void {
    this.name = newName;
  }
}

class Manager extends Employee {
  private level: string;

  constructor(id: number, name: string, department: string, level: string) {
    super(id, name, department);
    this.level = level;
  }

  public getDetails(): string {
    return `${super.getDetails()}, Level: ${this.level}`;
  }

  public promote(newLevel: string): void {
    this.changeName("John Doe"); // Accessing protected method from the base class
    this.level = newLevel;
  }
}

const employee = new Employee(1, "John Smith", "IT");
console.log(employee.department); // Accessing public property
// console.log(employee.name); // Error: 'name' is private and cannot be accessed

const manager = new Manager(2, "Jane Doe", "HR", "Senior");
console.log(manager.getDetails()); // Accessing public method
// manager.changeName("Jane Smith"); // Error: 'changeName' is protected and cannot be accessed
manager.promote("Lead");
console.log(manager.getDetails());

```

In the above example, the `Employee` class encapsulates the internal state (`id`, `name`, `department`) and provides public methods (`getDetails`) to interact with the object. The `name` property is marked as `private`, so it cannot be accessed directly from outside the class. The `changeName` method is marked as `protected`, allowing it to be accessed from within the class and its subclasses.

The `Manager` class extends the `Employee` class and adds an additional property (`level`). It overrides the `getDetails` method to include the level information. The `promote` method in the `Manager` class demonstrates accessing the `changeName` method, which is protected in the base class.

By encapsulating the internal details of the `Employee` class and providing controlled access through public methods, the code is more secure and maintainable.

# SPANISH
**Encapsulación**

La encapsulación es un concepto fundamental en la programación orientada a objetos (POO) que combina datos y los métodos que operan sobre esos datos en una sola unidad llamada objeto. Involucra agrupar datos y métodos juntos y restringir el acceso directo al estado interno de un objeto desde el exterior. El estado interno de un objeto solo puede ser accedido y modificado a través de los métodos proporcionados por el objeto.

El objetivo principal de la encapsulación es ocultar los detalles internos de un objeto y proporcionar una interfaz controlada para interactuar con él. Esto ayuda a lograr la abstracción de datos, donde los detalles de implementación están ocultos y solo se expone la información esencial al mundo exterior. La encapsulación ofrece varios beneficios, como una mayor seguridad, mantenibilidad del código y flexibilidad.

En TypeScript, la encapsulación se puede lograr mediante el uso de modificadores de acceso. TypeScript proporciona tres modificadores de acceso: `public`, `private` y `protected`.

- `public` es el modificador de acceso predeterminado y permite que el miembro (propiedad o método) sea accesible desde cualquier lugar.
- `private` restringe el acceso solo dentro de la misma clase. Los miembros privados no pueden ser accedidos o modificados desde fuera de la clase.
- `protected` permite el acceso dentro de la misma clase y sus subclases. Los miembros protegidos no son accesibles desde fuera de la jerarquía de clases.

Aquí tienes un ejemplo en TypeScript que demuestra la encapsulación:

```ts
class Empleado {
  private id: number;
  protected nombre: string;
  public departamento: string;

  constructor(id: number, nombre: string, departamento: string) {
    this.id = id;
    this.nombre = nombre;
    this.departamento = departamento;
  }

  public obtenerDetalles(): string {
    return `ID: ${this.id}, Nombre: ${this.nombre}, Departamento: ${this.departamento}`;
  }

  protected cambiarNombre(nuevoNombre: string): void {
    this.nombre = nuevoNombre;
  }
}

class Gerente extends Empleado {
  private nivel: string;

  constructor(id: number, nombre: string, departamento: string, nivel: string) {
    super(id, nombre, departamento);
    this.nivel = nivel;
  }

  public obtenerDetalles(): string {
    return `${super.obtenerDetalles()}, Nivel: ${this.nivel}`;
  }

  public promover(nuevoNivel: string): void {
    this.cambiarNombre("Juan Doe"); // Accediendo al método protegido de la clase base
    this.nivel = nuevoNivel;
  }
}

const empleado = new Empleado(1, "Juan Pérez", "TI");
console.log(empleado.departamento); // Accediendo a una propiedad pública
// console.log(empleado.nombre); // Error: 'nombre' es privado y no se puede acceder

const gerente = new Gerente(2, "María Gómez", "RRHH", "Senior");
console.log(gerente.obtenerDetalles()); // Accediendo a un método público
// gerente.cambiarNombre("María Pérez"); // Error: 'cambiarNombre' es protegido y no se puede acceder
gerente.promover("Líder");
console.log(gerente.obtenerDetalles());
```

En el ejemplo anterior, la clase `Empleado` encapsula el estado interno (`id`, `nombre`, `departamento`) y proporciona métodos públicos (`obtenerDetalles`) para interactuar con el objeto. La propiedad `nombre` se marca como `private`, por lo que no se puede acceder directamente desde fuera de la clase. El método `cambiarNombre` se marca como `protected`, lo que permite acceder a él desde dentro de la clase y sus subclases.

La clase `Gerente` extiende la clase `Empleado` y agrega una propiedad adicional (`nivel`). Sobrescribe el método `obtenerDetalles` para incluir la información del nivel. El método `promover` en la clase `Gerente` demuestra cómo acceder al método `cambiarNombre`, que es protegido en la clase base.

Al encapsular los detalles internos de la clase `Empleado` y proporcionar acceso controlado a través de métodos públicos, el código es más seguro y mantenible.