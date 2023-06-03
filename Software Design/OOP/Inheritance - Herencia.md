# ENGLISH
**Inheritance**

Inheritance is a key concept in object-oriented programming (OOP) that allows a class to inherit properties and methods from another class. It establishes a relationship between classes, where one class (the subclass or derived class) inherits the characteristics of another class (the superclass or base class). The derived class can then extend and specialize the behavior of the base class by adding its own properties and methods or overriding the inherited ones.

Inheritance promotes code reuse, abstraction, and modularity. It allows you to create a hierarchy of classes that represent increasingly specific and specialized concepts. The base class serves as a blueprint for the derived classes, providing a foundation of common functionality that can be shared among multiple subclasses.

In TypeScript, inheritance is implemented using the `extends` keyword. A subclass can inherit from a single superclass, but a superclass can have multiple subclasses. The subclass inherits all accessible members (properties and methods) from the superclass, including public and protected members. Private members are not inherited and can only be accessed within the defining class.

Here's an example in TypeScript that illustrates inheritance:

```ts
class Shape {
  protected color: string;

  constructor(color: string) {
    this.color = color;
  }

  public getInfo(): string {
    return `This shape is ${this.color}.`;
  }

  public calculateArea(): number {
    return 0;
  }
}

class Circle extends Shape {
  private radius: number;

  constructor(color: string, radius: number) {
    super(color);
    this.radius = radius;
  }

  public calculateArea(): number {
    return Math.PI * Math.pow(this.radius, 2);
  }
}

class Rectangle extends Shape {
  private width: number;
  private height: number;

  constructor(color: string, width: number, height: number) {
    super(color);
    this.width = width;
    this.height = height;
  }

  public calculateArea(): number {
    return this.width * this.height;
  }
}

const circle = new Circle("Red", 5);
console.log(circle.getInfo()); // Accessing a public method from the base class
console.log(circle.calculateArea()); // Accessing an overridden method in the subclass

const rectangle = new Rectangle("Blue", 4, 6);
console.log(rectangle.getInfo());
console.log(rectangle.calculateArea());
```

In the above example, the `Shape` class is the base class that defines common properties and methods for shapes. The `Circle` and `Rectangle` classes inherit from `Shape` using the `extends` keyword. They override the `calculateArea` method to provide their own implementation specific to circles and rectangles.

The `Circle` class adds a private property `radius` and implements the area calculation formula for circles. The `Rectangle` class adds private properties `width` and `height` and implements the area calculation formula for rectangles.

By inheriting from the `Shape` class, both the `Circle` and `Rectangle` classes inherit the `color` property and the `getInfo` method, allowing them to access and modify the `color` property and use the method to retrieve information about the shape. They also provide their own implementations of the `calculateArea` method, which are specific to their respective shapes.

Inheritance allows you to create a hierarchy of classes, organizing related concepts and promoting code reuse. It helps to establish a relationship between classes based on their similarities and differences, enabling you to model real-world scenarios more accurately in your code.

# SPANISH

**Herencia**

La herencia es un concepto fundamental en la programación orientada a objetos (POO) que permite que una clase herede propiedades y métodos de otra clase. Establece una relación entre clases, donde una clase (la subclase o clase derivada) hereda las características de otra clase (la superclase o clase base). La clase derivada puede extender y especializar el comportamiento de la clase base agregando sus propias propiedades y métodos o sobrescribiendo los heredados.

La herencia promueve la reutilización de código, la abstracción y la modularidad. Permite crear una jerarquía de clases que representan conceptos cada vez más específicos y especializados. La clase base sirve como un modelo para las clases derivadas, proporcionando una base de funcionalidad común que se puede compartir entre varias subclases.

En TypeScript, la herencia se implementa utilizando la palabra clave `extends`. Una subclase puede heredar de una sola superclase, pero una superclase puede tener múltiples subclases. La subclase hereda todos los miembros accesibles (propiedades y métodos) de la superclase, incluyendo los miembros públicos y protegidos. Los miembros privados no se heredan y solo se pueden acceder dentro de la clase que los define.

Aquí tienes un ejemplo en TypeScript que ilustra la herencia:

```ts
class Forma {
  protected color: string;

  constructor(color: string) {
    this.color = color;
  }

  public obtenerInformacion(): string {
    return `Esta forma es de color ${this.color}.`;
  }

  public calcularArea(): number {
    return 0;
  }
}

class Circulo extends Forma {
  private radio: number;

  constructor(color: string, radio: number) {
    super(color);
    this.radio = radio;
  }

  public calcularArea(): number {
    return Math.PI * Math.pow(this.radio, 2);
  }
}

class Rectangulo extends Forma {
  private ancho: number;
  private alto: number;

  constructor(color: string, ancho: number, alto: number) {
    super(color);
    this.ancho = ancho;
    this.alto = alto;
  }

  public calcularArea(): number {
    return this.ancho * this.alto;
  }
}

const circulo = new Circulo("Rojo", 5);
console.log(circulo.obtenerInformacion()); // Accediendo a un método público de la clase base
console.log(circulo.calcularArea()); // Accediendo a un método sobrescrito en la subclase

const rectangulo = new Rectangulo("Azul", 4, 6);
console.log(rectangulo.obtenerInformacion());
console.log(rectangulo.calcularArea());
```
En el ejemplo anterior, la clase `Forma` es la clase base que define propiedades y métodos comunes para las formas. Las clases `Circulo` y `Rectangulo` heredan de `Forma` utilizando la palabra clave `extends`. Sobrescriben el método `calcularArea` para proporcionar su propia implementación específica para círculos y rectángulos.

La clase `Circulo` agrega una propiedad privada `radio` e implementa la fórmula de cálculo de área para círculos. La clase `Rectangulo` agrega propiedades privadas `ancho` y `alto` e implementa la fórmula de cálculo de área para rectángulos.

Al heredar de la clase `Forma`, tanto las clases `Circulo` como `Rectangulo` heredan la propiedad `color` y el método `obtenerInformacion`, lo que les permite acceder y modificar la propiedad `color` y usar el método para obtener información sobre la forma. También proporcionan sus propias implementaciones del método `calcularArea`, que son específicas para cada forma respectiva.

La herencia te permite crear una jerarquía de clases, organizar conceptos relacionados y fomentar la reutilización de código. Ayuda a establecer una relación entre clases basada en sus similitudes y diferencias, lo que te permite modelar de manera más precisa escenarios del mundo real en tu código.