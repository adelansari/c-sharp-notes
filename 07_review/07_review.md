# 07_review: Advanced OOP Concepts and Strategy Pattern in C#

## Overview

The `07_review` folder delves into advanced Object-Oriented Programming (OOP) concepts and the implementation of the Strategy Pattern in C#. This section is crucial for understanding how to design flexible and dynamic software systems using advanced OOP techniques.

## Topics Covered

1. **Advanced OOP Concepts**
   - Exploring more complex aspects of OOP such as composition, delegation, and advanced inheritance.
   - Example:
     ```csharp
     class Warrior {
         private IStrategy battleStrategy;
         public Warrior(IStrategy strategy) {
             this.battleStrategy = strategy;
         }
         public void ChangeStrategy(IStrategy strategy) {
             this.battleStrategy = strategy;
         }
         public void ExecuteStrategy() {
             battleStrategy.Execute();
         }
     }
     ```

2. **Strategy Pattern**
   - Understanding the Strategy Pattern, which allows the behavior of a class to be changed at runtime by introducing new executable strategies.
   - Example:
     ```csharp
     interface IStrategy {
         void Execute();
     }
     class AggressiveStrategy : IStrategy {
         public void Execute() {
             // Aggressive behavior logic
         }
     }
     class DefensiveStrategy : IStrategy {
         public void Execute() {
             // Defensive behavior logic
         }
     }
     ```

3. **Example Classes: `Warrior`, `Battle`, `IStrategy`, `CanTeleport`, `CantTeleport`**
   - `Warrior`: A class representing a warrior character in a game or simulation.
   - `Battle`: A class that might use different strategies based on the context.
   - `IStrategy`, `CanTeleport`, `CantTeleport`: Interfaces and classes that demonstrate the Strategy Pattern in action.

## Study Notes

- Advanced OOP concepts like composition and delegation provide alternatives to inheritance, offering more flexibility in some scenarios.
- The Strategy Pattern is a behavioral design pattern that enables an algorithm's behavior to be selected at runtime, making a system more modular and extendable.
- Practice implementing the Strategy Pattern in different contexts to understand its versatility and power.

## Exercises

1. Create a new strategy for the `Warrior` class and integrate it to see how it changes the warrior's behavior.
2. Implement a different behavioral pattern (like Observer or Singleton) and compare it with the Strategy Pattern.
3. Design a small simulation where strategies can be swapped dynamically based on different conditions or user input.

---

Mastering advanced OOP concepts and design patterns like the Strategy Pattern is key to building sophisticated and adaptable software systems in C#. These exercises and examples provide a practical framework for understanding and applying these concepts.
