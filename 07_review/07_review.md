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
   ```csharp
    public interface ICombatStrategy
    {
        void Execute();
    }

    public class AggressiveStrategy : ICombatStrategy
    {
        public void Execute()
        {
            Console.WriteLine("Aggressive strategy: Attack!");
        }
    }

    public class DefensiveStrategy : ICombatStrategy
    {
        public void Execute()
        {
            Console.WriteLine("Defensive strategy: Defend!");
        }
    }

    public class Warrior
    {
        private ICombatStrategy _combatStrategy;

        public Warrior(ICombatStrategy combatStrategy)
        {
            _combatStrategy = combatStrategy;
        }

        public void SetStrategy(ICombatStrategy combatStrategy)
        {
            _combatStrategy = combatStrategy;
        }

        public void ExecuteStrategy()
        {
            _combatStrategy.Execute();
        }
    }

    Warrior warrior = new Warrior(new AggressiveStrategy());
    warrior.ExecuteStrategy();  // Outputs: "Aggressive strategy: Attack!"

    warrior.SetStrategy(new DefensiveStrategy());
    warrior.ExecuteStrategy();  // Outputs: "Defensive strategy: Defend!"
    ```
2. Implement a different behavioral pattern (like Observer or Singleton) and compare it with the Strategy Pattern.
   ```csharp
   public interface IObserver
    {
        void Update(string message);
    }

    public class Observer : IObserver
    {
        private string _name;

        public Observer(string name)
        {
            _name = name;
        }

        public void Update(string message)
        {
            Console.WriteLine($"{_name} received: {message}");
        }
    }

    public class Subject
    {
        private List<IObserver> _observers = new List<IObserver>();

        public void RegisterObserver(IObserver observer)
        {
            _observers.Add(observer);
        }

        public void UnregisterObserver(IObserver observer)
        {
            _observers.Remove(observer);
        }

        public void NotifyObservers(string message)
        {
            foreach (var observer in _observers)
            {
                observer.Update(message);
            }
        }
    }
   ```
3. Design a small simulation where strategies can be swapped dynamically based on different conditions or user input.
   ```csharp
    public class Battle
     {
          private ICombatStrategy _strategy;
    
          public Battle(ICombatStrategy strategy)
          {
                _strategy = strategy;
          }
    
          public void ChangeStrategy(ICombatStrategy strategy)
          {
                _strategy = strategy;
          }
    
          public void ExecuteStrategy()
          {
                _strategy.Execute();
          }
     }
    
     Battle battle = new Battle(new AggressiveStrategy());
     battle.ExecuteStrategy();  // Outputs: "Aggressive strategy: Attack!"
    
     battle.ChangeStrategy(new DefensiveStrategy());
     battle.ExecuteStrategy();  // Outputs: "Defensive strategy: Defend!"
    ```

    or

    ```csharp
    public interface ICombatStrategy
    {
        void Execute();
    }

    public class AggressiveStrategy : ICombatStrategy
    {
        public void Execute()
        {
            Console.WriteLine("Aggressive strategy: Attack!");
        }
    }

    public class DefensiveStrategy : ICombatStrategy
    {
        public void Execute()
        {
            Console.WriteLine("Defensive strategy: Defend!");
        }
    }

    public class Warrior
    {
        private ICombatStrategy _combatStrategy;

        public Warrior(ICombatStrategy combatStrategy)
        {
            _combatStrategy = combatStrategy;
        }

        public void SetStrategy(ICombatStrategy combatStrategy)
        {
            _combatStrategy = combatStrategy;
        }

        public void ExecuteStrategy()
        {
            _combatStrategy.Execute();
        }
    }

    public class Simulation
    {
        public void Run()
        {
            Warrior warrior = new Warrior(new AggressiveStrategy());

            while (true)
            {
                Console.WriteLine("Enter 'a' for aggressive strategy, 'd' for defensive strategy, or 'q' to quit:");
                string input = Console.ReadLine();

                if (input == "a")
                {
                    warrior.SetStrategy(new AggressiveStrategy());
                }
                else if (input == "d")
                {
                    warrior.SetStrategy(new DefensiveStrategy());
                }
                else if (input == "q")
                {
                    break;
                }
                else
                {
                    Console.WriteLine("Invalid input");
                    continue;
                }

                warrior.ExecuteStrategy();
            }
        }
    }
    ```

---
