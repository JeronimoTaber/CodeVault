# ENGLISH
Abstraction is a fundamental concept in object-oriented programming (OOP) that allows us to represent complex real-world entities in a simplified and generalized manner. It involves identifying the essential characteristics and behaviors of an object while ignoring the irrelevant details.

In OOP, we use classes as the building blocks of abstraction. A class represents an abstract concept or idea and defines the common properties and methods that objects of that class will have. It serves as a blueprint for creating objects.

By abstracting away unnecessary details, we focus on the essential aspects of an object, making it easier to understand and work with. Abstraction also enables code reusability and promotes modular and maintainable software development.

Here's an example in TypeScript:

```run-ts
abstract class Animal {
  protected name: string;

  constructor(name: string) {
    this.name = name;
  }

  abstract makeSound(): void;
}

class Dog extends Animal {
  makeSound(): void {
    console.log("Woof!");
  }
}

class Cat extends Animal {
  makeSound(): void {
    console.log("Meow!");
  }
}

const dog: Animal = new Dog("Buddy");
const cat: Animal = new Cat("Whiskers");

dog.makeSound(); // Output: Woof!
cat.makeSound(); // Output: Meow!
```

In this example, the `Animal` class represents an abstract concept of an animal. It defines a common property `name` and an abstract method `makeSound()`, which must be implemented by its derived classes (`Dog` and `Cat`). By using abstraction, we can create objects of specific animal types (`Dog` and `Cat`) and invoke the `makeSound()` method without worrying about the internal implementation details. We can treat different animal objects uniformly, emphasizing the essential behavior they exhibit.

# SPANISH

La abstracción es un concepto fundamental en la programación orientada a objetos (POO) que nos permite representar entidades complejas del mundo real de manera simplificada y generalizada. Consiste en identificar las características y comportamientos esenciales de un objeto mientras se ignoran los detalles irrelevantes.

En la POO, utilizamos clases como los bloques de construcción de la abstracción. Una clase representa un concepto o idea abstracta y define las propiedades y métodos comunes que los objetos de esa clase tendrán. Sirve como un plano para crear objetos.

Al abstraer los detalles innecesarios, nos enfocamos en los aspectos esenciales de un objeto, lo que facilita su comprensión y manipulación. La abstracción también permite la reutilización de código y promueve el desarrollo de software modular y mantenible.

Aquí tienes un ejemplo en TypeScript:

```run-ts
abstract class Animal {
  protected name: string;

  constructor(name: string) {
    this.name = name;
  }

  abstract makeSound(): void;
}

class Dog extends Animal {
  makeSound(): void {
    console.log("¡Guau!");
  }
}

class Cat extends Animal {
  makeSound(): void {
    console.log("¡Miau!");
  }
}

const dog: Animal = new Dog("Buddy");
const cat: Animal = new Cat("Whiskers");

dog.makeSound(); // Salida: ¡Guau!
cat.makeSound(); // Salida: ¡Miau!
```

En este ejemplo, la clase `Animal` representa el concepto abstracto de un animal. Define una propiedad común `name` y un método abstracto `makeSound()`, que debe ser implementado por sus clases derivadas (`Dog` y `Cat`). Mediante la abstracción, podemos crear objetos de tipos específicos de animales (`Dog` y `Cat`) e invocar el método `makeSound()` sin preocuparnos por los detalles de implementación internos. Podemos tratar los diferentes objetos animales de manera uniforme, haciendo hincapié en el comportamiento esencial que exhiben.