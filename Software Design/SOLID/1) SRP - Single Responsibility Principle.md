  [[SOLID]] #CleanCode
# ENGLISH
**Single Responsibility Principle (SRP)**

The Single Responsibility Principle states that a class should have only one reason to change. In other words, a class should have a single responsibility or function within the system. This principle promotes code cohesion and modularity, as each class focuses on performing a specific task and does not assume multiple responsibilities.

When a class has a single responsibility, it becomes easier to understand, maintain, and test. If a class has multiple responsibilities, changes related to one responsibility may inadvertently affect other parts of the system, leading to fragile and hard-to-maintain code.

Here's an example in TypeScript that illustrates the Single Responsibility Principle:
```ts
// Incorrect example violating SRP
class Employee {
  constructor(private name: string, private employeeID: number) {}

  calculateSalary() {
    // Logic to calculate employee's salary
  }

  saveToDatabase() {
    // Logic to save employee's data to the database
  }

  generatePayStub() {
    // Logic to generate employee's pay stub
  }
}
```

In the above example, the `Employee` class assumes multiple responsibilities, such as calculating the salary, saving data to the database, and generating the pay stub. This violates SRP as the class has more than one reason to change. If any of these responsibilities change, it may require modifying the `Employee` class and impacting other areas of the system.

Here's an example that adheres to the Single Responsibility Principle:

```ts
// Correct example following SRP
class Employee {
  constructor(private name: string, private employeeID: number) {}

  calculateSalary() {
    // Logic to calculate employee's salary
  }
}

class EmployeeDatabase {
  saveToDatabase(employee: Employee) {
    // Logic to save employee's data to the database
  }
}

class Payroll {
  generatePayStub(employee: Employee) {
    // Logic to generate employee's pay stub
  }
}
```


In this case, we have separated the responsibilities into different classes. The Employee class is solely responsible for employee data and salary calculation. The EmployeeDatabase class handles data persistence to the database, while the Payroll class is responsible for generating the pay stub. Each class has a single responsibility, making the code more modular and easier to maintain.

Remember, adhering to the Single Responsibility Principle helps improve code readability, maintainability, and scalability in the long run.


# SPANISH
**Principio de Responsabilidad Única (SRP - Single Responsibility Principle)**

El Principio de Responsabilidad Única establece que una clase debe tener una sola razón para cambiar. En otras palabras, una clase debe tener una única responsabilidad o función en el sistema. Este principio promueve la cohesión y modularidad del código, ya que cada clase se enfoca en realizar una tarea específica y no asume múltiples responsabilidades.

Cuando una clase tiene una única responsabilidad, se vuelve más fácil de entender, mantener y probar. Si una clase tiene múltiples responsabilidades, los cambios relacionados con una responsabilidad podrían afectar inadvertidamente a otras partes del sistema, lo que lleva a un código frágil y difícil de mantener.

Un ejemplo de código en TypeScript que ilustra el Principio de Responsabilidad Única podría ser el siguiente:

```ts
// Ejemplo incorrecto que viola el SRP
class Employee {
  constructor(private name: string, private employeeID: number) {}

  calculateSalary() {
    // Lógica para calcular el salario del empleado
  }

  saveToDatabase() {
    // Lógica para guardar los datos del empleado en la base de datos
  }

  generatePayStub() {
    // Lógica para generar el comprobante de pago del empleado
  }
}
```

En el ejemplo anterior, la clase `Employee` asume múltiples responsabilidades, como el cálculo del salario, guardar los datos en la base de datos y generar el comprobante de pago. Esto viola el SRP, ya que la clase tiene más de una razón para cambiar. Si alguna de estas responsabilidades cambia, es posible que sea necesario modificar la clase `Employee` y afectar otras áreas del sistema.

A continuación, se muestra un ejemplo que sigue el Principio de Responsabilidad Única:

```ts
// Ejemplo correcto que sigue el SRP
class Employee {
  constructor(private name: string, private employeeID: number) {}

  calculateSalary() {
    // Lógica para calcular el salario del empleado
  }
}

class EmployeeDatabase {
  saveToDatabase(employee: Employee) {
    // Lógica para guardar los datos del empleado en la base de datos
  }
}

class Payroll {
  generatePayStub(employee: Employee) {
    // Lógica para generar el comprobante de pago del empleado
  }
}
```

En este caso, hemos separado las responsabilidades en diferentes clases. La clase `Employee` se encarga exclusivamente de los datos del empleado y el cálculo del salario. La clase `EmployeeDatabase` se encarga de la persistencia de datos en la base de datos, mientras que la clase `Payroll` se encarga de generar el comprobante de pago. Cada clase tiene una única responsabilidad, lo que hace que el código sea más modular y fácil de mantener.

Recuerda que seguir el Principio de Responsabilidad Única ayuda a mejorar la legibilidad, mantenibilidad y escalabilidad del código a largo plazo.