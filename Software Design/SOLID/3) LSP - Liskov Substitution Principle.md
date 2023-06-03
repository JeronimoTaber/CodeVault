  [[SOLID]] #CleanCode

# ENGLISH

**Liskov Substitution Principle (LSP)**

The Liskov Substitution Principle states that objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program. In other words, if class A is a subclass of class B, then instances of class B should be substitutable with instances of class A without altering the expected behavior of the program.

This principle is based on the concept that derived classes should be fully substitutable for their base classes, without introducing errors or unexpected behaviors. It ensures that code using objects of the base class will work correctly when instances of the derived classes are used.

Here's an example in TypeScript that illustrates the Liskov Substitution Principle:

```run-ts
abstract class CustomError {
  error: Error;
  errorMessage: string = ''; // Add an initializer or assign a default value

  constructor(error: Error) {
    this.error = error;
  }

  abstract createErrorMessage(): void;
  abstract logError(): void;
}

class ConnectionError extends CustomError {
  constructor(error: Error) {
    super(error);
  }

  createErrorMessage(): void {
    this.errorMessage = `Connection error: ${this.error.message}`;
  }

  logError(): void {
    console.log(this.errorMessage);
  }
}

class DBError extends CustomError {
  constructor(error: Error) {
    super(error);
  }

  createErrorMessage(): void {
    this.errorMessage = `DB error: ${this.error.message}`;
  }

  logError(): void {
    console.log(this.errorMessage);
  }

  createAlert(): void {
    console.log("Alert Sent");
  }
}

const errorDecorator = (customError: CustomError) => {
  customError.createErrorMessage();
  customError.logError();

  if (customError instanceof DBError) {
    (customError as DBError).createAlert();
  }
};

const main = () => {
  const dbError = new DBError(new Error("DB error"));
  errorDecorator(dbError);
};

main();
```
In the above example, In the above example, 
```ts
  if (customError instanceof DBError) {
    customError.createAlert();
  }
```
the code smells because it requires knowing the instance type beforehand. Extend this case to future errors of `APIError`, `GraphError` and so on, and it results in a series of never-ending if/else cases. The problem arises because of the overgeneralization of use cases.


Predicting the future of these types of classes is where the problem exists. It is better to be defensive in such assumptions and go for a ``“has/a” class type`` instead of an ``“is/a” class type``. Let’s take a look at an example to understand this better:

```run-ts
abstract class CustomError {
  error: Error;
  errorMessage: string = "";
  constructor(error: Error) {
    this.error = error;
  }
  abstract createErrorMessage(): void;
  abstract logError(): void;
}

class ConnectionError extends CustomError {
  constructor(error: Error) {
    super(error);
  }
  createErrorMessage(): void {
    this.errorMessage = `Connection error: ${this.error.message}`;
  }
  logError(): void {
    console.log(this.errorMessage);
  }
}

class AlertSystem {
  public sendAlert(message: string) {
    console.log("Alert sent");
  }
}

class DBError extends CustomError {
  constructor(error: Error) {
    super(error);
  }

  createErrorMessage(): void {
    this.errorMessage = `DB error: ${this.error.message}`;
  }

  logError(): void {
    console.log(this.errorMessage);
    const alert = new AlertSystem();
    alert.sendAlert(this.errorMessage);
  }
}

const errorDecorator = (customError: CustomError) => {
  customError.createErrorMessage();
  customError.logError();
};

const main = () => {
  const dbError = new DBError(new Error("DB err1"));
  errorDecorator(dbError);
};

main();
```

Considering our example of error handlers again: One approach can be to compose our logging method with an alerting mechanism. The `AlertSystem` is now used in composition and added to `DBError’s logError` instead. Another viable approach would have been to completely decouple the `AlertSystem` from both the errors. When compared to our previous examples we do not have any more if/else conditions on the type of class instance.

Adhering to the Liskov Substitution Principle ensures that derived classes are truly substitutable for their base classes, avoiding surprises and unexpected behaviors in code that relies on polymorphism.

# SPANISH

**El Principio de Sustitución de Liskov (LSP)**

El Principio de Sustitución de Liskov establece que los objetos de una superclase deben poder ser reemplazados por objetos de sus subclases sin afectar la corrección del programa. En otras palabras, si la clase A es una subclase de la clase B, entonces las instancias de la clase B deben poder ser sustituidas por instancias de la clase A sin alterar el comportamiento esperado del programa.

Este principio se basa en el concepto de que las clases derivadas deben ser completamente sustituibles por sus clases base, sin introducir errores o comportamientos inesperados. Garantiza que el código que utiliza objetos de la clase base funcione correctamente cuando se utilizan instancias de las clases derivadas.

Aquí tienes un ejemplo en TypeScript que ilustra el Principio de Sustitución de Liskov:

```run-ts
abstract class CustomError {
  error: Error;
  errorMessage: string = ''; // Add an initializer or assign a default value

  constructor(error: Error) {
    this.error = error;
  }

  abstract createErrorMessage(): void;
  abstract logError(): void;
}

class ConnectionError extends CustomError {
  constructor(error: Error) {
    super(error);
  }

  createErrorMessage(): void {
    this.errorMessage = `Connection error: ${this.error.message}`;
  }

  logError(): void {
    console.log(this.errorMessage);
  }
}

class DBError extends CustomError {
  constructor(error: Error) {
    super(error);
  }

  createErrorMessage(): void {
    this.errorMessage = `DB error: ${this.error.message}`;
  }

  logError(): void {
    console.log(this.errorMessage);
  }

  createAlert(): void {
    console.log("Alert Sent");
  }
}

const errorDecorator = (customError: CustomError) => {
  customError.createErrorMessage();
  customError.logError();

  if (customError instanceof DBError) {
    (customError as DBError).createAlert();
  }
};

const main = () => {
  const dbError = new DBError(new Error("DB error"));
  errorDecorator(dbError);
};

main();
```

En el siguiente fragmento de código del ejemplo anterios:
```ts
  if (customError instanceof DBError) {
    customError.createAlert();
  }
```

el código no es óptimo ya que requiere conocer el tipo de instancia de antemano. Si extendemos este caso a futuros errores como `APIError`, `GraphError`, `etc`., nos encontraremos con una serie de condicionales if/else interminables. El problema surge debido a la sobre-generalización de casos de uso.

Predecir el futuro de este tipo de clases es donde reside el problema. Es mejor ser defensivo en tales suposiciones y optar por un tipo de clase `"tener" ("has/a")` en lugar de un tipo de clase `"ser" ("is/a")`. Echemos un vistazo a un ejemplo para entender esto mejor:

```run-ts
abstract class CustomError {
  error: Error;
  errorMessage: string = "";
  constructor(error: Error) {
    this.error = error;
  }
  abstract createErrorMessage(): void;
  abstract logError(): void;
}

class ConnectionError extends CustomError {
  constructor(error: Error) {
    super(error);
  }
  createErrorMessage(): void {
    this.errorMessage = `Connection error: ${this.error.message}`;
  }
  logError(): void {
    console.log(this.errorMessage);
  }
}

class AlertSystem {
  public sendAlert(message: string) {
    console.log("Alert sent");
  }
}

class DBError extends CustomError {
  constructor(error: Error) {
    super(error);
  }

  createErrorMessage(): void {
    this.errorMessage = `DB error: ${this.error.message}`;
  }

  logError(): void {
    console.log(this.errorMessage);
    const alert = new AlertSystem();
    alert.sendAlert(this.errorMessage);
  }
}

const errorDecorator = (customError: CustomError) => {
  customError.createErrorMessage();
  customError.logError();
};

const main = () => {
  const dbError = new DBError(new Error("DB err1"));
  errorDecorator(dbError);
};

main();
```

Considerando nuestro ejemplo de controladores de errores nuevamente, un enfoque puede ser componer nuestro método de registro con un mecanismo de alerta. Ahora se utiliza el `AlertSystem` en composición y se agrega al método `logError` de `DBError`. Otra opción viable habría sido desacoplar por completo el `AlertSystem` de ambos errores. En comparación con nuestros ejemplos anteriores, ya no tenemos más condiciones `if/else` basadas en el tipo de instancia de la clase.

Cumplir con el Principio de Sustitución de Liskov garantiza que las clases derivadas sean verdaderamente sustituibles por sus clases base, evitando sorpresas y comportamientos inesperados en el código que depende de la polimorfismo.