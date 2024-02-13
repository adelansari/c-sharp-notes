# 10_review: More C# stuff

## Overview

The file covers multiple functions you can use to work with lists of data in C#, including Lambda, Where, ToList, Select, Zip, Aggregate, and Average.

## Topics Covered

1. **Lambda Expressions**
   - Lambda expressions allow you to use anonymous methods that define the input parameters on the left and the code to execute on the right.
   - Example:
     ```csharp
     // Delegate that is assigned a Lambda expression
     delegate double doubleIt(double val);
     // Assign a Lambda to the delegate
     doubleIt dblIt = x => x * 2;
     Console.WriteLine($"5 * 2 = {dblIt(5)}");
     ```

2. **Where and ToList**
   - These functions can be used to search through a list and create a new list based on certain conditions.
   - Example:
     ```csharp
     List<int> numList = new List<int> { 1, 9, 2, 6, 3 };
     var evenList = numList.Where(a => a % 2 == 0).ToList();
     ```

3. **Select**
   - Select allows you to execute a function on each item in a list.
   - Example:
     ```csharp
     var oneTo10 = new List<int>();
     oneTo10.AddRange(Enumerable.Range(1, 10));
     var squares = oneTo10.Select(x => x * x);
     ```

4. **Zip**
   - Zip applies a function to two lists.
   - Example:
     ```csharp
     var listOne = new List<int>(new int[] { 1, 3, 4 });
     var listTwo = new List<int>(new int[] { 4, 6, 8 });
     var sumList = listOne.Zip(listTwo, (x, y) => x + y).ToList();
     ```

5. **Aggregate**
   - Aggregate performs an operation on each item in a list and carries the results forward.
   - Example:
     ```csharp
     var numList2 = new List<int>() { 1, 2, 3, 4, 5 };
     Console.WriteLine("Sum : {0}", numList2.Aggregate((a, b) => a + b));
     ```

6. **Average**
   - Get the average of a list of values.
   - Example:
     ```csharp
     var numList3 = new List<int>() { 1, 2, 3, 4, 5 };
     Console.WriteLine("AVG : {0}", numList3.AsQueryable().Average());
     ```

7. **All and Any**
   - These functions determine if all or any items in a list meet a condition.
   - Example:
     ```csharp
     var numList4 = new List<int>() { 1, 2, 3, 4, 5 };
     Console.WriteLine("All > 3 : {0}", numList4.All(x => x > 3));
     Console.WriteLine("Any > 3 : {0}", numList4.Any(x => x > 3));
     ```

8. **Distinct, Except, and Intersect**
   - These functions are used to manipulate lists by eliminating duplicates, returning values not found in the second list, and returning values that both lists have, respectively.
   - Example:
     ```csharp
     var numList6 = new List<int>() { 1, 2, 3, 2, 3 };
     Console.WriteLine("Distinct : {0}", string.Join(", ", numList6.Distinct()));
     var numList7 = new List<int>() { 1, 2, 3, 2, 3 };
     var numList8 = new List<int>() { 3 };
     Console.WriteLine("Except : {0}", string.Join(", ", numList7.Except(numList8)));
     var numList9 = new List<int>() { 1, 2, 3, 2, 3 };
     var numList10 = new List<int>() { 2, 3 };
     Console.WriteLine("Intersect : {0}", string.Join(", ", numList9.Intersect(numList10)));
     ```

## Exercises

1. Create a small project or code snippet that demonstrates your understanding of each of the topics covered.
    ```csharp
    // 1. Lambda Expressions
    Func<int, int> square = x => x * x;
    Console.WriteLine($"Square of 5: {square(5)}");

    // 2. Where and ToList
    List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    List<int> evenNumbers = numbers.Where(x => x % 2 == 0).ToList();
    Console.WriteLine($"Even numbers: {string.Join(", ", evenNumbers)}");

    // 3. Select
    List<int> squares = numbers.Select(x => x * x).ToList();
    Console.WriteLine($"Squares: {string.Join(", ", squares)}");

    // 4. Zip
    List<int> moreNumbers = new List<int> { 11, 12, 13, 14, 15, 16, 17, 18, 19, 20 };
    List<int> sums = numbers.Zip(moreNumbers, (first, second) => first + second).ToList();
    Console.WriteLine($"Sums: {string.Join(", ", sums)}");

    // 5. Aggregate
    int product = numbers.Aggregate((x, y) => x * y);
    Console.WriteLine($"Product: {product}");

    // 6. Average
    double average = numbers.Average();
    Console.WriteLine($"Average: {average}");

    // 7. All and Any
    bool allGreaterThanTen = numbers.All(x => x > 10);
    bool anyGreaterThanTen = numbers.Any(x => x > 10);
    Console.WriteLine($"All greater than 10: {allGreaterThanTen}");
    Console.WriteLine($"Any greater than 10: {anyGreaterThanTen}");

    // 8. Distinct, Except, and Intersect
    List<int> distinctNumbers = numbers.Distinct().ToList();
    List<int> except = numbers.Except(moreNumbers).ToList();
    List<int> intersect = numbers.Intersect(moreNumbers).ToList();
    Console.WriteLine($"Distinct numbers: {string.Join(", ", distinctNumbers)}");
    Console.WriteLine($"Except: {string.Join(", ", except)}");
    Console.WriteLine($"Intersect: {string.Join(", ", intersect)}");

    ```
2. Implement a specific function in a C# application and explain its benefits and use cases.
    ```csharp
    public static int CalculateProduct(List<int> numbers)
    {
        return numbers.Aggregate(1, (total, number) => total * number);
    }
    ```
    This function calculates the product of a list of integers using the `Aggregate` method. It's beneficial because it provides a simple and efficient way to perform a calculation over a sequence of values. It can be used with any binary operation, such as addition, multiplication, or string concatenation. The use of `Aggregate` can make your code more concise and easier to read.

    Use cases for this function could include:

    - Calculating the factorial of a number: The factorial of a number is the product of all positive integers less than or equal to that number. You could generate a list of these integers and then use this function to calculate the factorial.
    - Calculating the product of array elements: In some problems, you might need to calculate the product of all elements in an array or list. This function provides a simple way to do that.

3. Write a program that demonstrates the use of `All` and `Any` methods in C#.
    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;

    class Program
    {
        static void Main(string[] args)
        {
            List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

            bool allGreaterThanTen = numbers.All(x => x > 10);
            bool anyGreaterThanTen = numbers.Any(x => x > 10);

            Console.WriteLine($"All greater than 10: {allGreaterThanTen}");
            Console.WriteLine($"Any greater than 10: {anyGreaterThanTen}");
        }
    }
    ```
    In this program, we create a list of integers and then use the `All` and `Any` methods to check if all or any of the numbers in the list are greater than 10. The output will be `All greater than 10: False` and `Any greater than 10: True`, indicating that not all numbers are greater than 10, but at least one number is.

---