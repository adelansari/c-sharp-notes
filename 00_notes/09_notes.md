# 09_review: Exploring Advanced Features and Techniques in C#

## Overview

The file is dedicated to exploring a range of advanced features and techniques in C#. This section is designed for those who are already familiar with the basics and intermediate aspects of C# and are looking to further enhance their skills with more complex and powerful features of the language.

## Topics Covered

1. **Exception Handling and Debugging**
   - Mastering the art of handling runtime errors gracefully using try-catch blocks and understanding the debugging process in C#.
   - Example:
     ```csharp
     try {
         // Code that may throw an exception
     }
     catch (Exception ex) {
         Console.WriteLine($"Error: {ex.Message}");
     }
     ```

2. **Advanced File Operations**
   - Learning to perform advanced file operations, including reading, writing, and manipulating file data efficiently.
   - Example:
     ```csharp
     string filePath = @"C:\example.txt";
     string fileContent = File.ReadAllText(filePath);
     Console.WriteLine(fileContent);
     ```

3. **Multithreading and Concurrency**
   - Exploring the concepts of multithreading and concurrency to improve the performance of applications by executing multiple operations simultaneously.
   - Example:
     ```csharp
     Thread thread = new Thread(new ThreadStart(DoWork));
     thread.Start();
     void DoWork() {
         // Thread's work here
     }
     ```

4. **Advanced Data Manipulation**
   - Delving into more complex data manipulation techniques, including working with JSON, XML, and utilizing serialization and deserialization.
   - Example:
     ```csharp
     using System.Text.Json;
     string jsonString = JsonSerializer.Serialize(myObject);
     MyObject obj = JsonSerializer.Deserialize<MyObject>(jsonString);
     ```

5. **Design Patterns and Best Practices**
   - Understanding various design patterns and best practices in C# to write clean, maintainable, and efficient code.
   - Example:
     ```csharp
     // Singleton pattern example
     public class Singleton {
         private static Singleton instance;
         private Singleton() {}
         public static Singleton Instance {
             get {
                 if (instance == null) {
                     instance = new Singleton();
                 }
                 return instance;
             }
         }
     }
     ```

## Study Notes

- Exception handling is crucial for building robust applications that can handle unexpected situations gracefully.
- Advanced file operations are essential for applications that need to interact with the file system.
- Multithreading and concurrency are key to improving the performance of applications that perform multiple operations or tasks.
- Understanding serialization and data manipulation techniques is important for working with various data formats.
- Familiarity with design patterns and best practices is essential for writing high-quality, professional-grade C# code.

## Exercises

1. Write a program that demonstrates the use of multiple try-catch blocks for different exception types.
   ```csharp
   public class Program
    {
        public static void Main(string[] args)
        {
            try
            {
                Console.WriteLine("Enter a number:");
                int num = int.Parse(Console.ReadLine());

                Console.WriteLine("Enter a divisor:");
                int divisor = int.Parse(Console.ReadLine());

                int result = num / divisor;
                Console.WriteLine($"The result is {result}");
            }
            catch (DivideByZeroException)
            {
                Console.WriteLine("Error: Division by zero is not allowed.");
            }
            catch (FormatException)
            {
                Console.WriteLine("Error: The input was not a valid number.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error: {ex.Message}");
            }
        }
    }
   ```
2. Create a file manipulation utility that performs various operations like reading, writing, and searching within files.
   ```csharp
   using System;
    using System.IO;
    using System.Linq;

    public class FileUtility
    {
        public string ReadFromFile(string filePath)
        {
            try
            {
                return File.ReadAllText(filePath);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error reading from file: {ex.Message}");
                return null;
            }
        }

        public void WriteToFile(string filePath, string content)
        {
            try
            {
                File.WriteAllText(filePath, content);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error writing to file: {ex.Message}");
            }
        }

        public bool SearchInFile(string filePath, string searchTerm)
        {
            try
            {
                string content = File.ReadAllText(filePath);
                return content.Contains(searchTerm);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error searching in file: {ex.Message}");
                return false;
            }
        }
    }

    FileUtility fileUtility = new FileUtility();

    // Write to a file
    fileUtility.WriteToFile("test.txt", "Hello, world!");

    // Read from a file
    string content = fileUtility.ReadFromFile("test.txt");
    Console.WriteLine(content);  // Outputs: "Hello, world!"

    // Search in a file
    bool found = fileUtility.SearchInFile("test.txt", "world");
    Console.WriteLine(found);  // Outputs: "True"
   ```
3. Implement a simple multithreading application that performs several tasks in parallel.
    ```csharp
    using System;
     using System.Threading;
    
     public class Program
     {
          public static void Main(string[] args)
          {
                Thread thread1 = new Thread(new ThreadStart(DoWork1));
                Thread thread2 = new Thread(new ThreadStart(DoWork2));
    
                thread1.Start();
                thread2.Start();
    
                Console.WriteLine("Main thread is done.");
          }
    
          static void DoWork1()
          {
                Console.WriteLine("Thread 1 is working...");
                Thread.Sleep(2000);
                Console.WriteLine("Thread 1 is done.");
          }
    
          static void DoWork2()
          {
                Console.WriteLine("Thread 2 is working...");
                Thread.Sleep(3000);
                Console.WriteLine("Thread 2 is done.");
          }
     }
    
    ```
   Another example:
    ```csharp
    using System;
    using System.Threading.Tasks;

    public class Program
    {
        public static void Main(string[] args)
        {
            // Define the tasks
            Task task1 = Task.Run(() => DoWork("Task 1"));
            Task task2 = Task.Run(() => DoWork("Task 2"));
            Task task3 = Task.Run(() => DoWork("Task 3"));

            // Wait for all tasks to complete
            Task.WaitAll(task1, task2, task3);

            Console.WriteLine("All tasks completed.");
        }

        public static void DoWork(string taskName)
        {
            for (int i = 0; i < 5; i++)
            {
                Console.WriteLine($"{taskName} is working...");
                Task.Delay(1000).Wait();  // Simulate work with a delay
            }
        }
    }
    ```
    
4. Write a program that serializes and deserializes an object to and from JSON.
   ```csharp
   using System;
    using System.Text.Json;

    public class Person
    {
        public string Name { get; set; }
        public int Age { get; set; }
    }

    public class Program
    {
        public static void Main(string[] args)
        {
            // Create a Person object
            Person person = new Person { Name = "John Doe", Age = 30 };

            // Serialize the Person object to a JSON string
            string jsonString = JsonSerializer.Serialize(person);
            Console.WriteLine(jsonString);  // Outputs: {"Name":"John Doe","Age":30}

            // Deserialize the JSON string back to a Person object
            Person deserializedPerson = JsonSerializer.Deserialize<Person>(jsonString);
            Console.WriteLine($"{deserializedPerson.Name}, {deserializedPerson.Age}");  // Outputs: John Doe, 30
        }
    }
   ```
   Another example:
   ```csharp
    using System;
     using System.Text.Json;
    
     public class Program
     {
          public static void Main(string[] args)
          {
                // Serialize an object to JSON
                MyObject myObject = new MyObject { Name = "John", Age = 30 };
                string jsonString = JsonSerializer.Serialize(myObject);
                Console.WriteLine(jsonString);  // Outputs: {"Name":"John","Age":30}
    
                // Deserialize JSON to an object
                MyObject obj = JsonSerializer.Deserialize<MyObject>(jsonString);
                Console.WriteLine(obj.Name);  // Outputs: "John"
                Console.WriteLine(obj.Age);   // Outputs: 30
          }
     }
    
     public class MyObject
     {
          public string Name { get; set; }
          public int Age { get; set; }
     }
    ```
5. Implement a design pattern of your choice in a small application or module.
   ```csharp
    // Singleton pattern example
     public class Singleton
     {
          private static Singleton instance;
          private Singleton() { }
    
          public static Singleton Instance
          {
                get
                {
                 if (instance == null)
                 {
                      instance = new Singleton();
                 }
                 return instance;
                }
          }
     }
    ```
    Another example:
    ```csharp
    public class Singleton
    {
        // Static variable that holds the single instance of the class
        private static Singleton instance;

        // Private constructor to prevent instantiation of the class from outside
        private Singleton() { }

        // Public method that returns the single instance of the class
        public static Singleton GetInstance()
        {
            // If the instance is null, create a new instance
            if (instance == null)
            {
                instance = new Singleton();
            }

            // Return the single instance of the class
            return instance;
        }
    }

    public class Program
    {
        public static void Main(string[] args)
        {
            // Get the single instance of the Singleton class
            Singleton singleton = Singleton.GetInstance();

            // The same instance will be returned every time GetInstance is called
            Singleton sameSingleton = Singleton.GetInstance();

            Console.WriteLine(object.ReferenceEquals(singleton, sameSingleton));  // Outputs: "True"
        }
    }
    ```

---