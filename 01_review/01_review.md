**C# Fundamentals with Examples**

This file contains simple C# examples showcasing fundamental programming concepts. Use it as a quick reference or if you're new to C#.

**Concepts Covered:**

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


**Examples**

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
