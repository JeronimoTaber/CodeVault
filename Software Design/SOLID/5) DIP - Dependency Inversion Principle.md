  [[SOLID]] #CleanCode

# ENGLISH
**Dependency Inversion Principle (DIP)**

The Dependency Inversion Principle states that high-level modules should not depend on low-level modules; both should depend on abstractions. In other words, the principle suggests that the implementation details should depend on abstractions, rather than the other way around.

The DIP promotes loose coupling between modules, which leads to more flexible and maintainable code. By depending on abstractions instead of concrete implementations, it becomes easier to change and extend the behavior of the system without affecting other parts of the codebase.

Here's an example in TypeScript that illustrates the Dependency Inversion Principle:

```ts
// High-level module
class User {
  private database: Database;

  constructor(database: Database) {
    this.database = database;
  }

  saveUser(user: UserData) {
    // Perform user validation and business logic
    this.database.save(user);
  }
}

// Low-level module
class Database {
  save(user: UserData) {
    // Implementation details to save user to the database
  }
}
```
In the above example, the `User` class represents a high-level module that is responsible for saving user data. It depends on the `Database` class, which represents a low-level module responsible for interacting with the actual database.

To adhere to the Dependency Inversion Principle, we can introduce an abstraction to decouple the high-level module from the low-level module:

```ts
// Abstraction
interface Database {
  save(user: UserData): void;
}

// High-level module
class User {
  private database: Database;

  constructor(database: Database) {
    this.database = database;
  }

  saveUser(user: UserData) {
    // Perform user validation and business logic
    this.database.save(user);
  }
}

// Low-level module
class MongoDB implements Database {
  save(user: UserData) {
    // MongoDB-specific implementation to save user to the database
  }
}

class MySQL implements Database {
  save(user: UserData) {
    // MySQL-specific implementation to save user to the database
  }
}

```

In this revised example, an abstraction `Database` is introduced as an interface. Both the `MongoDB` and `MySQL` classes implement the `Database` interface, providing their own specific implementation details to save the user data. The `User` class now depends on the `Database` abstraction instead of a specific database implementation.

By applying the Dependency Inversion Principle, we achieve a more flexible and modular design, as high-level modules are decoupled from low-level modules through abstractions. This allows for easier substitution of different implementations and promotes the reuse and testability of components.****

# SPANISH

**Principio de Inversión de Dependencias (DIP)**

El Principio de Inversión de Dependencias establece que los módulos de alto nivel no deben depender de módulos de bajo nivel; ambos deben depender de abstracciones. En otras palabras, el principio sugiere que los detalles de implementación deben depender de abstracciones, en lugar de que ocurra lo contrario.

El DIP promueve el acoplamiento débil entre los módulos, lo que conduce a un código más flexible y mantenible. Al depender de abstracciones en lugar de implementaciones concretas, se vuelve más fácil cambiar y extender el comportamiento del sistema sin afectar otras partes del código base.

Aquí tienes un ejemplo en TypeScript que ilustra el Principio de Inversión de Dependencias:

```ts
// Módulo de alto nivel
class Usuario {
  private baseDeDatos: BaseDeDatos;

  constructor(baseDeDatos: BaseDeDatos) {
    this.baseDeDatos = baseDeDatos;
  }

  guardarUsuario(usuario: DatosUsuario) {
    // Realizar validación de usuario y lógica de negocio
    this.baseDeDatos.guardar(usuario);
  }
}

// Módulo de bajo nivel
class BaseDeDatos {
  guardar(usuario: DatosUsuario) {
    // Detalles de implementación para guardar el usuario en la base de datos
  }
}
```

En el ejemplo anterior, la clase `Usuario` representa un módulo de alto nivel que es responsable de guardar los datos de usuario. Depende de la clase `BaseDeDatos`, que representa un módulo de bajo nivel responsable de interactuar con la base de datos real.

Para cumplir con el Principio de Inversión de Dependencias, podemos introducir una abstracción para desacoplar el módulo de alto nivel del módulo de bajo nivel:

```ts
// Abstracción
interface BaseDeDatos {
  guardar(usuario: DatosUsuario): void;
}

// Módulo de alto nivel
class Usuario {
  private baseDeDatos: BaseDeDatos;

  constructor(baseDeDatos: BaseDeDatos) {
    this.baseDeDatos = baseDeDatos;
  }

  guardarUsuario(usuario: DatosUsuario) {
    // Realizar validación de usuario y lógica de negocio
    this.baseDeDatos.guardar(usuario);
  }
}

// Módulo de bajo nivel
class MongoDB implements BaseDeDatos {
  guardar(usuario: DatosUsuario) {
    // Implementación específica de MongoDB para guardar el usuario en la base de datos
  }
}

class MySQL implements BaseDeDatos {
  guardar(usuario: DatosUsuario) {
    // Implementación específica de MySQL para guardar el usuario en la base de datos
  }
}
```

En este ejemplo revisado, se introduce una abstracción `BaseDeDatos` como una interfaz. Las clases `MongoDB` y `MySQL` implementan la interfaz `BaseDeDatos`, proporcionando sus propios detalles de implementación específicos para guardar los datos de usuario. La clase `Usuario` ahora depende de la abstracción `BaseDeDatos` en lugar de una implementación de base de datos específica.

Al aplicar el Principio de Inversión de Dependencias, logramos un diseño más flexible y modular, ya que los módulos de alto nivel están desacoplados de los módulos de bajo nivel a través de abstracciones. Esto permite una fácil sustitución de diferentes implementaciones y promueve la reutilización y la testabilidad de los componentes.