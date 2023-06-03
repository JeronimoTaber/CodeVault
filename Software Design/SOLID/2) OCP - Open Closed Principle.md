 [[SOLID]] #CleanCode

# ENGLISH

**Open/Closed Principle (OCP)**

The Open/Closed Principle states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. This means that the behavior of a system can be extended without modifying its existing code. The principle encourages the use of abstraction, inheritance, and interfaces to achieve this goal.

By designing software that is open for extension, we can add new features or behaviors to the system without altering its existing code. This promotes code reusability and maintainability, as modifications to existing code can introduce bugs and create a ripple effect throughout the system.

Here's an example in TypeScript that demonstrates the Open/Closed Principle:

```ts
class Order {
  id: number;
  items: string[];
  shipping: string;

  // constructor

  getTotalCost(): number {
    // calculates total cost
  }

  getShippingCosts(): number {
    const totalCost = this.getTotalCost();

    if (this.shipping === "ground") {
      return totalCost > 50 ? 0 : 5.95;
    }

    if (this.shipping === "air") {
      return 10.95;
    }

    return 0;
  }
}
```


In the above example, the `Order` class violate the Open/Closed Principle. If we want to introduce a new shipping, such as a sea or pick in store, we would need to modify the existing classes and add a new method for calculating the costs of a the shipping. This violates the principle since we are modifying existing code instead of extending it.

To adhere to the Open/Closed Principle, we can use abstraction and interfaces:

```ts
class Order {
  id: number;
  items: string[];
  shipping: Shipping;

  // constructor

  getTotalCost(): number {
    // calculates total cost
  }
}

interface Shipping {
  getShippingCosts(totalCost: number): number;
}

class Ground implements Shipping {
  getShippingCosts(totalCost: number): number {
    return totalCost > 50 ? 0 : 5.95;
  }
}

class Air implements Shipping {
  getShippingCosts(): number {
    return 10.95;
  }
}

class PickUpInStore implements Shipping {
  getShippingCosts(): number {
    return 0;
  }
}
```

In this revised example, we define the `Shipping` interface that includes the `getShippingCosts` method. Each class, such as `Ground`, `Air`, and `PickUpInStore`, implements the `Shipping` interface and provides its own implementation of the `getShippingCosts` method. Now, if we want to introduce a new shape, we can simply create a new class that implements the `Shipping` interface and add the calculation logic for that specific shape, without modifying the existing code.

Following the Open/Closed Principle allows for a more flexible and maintainable codebase, as new functionality can be added through extension rather than modification.

# SPANISH
**Principio de Abierto/Cerrado (OCP)**

El Principio de Abierto/Cerrado establece que las entidades de software (clases, módulos, funciones, etc.) deben estar abiertas para su extensión pero cerradas para su modificación. Esto significa que el comportamiento de un sistema puede ser extendido sin necesidad de modificar su código existente. El principio promueve el uso de abstracción, herencia e interfaces para lograr este objetivo.

Al diseñar software que está abierto para su extensión, podemos agregar nuevas características o comportamientos al sistema sin modificar el código existente. Esto promueve la reutilización y mantenibilidad del código, ya que las modificaciones al código existente pueden introducir errores y crear un efecto dominó en todo el sistema.

Aquí tienes un ejemplo en TypeScript que muestra el Principio de Abierto/Cerrado:

```ts
// Ejemplo incorrecto que viola el OCP
class Order {
  id: number;
  items: string[];
  shipping: string;

  // constructor

  getTotalCost(): number {
    // calcula el costo total
  }

  getShippingCosts(): number {
    const totalCost = this.getTotalCost();

    if (this.shipping === "ground") {
      return totalCost > 50 ? 0 : 5.95;
    }

    if (this.shipping === "air") {
      return 10.95;
    }

    return 0;
  }
}
```

En el ejemplo anterior, la clase `Order` y sus clases derivadas violan el Principio de Abierto/Cerrado. Si queremos introducir una nueva forma, como un triángulo, tendríamos que modificar las clases existentes y agregar un nuevo método para calcular el área de un triángulo. Esto viola el principio, ya que estamos modificando código existente en lugar de extenderlo.

Para cumplir con el Principio de Abierto/Cerrado, podemos utilizar abstracción e interfaces:

```ts
// Ejemplo correcto que sigue el OCP

class Order {
  id: number;
  items: string[];
  shipping: Shipping;

  // constructor

  getTotalCost(): number {
    // calcula el costo total
  }
}

interface Shipping {
  getShippingCosts(totalCost: number): number;
}

class Ground extends Order implements Shipping {
  getShippingCosts(totalCost: number): number {
    return totalCost > 50 ? 0 : 5.95;
  }
}

class Air extends Order implements Shipping {
  getShippingCosts(): number {
    return 10.95;
  }
}

class PickUpInStore extends Order implements Shipping {
  getShippingCosts(): number {
    return 0;
  }
}
```

En este ejemplo revisado, definimos la interfaz `Forma` que incluye el método `calcularArea()`. Cada forma, como `Circulo`, `Rectangulo` y `Triangulo`, implementa la interfaz `Forma` y proporciona su propia implementación del método `calcularArea()`. Ahora, si queremos introducir una nueva forma, simplemente creamos una nueva clase que implemente la interfaz `Forma` y agregamos la lógica de cálculo específica para esa forma, sin necesidad de modificar el código existente.

Seguir el Principio de Abierto/Cerrado permite tener un código más flexible y fácil de mantener, ya que se pueden agregar nuevas funcionalidades a través de la extensión en lugar de la modificación.