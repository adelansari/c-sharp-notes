# 04_review: Inheritance and Polymorphism in C#

## Overview

The `04_review` folder is dedicated to exploring inheritance and polymorphism, two fundamental concepts in Object-Oriented Programming (OOP) in C#. This section helps in understanding how to create hierarchical class structures and leverage polymorphism for more dynamic and flexible code.

## Topics Covered

1. **Inheritance and Base Classes**
   - Learning how to create derived classes that inherit properties and methods from base classes.
   - Example:
     ```csharp
     class Animal {
         public string Name { get; set; }
         public string Sound { get; set; }
         public Animal(string name = "No Name", string sound = "No Sound") {
             Name = name;
             Sound = sound;
         }
     }
     class Dog : Animal {
         public string Sound2 { get; set; } = "Grrr";
     }
     ```

2. **Method Overriding (virtual, override keywords)**
   - Understanding how to override methods in derived classes for customized behavior.
   - Example:
     ```csharp
     class Animal {
         public virtual void MakeSound() {
             Console.WriteLine($"{Name} says {Sound}");
         }
     }
     class Dog : Animal {
         public override void MakeSound() {
             Console.WriteLine($"{Name} says {Sound} and {Sound2}");
         }
     }
     ```

3. **Inner Classes**
   - Exploring the concept of nesting classes within other classes.
   - Example:
     ```csharp
     class Animal {
         public class AnimalHealth {
             public bool HealthyWeight(double weight) {
                 // Weight-check logic here
                 return true;
             }
         }
     }
     ```

4. **Aggregation and Composition**
   - Understanding relationships between objects, such as "has-a" relationships.
   - Example:
     ```csharp
     class Animal {
         public AnimalIDInfo AnimalID { get; set; }
     }
     class AnimalIDInfo {
         public int IDNum { get; set; }
         public string Owner { get; set; }
     }
     ```

5. **Example Classes: `Animal`, `AnimalIDInfo`, `Dog`**
   - `Animal`: A base class representing general characteristics of an animal.
   - `AnimalIDInfo`: A class representing identification information for an animal.
   - `Dog`: A derived class from `Animal` that adds specific characteristics.

## Study Notes

- Pay attention to the inheritance hierarchy and how derived classes extend the functionality of base classes.
- Understand the significance of `virtual` and `override` keywords in method overriding.
- Explore how inner classes can be used for organization and encapsulation within a class.
- Learn about object relationships and how they can be represented in code through aggregation and composition.

## Exercises

1. Create a new derived class from `Animal` and add unique properties or methods.
   ```csharp
    public class Animal
    {
        public string Name { get; set; }
        public int Age { get; set; }

        public void Eat()
        {
            Console.WriteLine($"{Name} is eating.");
        }

        public void Sleep()
        {
            Console.WriteLine($"{Name} is sleeping.");
        }
    }

    public class Dog : Animal
    {
        public string Breed { get; set; }

        public void Bark()
        {
            Console.WriteLine($"{Name} is barking.");
        }

        public void Fetch()
        {
            Console.WriteLine($"{Name} is fetching.");
        }
    }
    ```
2. Override a method in a derived class and demonstrate how it changes the behavior compared to the base class.
   ```csharp
    using System;

    public class Animal
    {
        public virtual void MakeSound()
        {
            Console.WriteLine("The animal makes a sound");
        }
    }

    public class Dog : Animal
    {
        public override void MakeSound()
        {
            Console.WriteLine("The dog barks");
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Animal myAnimal = new Animal();
            Animal myDog = new Dog();

            myAnimal.MakeSound();  // Outputs: "The animal makes a sound"
            myDog.MakeSound();     // Outputs: "The dog barks"
        }
    }
    ```
3. Experiment with creating and using inner classes within a class.
   ```csharp
    public class OuterClass {
        private String outerField = "Outer field";

        class InnerClass {
            private String innerField = "Inner field";

            public void displayFields() {
                System.out.println("Outer Field: " + outerField);
                System.out.println("Inner Field: " + innerField);
            }
        }

        public static void main(String[] args) {
            // Create an instance of the outer class
            OuterClass outer = new OuterClass();

            // Create an instance of the inner class
            OuterClass.InnerClass inner = outer.new InnerClass();

            // Call a method on the inner class
            inner.displayFields();
        }
    }
    ```

---

Inheritance and polymorphism are key to creating extendable and maintainable code in C#. These examples and exercises are designed to provide a practical understanding of these concepts.
