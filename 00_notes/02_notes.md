# 02_review: Object-Oriented Programming in C#

## Overview

This file delves into the core concepts of Object-Oriented Programming (OOP) in C#. It's designed to provide a practical understanding of how OOP principles are applied in C# programming.

## Topics Covered

1. **Class and Object Creation**
   - Understanding the basic structure of a class and how to instantiate it as an object.
   - Example from `Animal.cs`:
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
   - Example from `Animal.cs`:
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
   - Example from `ShapeMath.cs`:
     ```csharp
     class ShapeMath {
         static int numOfShapes = 0;
         public static int GetNumShapes() {
             return numOfShapes;
         }
     }
     ```

4. **Nullable Types and Structs**
   - Understanding the use of nullable types for handling null values.
   - Learning about structs, which are similar to classes but used for smaller and less complex data structures.
   - Example from `Program.cs`:
     ```csharp
     struct Rectangle {
         public double length;
         public double width;
         public double Area() {
             return length * width;
         }
     }
     ```

5. **Example Classes: `Animal`, `ShapeMath`**
   - `Animal`: A basic class to represent an animal with properties like name and sound.
   - `ShapeMath`: A utility class demonstrating static methods.

## Study Notes

- Pay attention to how constructors are used to initialize objects with default or specific values.
- Notice the use of `static` keyword and how it affects the behavior of methods and fields.
- Understand the difference between a class and a struct, and when to use each.

## Exercises

1. Create a new class representing a vehicle, with properties like make, model, and year.
   ```csharp
    class Vehicle {
         public string make;
         public string model;
         public int year;
    }

    Vehicle car = new Vehicle { make = "Toyota", model = "Camry", year = 2020 };
    ```
2. Implement a method in the `Animal` class that prints the animal's details.
    ```csharp
     class Animal {
            public string name;
            public string sound;
            public void PrintDetails() {
                 Console.WriteLine($"Name: {name}, Sound: {sound}");
            }
     }

     Animal cat = new Animal { name = "Whiskers", sound = "Meow" };
     cat.PrintDetails();
     ```
3. Experiment with creating and using structs for simple data types.
   ```csharp
    struct Point {
         public int x;
         public int y;
    }

    Point p1 = new Point();
    p1.x = 10;
    p1.y = 20;

    Point p2 = new Point { x = 5, y = 15 };

    Console.WriteLine($"Point 1: ({p1.x}, {p1.y})");
    ```

---