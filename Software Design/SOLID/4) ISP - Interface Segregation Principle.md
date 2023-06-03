  [[SOLID]] #CleanCode 

# ENGLISH
**Interface Segregation Principle (ISP)**

The Interface Segregation Principle states that clients should not be forced to depend on interfaces they do not use. Instead of having large and general interfaces, it is better to have smaller and more specific interfaces for each client or group.

This principle promotes the idea of designing cohesive and focused interfaces that cater to the specific needs of the clients that use them. It aims to avoid the problem of "interface bloat," where a single interface becomes bloated with methods that may not be relevant or necessary for all clients.

Here's an example in TypeScript that illustrates the Interface Segregation Principle:

```ts
// Incorrect example violating ISP
interface Vehicle {
  startEngine(): void;
  stopEngine(): void;
  accelerate(speed: number): void;
  brake(): void;
  playMusic(): void;
  navigate(): void;
}

class Car implements Vehicle {
  startEngine() {
    // Implementation
  }

  stopEngine() {
    // Implementation
  }

  accelerate(speed: number) {
    // Implementation
  }

  brake() {
    // Implementation
  }

  playMusic() {
    // Implementation
  }

  navigate() {
    // Implementation
  }
}

class Bicycle implements Vehicle {
  startEngine() {
    // Not applicable to bicycles
  }

  stopEngine() {
    // Not applicable to bicycles
  }

  accelerate(speed: number) {
    // Not applicable to bicycles
  }

  brake() {
    // Implementation
  }

  playMusic() {
    // Not applicable to bicycles
  }

  navigate() {
    // Implementation
  }
}
```

In the above example, the `Vehicle` interface has multiple methods, including `startEngine()`, `accelerate()`, `playMusic()`, and `navigate()`. However, the `Bicycle` class, which also implements the `Vehicle` interface, does not require or use many of these methods, such as `startEngine()` and `accelerate()`. This violates the Interface Segregation Principle because the clients (in this case, `Bicycle`) are forced to depend on methods that are not applicable to them.

To adhere to the Interface Segregation Principle, we can split the `Vehicle` interface into more focused interfaces:

```ts
// Correct example following ISP
interface Drivable {
  startEngine(): void;
  stopEngine(): void;
  accelerate(speed: number): void;
  brake(): void;
}

interface Playable {
  playMusic(): void;
}

interface Navigable {
  navigate(): void;
}

class Car implements Drivable, Playable, Navigable {
  // Implementation for Car
}

class Bicycle implements Drivable, Navigable {
  // Implementation for Bicycle
}
```

In this revised example, the `Vehicle` interface is segregated into three smaller interfaces: `Drivable`, `Playable`, and `Navigable`. Each class (`Car` and `Bicycle`) implements only the interfaces that are relevant to them. This adheres to the Interface Segregation Principle as clients are no longer forced to depend on methods they do not use.

By following the Interface Segregation Principle, we create interfaces that are focused, cohesive, and specific to the needs of each client, promoting better code organization and avoiding unnecessary dependencies.

# SPANISH

**Principio de Segregación de Interfaces (ISP)**

El Principio de Segregación de Interfaces establece que los clientes no deben ser obligados a depender de interfaces que no utilizan. En lugar de tener interfaces grandes y generales, es mejor tener interfaces más pequeñas y específicas para cada cliente o grupo.

Este principio promueve la idea de diseñar interfaces cohesivas y enfocadas que se adapten a las necesidades específicas de los clientes que las utilizan. Su objetivo es evitar el problema de "inflado de interfaces", donde una única interfaz se llena de métodos que pueden no ser relevantes o necesarios para todos los clientes.

Aquí tienes un ejemplo en TypeScript que ilustra el Principio de Segregación de Interfaces:

```ts
// Ejemplo incorrecto que viola el ISP
interface Vehiculo {
  encenderMotor(): void;
  apagarMotor(): void;
  acelerar(velocidad: number): void;
  frenar(): void;
  reproducirMusica(): void;
  navegar(): void;
}

class Automovil implements Vehiculo {
  encenderMotor() {
    // Implementación
  }

  apagarMotor() {
    // Implementación
  }

  acelerar(velocidad: number) {
    // Implementación
  }

  frenar() {
    // Implementación
  }

  reproducirMusica() {
    // Implementación
  }

  navegar() {
    // Implementación
  }
}

class Bicicleta implements Vehiculo {
  encenderMotor() {
    // No aplicable a las bicicletas
  }

  apagarMotor() {
    // No aplicable a las bicicletas
  }

  acelerar(velocidad: number) {
    // No aplicable a las bicicletas
  }

  frenar() {
    // Implementación
  }

  reproducirMusica() {
    // No aplicable a las bicicletas
  }

  navegar() {
    // Implementación
  }
}
```

En el ejemplo anterior, la interfaz `Vehiculo` tiene múltiples métodos, incluyendo `encenderMotor()`, `acelerar()`, `reproducirMusica()` y `navegar()`. Sin embargo, la clase `Bicicleta`, que también implementa la interfaz `Vehiculo`, no requiere ni utiliza muchos de estos métodos, como `encenderMotor()` y `acelerar()`. Esto viola el Principio de Segregación de Interfaces, ya que los clientes (en este caso, `Bicicleta`) se ven obligados a depender de métodos que no son aplicables a ellos.

Para cumplir con el Principio de Segregación de Interfaces, podemos dividir la interfaz `Vehiculo` en interfaces más específicas:

```ts
// Ejemplo correcto que sigue el ISP
interface Conducible {
  encenderMotor(): void;
  apagarMotor(): void;
  acelerar(velocidad: number): void;
  frenar(): void;
}

interface Reproducible {
  reproducirMusica(): void;
}

interface Navegable {
  navegar(): void;
}

class Automovil implements Conducible, Reproducible, Navegable {
  // Implementación para Automovil
}

class Bicicleta implements Conducible, Navegable {
  // Implementación para Bicicleta
}
```

En este ejemplo revisado, la interfaz `Vehiculo` se ha segregado en tres interfaces más pequeñas: `Conducible`, `Reproducible` y `Navegable`. Cada clase (`Automovil` y `Bicicleta`) implementa solo las interfaces que son relevantes para ellos. Esto cumple con el Principio de Segregación de Interfaces, ya que los clientes ya no están obligados a depender de métodos que no utilizan.

Al seguir el Principio de Segregación de Interfaces, creamos interfaces enfocadas, cohesivas y específicas a las necesidades de cada cliente, lo cual promueve una mejor organización del código y evita dependencias innecesarias.