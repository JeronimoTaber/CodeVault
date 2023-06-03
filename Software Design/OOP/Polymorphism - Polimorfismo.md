# ENGLISH
**Polymorphism**

Polymorphism is a key concept in object-oriented programming that allows an object to take on multiple forms or behaviors. It refers to the ability of an object to be treated as an instance of its base class or as an instance of any of its derived classes. This allows different objects of related classes to respond differently to the same method call or property.

Polymorphism is based on two main features of object-oriented programming: inheritance and method overriding. Inheritance allows a class to inherit properties and methods from its parent class, while method overriding allows a subclass to provide its own implementation of a method inherited from the base class.

Polymorphism provides a way to write code that can work with objects of different classes, as long as they adhere to a common interface or base class. This allows for code reuse and flexibility, as new classes can be added without modifying existing code that relies on the common interface.

Here's an example in TypeScript to illustrate polymorphism:

```ts
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  makeSound(): void {
    console.log("The animal makes a sound");
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log("The dog barks");
  }
}

class Cat extends Animal {
  makeSound(): void {
    console.log("The cat meows");
  }
}

function animalSound(animal: Animal): void {
  animal.makeSound();
}

const dog = new Dog("Buddy");
const cat = new Cat("Whiskers");

animalSound(dog); // Output: "The dog barks"
animalSound(cat); // Output: "The cat meows"
```

In the above example, we have a base class `Animal` with a method `makeSound()`. The `Dog` and `Cat` classes are derived from the `Animal` class and provide their own implementation of the `makeSound()` method. The `animalSound()` function takes an `Animal` parameter and calls the `makeSound()` method on it. When we pass a `Dog` object and a `Cat` object to the `animalSound()` function, the appropriate `makeSound()` method of each object is invoked based on their actual types, demonstrating polymorphism.

Polymorphism allows for code that can work with different objects based on their common interface or base class, providing flexibility, extensibility, and code reusability in object-oriented programming.


# SPANISH
El polimorfismo es un concepto clave en la programación orientada a objetos que permite que un objeto pueda tomar múltiples formas o comportamientos. Se refiere a la capacidad de un objeto para ser tratado como una instancia de su clase base o como una instancia de cualquiera de sus clases derivadas. Esto permite que diferentes objetos de clases relacionadas respondan de manera diferente a la misma llamada de método o propiedad.

El polimorfismo se basa en dos características principales de la programación orientada a objetos: la herencia y la sobrescritura de métodos. La herencia permite que una clase herede propiedades y métodos de su clase padre, mientras que la sobrescritura de métodos permite que una subclase proporcione su propia implementación de un método heredado de la clase base.

El polimorfismo proporciona una forma de escribir código que puede funcionar con objetos de diferentes clases, siempre y cuando cumplan con una interfaz común o una clase base. Esto permite reutilizar código y brinda flexibilidad, ya que se pueden agregar nuevas clases sin modificar el código existente que depende de la interfaz común.

Aquí tienes un ejemplo en TypeScript para ilustrar el polimorfismo:

```run-ts
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  makeSound(): void {
    console.log("El animal emite un sonido");
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log("El perro ladra");
  }
}

class Cat extends Animal {
  makeSound(): void {
    console.log("El gato maúlla");
  }
}

function animalSound(animal: Animal): void {
  animal.makeSound();
}

const dog = new Dog("Buddy");
const cat = new Cat("Whiskers");

animalSound(dog); // Salida: "El perro ladra"
animalSound(cat); // Salida: "El gato maúlla"
```

En el ejemplo anterior, tenemos una clase base `Animal` con un método `makeSound()`. Las clases `Dog` y `Cat` son derivadas de la clase `Animal` y proporcionan su propia implementación del método `makeSound()`. La función `animalSound()` toma un parámetro de tipo `Animal` y llama al método `makeSound()` en él. Cuando pasamos un objeto `Dog` y un objeto `Cat` a la función `animalSound()`, se invoca el método `makeSound()` apropiado de cada objeto según sus tipos reales, demostrando el polimorfismo.

El polimorfismo permite escribir código que puede trabajar con diferentes objetos basados en su interfaz común o clase base, proporcionando flexibilidad, extensibilidad y reutilización de código en la programación orientada a objetos.