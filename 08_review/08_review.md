# 08_review: Advanced C# Programming Concepts

## Overview

The `08_review` folder is designed to explore advanced C# programming concepts. This section is ideal for deepening your understanding of complex C# features and programming techniques that are essential for high-level software development.

## Topics Covered

1. **Advanced Data Structures**
   - Exploring the use of advanced data structures like dictionaries, queues, stacks, and hash sets.
   - Example:
     ```csharp
     Dictionary<int, string> users = new Dictionary<int, string>();
     users.Add(1, "Alice");
     users.Add(2, "Bob");
     // Accessing elements
     string userName = users[1];
     ```

2. **Delegates and Events**
   - Understanding the use of delegates for creating customizable method references and events for handling notifications.
   - Example:
     ```csharp
     delegate void Notify();  // Delegate
     class ProcessBusinessLogic {
         public event Notify ProcessCompleted; // Event
         public void StartProcess() {
             // Process logic here
             OnProcessCompleted();
         }
         protected virtual void OnProcessCompleted() {
             ProcessCompleted?.Invoke();
         }
     }
     ```

3. **LINQ (Language Integrated Query)**
   - Learning how to use LINQ for more efficient data querying and manipulation.
   - Example:
     ```csharp
     List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
     var evenNumbers = numbers.Where(n => n % 2 == 0);
     foreach (var n in evenNumbers) {
         Console.WriteLine(n);
     }
     ```

4. **Asynchronous Programming**
   - Exploring asynchronous programming patterns in C# to improve application performance and responsiveness.
   - Example:
     ```csharp
     async Task LongRunningOperation() {
         await Task.Delay(1000);  // Simulate a long-running task
         Console.WriteLine("Operation Completed");
     }
     ```

5. **Reflection and Attributes**
   - Understanding how to use reflection for inspecting and interacting with object types, and attributes for adding metadata to code.
   - Example:
     ```csharp
     [Serializable]
     class MyClass {
         public int MyProperty { get; set; }
     }
     // Using reflection
     var myClassType = typeof(MyClass);
     var isSerializable = myClassType.IsDefined(typeof(SerializableAttribute), false);
     ```

## Study Notes

- Advanced data structures are crucial for efficient data storage and retrieval.
- Delegates and events are key to creating flexible and loosely-coupled applications.
- LINQ provides a powerful and concise way to query and manipulate data.
- Asynchronous programming is essential for developing responsive applications.
- Reflection and attributes offer advanced capabilities for type inspection and metadata processing.

## Exercises

1. Implement a complex data structure and perform various operations like adding, removing, and searching elements.
   ```csharp
    public class Node
    {
        public int Value { get; set; }
        public Node Left { get; set; }
        public Node Right { get; set; }

        public Node(int value)
        {
            Value = value;
        }
    }

    public class BST
    {
        public Node Root { get; private set; }

        public void Insert(int value)
        {
            var node = new Node(value);
            if (Root == null)
            {
                Root = node;
            }
            else
            {
                Node current = Root;
                Node parent = null;
                while (true)
                {
                    parent = current;
                    if (value < current.Value)
                    {
                        current = current.Left;
                        if (current == null)
                        {
                            parent.Left = node;
                            return;
                        }
                    }
                    else
                    {
                        current = current.Right;
                        if (current == null)
                        {
                            parent.Right = node;
                            return;
                        }
                    }
                }
            }
        }

        public bool Search(int value)
        {
            Node current = Root;
            while (current != null)
            {
                if (value < current.Value)
                    current = current.Left;
                else if (value > current.Value)
                    current = current.Right;
                else
                    return true;
            }
            return false;
        }

        // Note: This is a simplified version of the delete operation. It only works correctly for nodes with 0 or 1 child.
        public void Delete(int value)
        {
            Root = DeleteRecursive(Root, value);
        }

        private Node DeleteRecursive(Node root, int value)
        {
            if (root == null)
                return root;

            if (value < root.Value)
                root.Left = DeleteRecursive(root.Left, value);
            else if (value > root.Value)
                root.Right = DeleteRecursive(root.Right, value);
            else
            {
                if (root.Left == null)
                    return root.Right;
                else if (root.Right == null)
                    return root.Left;
            }

            return root;
        }
    }
    ```
2. Create a simple event system using delegates and events, and simulate event handling.
   ```csharp

    public class EventPublisher
    {
        public delegate void EventHandler(string message);
        public event EventHandler EventOccurred;

        public void SimulateEvent()
        {
            EventOccurred?.Invoke("Event occurred!");
        }
    }

    public class EventSubscriber
    {
        public void HandleEvent(string message)
        {
            Console.WriteLine("Event handled: " + message);
        }
    }

    EventPublisher publisher = new EventPublisher();
    EventSubscriber subscriber = new EventSubscriber();

    publisher.EventOccurred += subscriber.HandleEvent;
    publisher.SimulateEvent();  // Outputs: "Event handled: Event occurred!"
    ```

    Another example:
    ```csharp
    public class Notifier
    {
        // Declare a delegate
        public delegate void NotifyEventHandler(object sender, EventArgs e);

        // Declare an event of the delegate type
        public event NotifyEventHandler Notify;

        public void TriggerEvent()
        {
            // Trigger the event
            Notify?.Invoke(this, EventArgs.Empty);
        }
    }

    public class Listener
    {
        public void Subscribe(Notifier notifier)
        {
            // Subscribe to the event
            notifier.Notify += HandleEvent;
        }

        private void HandleEvent(object sender, EventArgs e)
        {
            // Handle the event
            Console.WriteLine("Event received!");
        }
    }

    Notifier notifier = new Notifier();
    Listener listener = new Listener();

    // The listener subscribes to the notifier's event
    listener.Subscribe(notifier);

    // The notifier triggers the event
    notifier.TriggerEvent();  // Outputs: "Event received!"
    ```
3. Write a LINQ query to filter and process a collection of objects.
   ```csharp
    List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
    var evenNumbers = numbers.Where(n => n % 2 == 0);
    foreach (var n in evenNumbers)
    {
        Console.WriteLine(n);
    }
    ```
    Another Example:
    ```csharp
    public class Product
    {
        public string Name { get; set; }
        public decimal Price { get; set; }
    }

    List<Product> products = new List<Product>
    {
        new Product { Name = "Apple", Price = 1.25m },
        new Product { Name = "Banana", Price = 0.33m },
        new Product { Name = "Cherry", Price = 2.00m },
        new Product { Name = "Date", Price = 1.75m },
    };

    // LINQ query to filter and process the products
    var expensiveProducts = from p in products
                            where p.Price > 1.50m
                            select p.Name;

    // Print the names of the expensive products
    foreach (var name in expensiveProducts)
    {
        Console.WriteLine(name);
    }
    ```
4. Create an asynchronous method and demonstrate how it improves application responsiveness.
   ```csharp
    public class Program
    {
        static async Task Main(string[] args)
        {
            Console.WriteLine("Starting download...");

            // Call the asynchronous method
            await DownloadDataAsync();

            Console.WriteLine("Download complete. You can interact with the application while data was downloading.");
        }

        static async Task DownloadDataAsync()
        {
            // Simulate a long-running operation
            await Task.Delay(5000);
        }
    }
    ```
5. Use reflection to inspect the properties and methods of a class, and use attributes to add custom metadata to a class or method.
   ```csharp
   // Define a custom attribute
    public class CustomAttribute : Attribute
    {
        public string Description { get; set; }

        public CustomAttribute(string description)
        {
            Description = description;
        }
    }

    // Apply the custom attribute to a class and its members
    [Custom("This is a test class")]
    public class TestClass
    {
        [Custom("This is a test property")]
        public string TestProperty { get; set; }

        [Custom("This is a test method")]
        public void TestMethod() { }
    }

    public class Program
    {
        static void Main(string[] args)
        {
            // Get the Type object representing TestClass
            Type testClassType = typeof(TestClass);

            // Use reflection to inspect the custom attributes of the class
            var classAttributes = testClassType.GetCustomAttributes(typeof(CustomAttribute), false);
            foreach (CustomAttribute attr in classAttributes)
            {
                Console.WriteLine($"Class description: {attr.Description}");
            }

            // Use reflection to inspect the properties of the class
            PropertyInfo[] properties = testClassType.GetProperties();
            foreach (PropertyInfo property in properties)
            {
                Console.WriteLine($"Property name: {property.Name}");

                var propertyAttributes = property.GetCustomAttributes(typeof(CustomAttribute), false);
                foreach (CustomAttribute attr in propertyAttributes)
                {
                    Console.WriteLine($"Property description: {attr.Description}");
                }
            }

            // Use reflection to inspect the methods of the class
            MethodInfo[] methods = testClassType.GetMethods();
            foreach (MethodInfo method in methods)
            {
                Console.WriteLine($"Method name: {method.Name}");

                var methodAttributes = method.GetCustomAttributes(typeof(CustomAttribute), false);
                foreach (CustomAttribute attr in methodAttributes)
                {
                    Console.WriteLine($"Method description: {attr.Description}");
                }
            }
        }
    }
   ```

---