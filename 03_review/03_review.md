# 03_review: Advanced Object-Oriented Programming in C#

## Overview

The `03_review` folder continues the exploration of Object-Oriented Programming (OOP) in C#, focusing on more advanced concepts. This section is crucial for understanding how to effectively encapsulate data, define behaviors, and create robust C# applications.

## Topics Covered

1. **Access Modifiers (public, private, protected)**
   - Understanding how to control access to class members.
   - Example:
     ```csharp
     class Animal {
         private string name; // Only accessible within the class
         protected string sound; // Accessible within the class and derived classes
         public void MakeSound() {
             Console.WriteLine($"{name} says {sound}");
         }
     }
     ```

2. **Constants and Read-only Fields**
   - Using `const` and `readonly` to define immutable values.
   - Example:
     ```csharp
     class Animal {
         public const string CATEGORY = "Mammal";
         public readonly int idNum;
         public Animal(int id) {
             idNum = id;
         }
     }
     ```

3. **Constructors, Setters, and Getters**
   - Advanced use of constructors for object initialization.
   - Implementing setters and getters for property manipulation.
   - Example:
     ```csharp
     class Animal {
         private string name;
         public string Name {
             get { return name; }
             set { name = value; }
         }
     }
     ```

4. **Properties and Static Properties**
   - Using properties to encapsulate data and validate input.
   - Understanding static properties and their class-wide impact.
   - Example:
     ```csharp
     class Animal {
         private static int numOfAnimals = 0;
         public static int NumOfAnimals {
             get { return numOfAnimals; }
             set { numOfAnimals = value; }
         }
     }
     ```

5. **Example Class: `Animal`**
   - The `Animal` class demonstrates the use of advanced OOP features like access modifiers, properties, and constructors.

## Study Notes

- Focus on understanding how access modifiers affect the visibility of class members.
- Learn the difference between `const` and `readonly`, and when to use each.
- Get comfortable with writing properties, including automatic properties for simpler implementation.
- Observe how static properties are shared across all instances of a class.

## Exercises

1. Modify the `Animal` class to include a method that displays all properties of the animal.
   ```csharp
    class Animal {
         private string name;
         private string sound;
         public void DisplayInfo() {
              Console.WriteLine($"Name: {name}, Sound: {sound}");
         }
    }

    Animal cat = new Animal();
    cat.name = "Whiskers";
    cat.sound = "Meow";
    cat.DisplayInfo();
    ```
2. Create a new class with private fields and public properties, and experiment with different access levels.
   ```csharp
    class Person {
         private string name;
         public string Name {
             get { return name; }
             set { name = value; }
         }
    }

    Person p = new Person();
    p.Name = "Alice";
    Console.WriteLine(p.Name);
   ```
3. Implement a static property in a class and demonstrate its shared nature across multiple instances.
   ```csharp
    class Vehicle {
         private static int numOfVehicles = 0;
         public static int NumOfVehicles {
             get { return numOfVehicles; }
             set { numOfVehicles = value; }
         }
    }

    Vehicle car1 = new Vehicle();
    Vehicle car2 = new Vehicle();
    Vehicle.NumOfVehicles = 2;
    Console.WriteLine(Vehicle.NumOfVehicles);
   ```

---

