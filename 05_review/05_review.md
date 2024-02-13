# 05_review: Abstract Classes, Interfaces, and Polymorphism in C#

## Overview

The `05_review` folder delves into the concepts of abstract classes, interfaces, and advanced polymorphism in C#. This section is crucial for understanding how to design flexible and reusable code using these advanced OOP features.

## Topics Covered

1. **Abstract Classes and Methods**
   - Understanding the role of abstract classes and methods in defining a contract for subclasses.
   - Example:
     ```csharp
     abstract class Shape {
         public string Name { get; set; }
         public abstract double Area();
     }
     class Circle : Shape {
         public double Radius { get; set; }
         public override double Area() {
             return Math.PI * Radius * Radius;
         }
     }
     ```

2. **Interfaces**
   - Learning how interfaces define a set of methods and properties that implementing classes must adhere to.
   - Example:
     ```csharp
     interface IDrawable {
         void Draw();
     }
     class Circle : Shape, IDrawable {
         public void Draw() {
             // Drawing logic here
         }
     }
     ```

3. **Polymorphism and Overriding Methods**
   - Exploring the use of polymorphism to achieve dynamic method behavior in derived classes.
   - Example:
     ```csharp
     class Shape {
         public virtual void GetInfo() {
             Console.WriteLine("This is a shape.");
         }
     }
     class Circle : Shape {
         public override void GetInfo() {
             base.GetInfo();
             Console.WriteLine("This is a circle.");
         }
     }
     ```

4. **`is` and `as` Keywords, Casting**
   - Understanding how to check the type of objects and cast them to different types.
   - Example:
     ```csharp
     Shape shape = new Circle();
     if (shape is Circle) {
         Circle circle = shape as Circle;
         // Use circle instance
     }
     ```

5. **Example Classes: `Shape`, `Circle`, `Rectangle`**
   - `Shape`: An abstract base class representing general characteristics of a shape.
   - `Circle` and `Rectangle`: Concrete classes derived from `Shape`, implementing specific behaviors.

## Study Notes

- Abstract classes and interfaces are crucial for designing a system where different classes can share a common interface.
- Pay attention to how polymorphism allows for dynamic behavior in class hierarchies.
- Practice using `is` and `as` for type checking and casting, understanding the scenarios where each is appropriate.

## Exercises

1. Create a new interface with a few methods and properties, and implement it in a class.
2. Extend the `Shape` class with a new derived class, implementing the abstract methods.
3. Write a method that takes a `Shape` object and uses type checking and casting to perform specific operations based on the actual type of the shape.

---

Mastering abstract classes, interfaces, and polymorphism is key to building scalable and maintainable applications in C#. Use these concepts to create a solid foundation for your C# programming skills.
