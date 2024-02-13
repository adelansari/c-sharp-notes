# 06_review: Interfaces and Design Patterns in C#

## Overview

The `06_review` folder focuses on the use of interfaces and the implementation of design patterns in C#. This section is essential for understanding how to create modular, reusable, and maintainable code structures in professional software development.

## Topics Covered

1. **Interfaces**
   - Exploring the concept of interfaces as contracts for classes, defining a set of methods and properties that implementing classes must provide.
   - Example:
     ```csharp
     interface IDrivable {
         void Drive();
         void Stop();
     }
     class Car : IDrivable {
         public void Drive() {
             // Driving logic
         }
         public void Stop() {
             // Stop logic
         }
     }
     ```

2. **Design Patterns: Command Pattern**
   - Understanding the command pattern, which encapsulates a request as an object, thereby allowing for parameterization of clients with queues, requests, and operations.
   - Example:
     ```csharp
     interface ICommand {
         void Execute();
     }
     class LightOnCommand : ICommand {
         public void Execute() {
             // Turn on the light
         }
     }
     class RemoteControl {
         public void Submit(ICommand command) {
             command.Execute();
         }
     }
     ```

3. **Example Interfaces: `ICommand`, `IDrivable`, `IElectronicDevice`**
   - `ICommand`: An interface representing a command in the command pattern.
   - `IDrivable`: An interface representing the drivable behavior of a vehicle.
   - `IElectronicDevice`: An interface representing operations for an electronic device.

## Study Notes

- Interfaces are a powerful way to define capabilities that different classes can implement, promoting a loose coupling between classes.
- The command pattern is an excellent example of encapsulating method invocation, requests, or operations into separate objects, providing additional layers of abstraction and flexibility.
- Practice implementing interfaces in various classes and see how they enforce a contract for the class's behavior.

## Exercises

1. Create a new interface and implement it in multiple classes, observing how it enforces a consistent structure across different implementations.
2. Implement a simple version of the command pattern with a few commands and a command invoker.
3. Explore creating an interface for a common behavior (like `IChargeable` for charging devices) and implement it in different classes.

---

Understanding interfaces and design patterns like the command pattern is crucial for advanced C# programming and software design. These concepts are fundamental in creating systems that are easy to maintain, extend, and refactor.
