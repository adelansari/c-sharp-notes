# 01_review: C# Fundamentals with Examples

## Overview
This file contains simple C# examples showcasing fundamental programming concepts. Use it as a quick reference or if you're new to C#.

## Concepts Covered

* **Comments:** Used to explain your code (lines starting with `//` or enclosed in `/* */`).
* **Namespaces:** Help organize code into logical groups (e.g., `using System;`)
* **Classes:** Blueprints for defining objects (e.g., `public class Program`).
* **Functions (Methods):** Blocks of code performing specific tasks (e.g., `static void SayHello()`).
* **Variables:** Containers for storing data (e.g., `string name = "Derek";`).
* **Data Types:**
    * **Integers:** Whole numbers (e.g., `int`, `long`, `byte`).
    * **Floating-Point:** Numbers with decimals (e.g., `float`, `double`, `decimal`).
    * **Booleans:** True or false (e.g., `bool`).
    * **Strings:** Sequences of characters (e.g., `string`).
* **Console Input/Output:** Receiving user input (`Console.ReadLine()`) and display output (`Console.WriteLine()`)
* **Operators:**
    * **Arithmetic:** `+`, `-`, `*`, `/`, `%` (modulus).
    * **Comparison:** `>`, `<`, `>=`, `<=`, `==`, `!=`.
    * **Logical:** `&&` (and), `||` (or), `!` (not).
* **Conditional Statements:** Make decisions based on conditions.
    * **if / else if / else** 
* **Loops:** Repeat code blocks.
    * **while** – Executes as long as its condition is true.
    * **do-while** – Executes at least once before checking the condition.
* **Arrays:** Collections of items of the same data type (e.g., `int[] favNums = new int[3];`).
* **Exception Handling:**  Catch and manage errors with `try`, `catch`, and `finally`.
* **String Manipulation** (Using `StringBuilder` for efficiency).
* **Passing Values:**
    * **Pass by Value** 
    * **Pass by Reference** (using `ref`)
    * **Output Parameters** (using `out`)
    * **Variable Number of Arguments** (using `params`)
* **Functions (Methods):** Reusable blocks of code (e.g., `static double GetSum(double x, double y)`).
* **Method Overloading:**  Multiple functions with the same name but different arguments.
* **Enums:** Custom data types representing fixed values (e.g., `enum CarColor { Orange, Blue, Green }`).


## Topics Covered

1. **Basic Syntax and Structure**
   - Understanding the basic structure of a C# program, including namespaces, classes, and methods.
   - Example:
     ```csharp
     using System;
     namespace HelloWorld {
         class Program {
             static void Main(string[] args) {
                 Console.WriteLine("Hello, World!");
             }
         }
     }
     ```

2. **Variables and Data Types**
   - Learning about different data types in C# and how to use variables to store information.
   - Example:
     ```csharp
     int number = 10;
     string text = "Sample Text";
     bool isTrue = true;
     ```

3. **Control Structures**
   - Exploring control structures such as if-else statements, loops (for, while, do-while), and switch statements.
   - Example:
     ```csharp
     for (int i = 0; i < 5; i++) {
         Console.WriteLine(i);
     }
     ```

4. **Basic Input and Output**
   - Understanding how to read input from the user and display output to the console.
   - Example:
     ```csharp
     Console.WriteLine("Enter your name:");
     string name = Console.ReadLine();
     Console.WriteLine($"Hello, {name}!");
     ```

5. **Arrays and Collections**
   - Learning how to use arrays and basic collections to store multiple values.
   - Example:
     ```csharp
     int[] numbers = new int[5] { 1, 2, 3, 4, 5 };
     foreach (int number in numbers) {
         Console.WriteLine(number);
     }
     ```

6. **Basic Error Handling**
   - Introduction to error handling using try-catch blocks.
   - Example:
     ```csharp
     try {
         // Code that may cause an exception
     }
     catch (Exception ex) {
         Console.WriteLine($"Error: {ex.Message}");
     }
     ```

## Study Notes

- Start with understanding the basic syntax and structure of a C# program.
- Practice with different data types and control structures to get comfortable with C# programming.
- Experiment with arrays and collections to understand how to work with multiple data items.
- Get familiar with basic input/output operations and simple error handling techniques.


---

## Examples

```csharp
// Variables Example
int age = 17;
string name = "Alice";

// Conditional Example
if (age >= 18) {
    Console.WriteLine("You can vote!");
}

// Loop Example
for (int i = 0; i < 5; i++) {
    Console.WriteLine(i);
}

// Function Example
static void PrintHello() {
    Console.WriteLine("Hello C#!"); 
}
PrintHello();  // Calling the function
```
---

## Exercises

1. Write a simple C# program that takes user input and performs basic calculations.
    ```csharp
    using System;

    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Enter the first number: ");
            double num1 = Convert.ToDouble(Console.ReadLine());

            Console.Write("Enter the second number: ");
            double num2 = Convert.ToDouble(Console.ReadLine());

            double sum = num1 + num2;
            double difference = num1 - num2;
            double product = num1 * num2;
            double quotient = num1 / num2;

            Console.WriteLine("Sum: " + sum);
            Console.WriteLine("Difference: " + difference);
            Console.WriteLine("Product: " + product);
            Console.WriteLine("Quotient: " + quotient);
        }
    }
    ```

2. Create a program that uses different types of loops to iterate over arrays or collections.
   ```csharp
    public class Main {
        public static void main(String[] args) {
            int[] array = {1, 2, 3, 4, 5};

            // Using for loop
            System.out.println("Using for loop:");
            for(int i = 0; i < array.length; i++) {
                System.out.println(array[i]);
            }

            // Using enhanced for loop (also known as for-each loop)
            System.out.println("\nUsing enhanced for loop:");
            for(int num : array) {
                System.out.println(num);
            }

            // Using while loop
            System.out.println("\nUsing while loop:");
            int i = 0;
            while(i < array.length) {
                System.out.println(array[i]);
                i++;
            }

            // Using do-while loop
            System.out.println("\nUsing do-while loop:");
            i = 0;
            do {
                System.out.println(array[i]);
                i++;
            } while(i < array.length);
        }
    }
    ```
3. Experiment with if-else and switch statements to handle different conditions in a program.
   ```csharp
    using System;

    class Program {
        static void Main(string[] args) {
            int number = 5;

            if (number > 0) {
                Console.WriteLine("The number is positive.");
            }
            else if (number < 0) {
                Console.WriteLine("The number is negative.");
            }
            else {
                Console.WriteLine("The number is zero.");
            }

            char grade = 'B';
            switch (grade) {
                case 'A':
                    Console.WriteLine("Excellent!");
                    break;
                case 'B':
                    Console.WriteLine("Good job!");
                    break;
                case 'C':
                    Console.WriteLine("You can do better.");
                    break;
                default:
                    Console.WriteLine("Invalid grade.");
                    break;
            }
        }
    }
    ```
4. Try adding basic error handling to your programs to manage potential runtime errors.
   ```csharp
    using System;

    class Program {
        static void Main(string[] args) {
            try {
                int[] numbers = { 1, 2, 3 };
                Console.WriteLine(numbers[3]);  // Accessing an out-of-bounds index
            }
            catch (IndexOutOfRangeException ex) {
                Console.WriteLine($"Error: {ex.Message}");
            }
        }
    }
    ```