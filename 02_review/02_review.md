# 02_review: Object-Oriented Programming in C#

## Overview

This folder delves into the core concepts of Object-Oriented Programming (OOP) in C#. It's designed to provide a practical understanding of how OOP principles are applied in C# programming.

## Topics Covered

1. **Class and Object Creation**
   - Understanding the basic structure of a class and how to instantiate it as an object.
   - Example:
     ```csharp
     class Animal {
         public string name;
         public string sound;
         public Animal() {
             name = "No Name";
             sound = "No Sound";
         }
     }
     Animal cat = new Animal();
     ```

2. **Constructors**
   - Exploring how constructors are used to initialize objects.
   - Example:
     ```csharp
     class Animal {
         public Animal(string name = "No Name", string sound = "No Sound") {
             this.name = name;
             this.sound = sound;
         }
     }
     Animal dog = new Animal("Rover", "Woof");
     ```

3. **Static Methods and Fields**
   - Learning about static members of a class and their shared nature across all instances.
   - Example:
     ```csharp
     class Animal {
         static int numOfAnimals = 0;
         public static int GetNumAnimals() {
             return numOfAnimals;
         }
     }
     ```

4. **Basic Principles of OOP**
   - Encapsulation: Keeping the internal state of an object hidden from the outside.
   - Inheritance: Creating new classes that inherit properties and methods from existing classes.
   - Polymorphism: Allowing methods to do different things based on the object they are acting upon.

5. **Nullable Types and Structs**
   - Understanding the use of nullable types for handling null values.
   - Learning about structs, which are similar to classes but used for smaller and less complex data structures.
   - Example:
     ```csharp
     struct Rectangle {
         public double length;
         public double width;
         public double Area() {
             return length * width;
         }
     }
     ```

6. **Example Classes: `Animal`, `ShapeMath`**
   - `Animal`: A basic class to represent an animal with properties like name and sound.
   - `ShapeMath`: A utility class demonstrating static methods.

## Study Notes

- Pay attention to how constructors are used to initialize objects with default or specific values.
- Notice the use of `static` keyword and how it affects the behavior of methods and fields.
- Understand the difference between a class and a struct, and when to use each.
- Explore the basic principles of OOP and how they are implemented in C#.

## Exercises

1. Create a new class representing a vehicle, with properties like make, model, and year.
2. Implement a method in the `Animal` class that prints the animal's details.
3. Experiment with creating and using structs for simple data types.

---

Remember, the key to mastering OOP in C# is practice and experimentation. Use these examples as a starting point and try to build your own classes and objects.
