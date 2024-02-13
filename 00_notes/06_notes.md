# 06_review: Interfaces and Design Patterns in C#

## Overview

The file focuses on the use of interfaces and the implementation of design patterns in C#. This section is essential for understanding how to create modular, reusable, and maintainable code structures in professional software development.

## Topics Covered

1. **Interfaces**
   - Exploring the concept of interfaces as contracts for classes, defining a set of methods and properties that implementing classes must provide.
   - Example:
     ```csharp
     interface IDrivable {
         void Drive();
         void Stop();
     }
     class Car : IDrivable {
         public void Drive() {
             // Driving logic
         }
         public void Stop() {
             // Stop logic
         }
     }
     ```

2. **Design Patterns: Command Pattern**
   - Understanding the command pattern, which encapsulates a request as an object, thereby allowing for parameterization of clients with queues, requests, and operations.
   - Example:
     ```csharp
     interface ICommand {
         void Execute();
     }
     class LightOnCommand : ICommand {
         public void Execute() {
             // Turn on the light
         }
     }
     class RemoteControl {
         public void Submit(ICommand command) {
             command.Execute();
         }
     }
     ```

3. **Example Interfaces: `ICommand`, `IDrivable`, `IElectronicDevice`**
   - `ICommand`: An interface representing a command in the command pattern.
   - `IDrivable`: An interface representing the drivable behavior of a vehicle.
   - `IElectronicDevice`: An interface representing operations for an electronic device.

## Study Notes

- Interfaces are a powerful way to define capabilities that different classes can implement, promoting a loose coupling between classes.
- The command pattern is an excellent example of encapsulating method invocation, requests, or operations into separate objects, providing additional layers of abstraction and flexibility.
- Practice implementing interfaces in various classes and see how they enforce a contract for the class's behavior.

## Exercises

1. Create a new interface and implement it in multiple classes, observing how it enforces a consistent structure across different implementations.
   ```csharp
    public interface IShape
    {
        double CalculateArea();
    }

    public class Circle : IShape
    {
        public double Radius { get; set; }

        public Circle(double radius)
        {
            Radius = radius;
        }

        public double CalculateArea()
        {
            return Math.PI * Math.Pow(Radius, 2);
        }
    }

    public class Square : IShape
    {
        public double Side { get; set; }

        public Square(double side)
        {
            Side = side;
        }

        public double CalculateArea()
        {
            return Math.Pow(Side, 2);
        }
    }

    public class Rectangle : IShape
    {
        public double Width { get; set; }
        public double Height { get; set; }

        public Rectangle(double width, double height)
        {
            Width = width;
            Height = height;
        }

        public double CalculateArea()
        {
            return Width * Height;
        }
    }
    ```
2. Implement a simple version of the command pattern with a few commands and a command invoker.
   ```csharp
    public interface ICommand
    {
        void Execute();
    }

    public class StartCommand : ICommand
    {
        public void Execute()
        {
            Console.WriteLine("Start command executed");
        }
    }

    public class StopCommand : ICommand
    {
        public void Execute()
        {
            Console.WriteLine("Stop command executed");
        }
    }

    public class CommandInvoker
    {
        private ICommand _command;

        public void SetCommand(ICommand command)
        {
            _command = command;
        }

        public void Invoke()
        {
            _command.Execute();
        }
    }


    CommandInvoker invoker = new CommandInvoker();
    invoker.SetCommand(new StartCommand());
    invoker.Invoke();  // Outputs: "Start command executed"

    invoker.SetCommand(new StopCommand());
    invoker.Invoke();  // Outputs: "Stop command executed"
    ```
3. Explore creating an interface for a common behavior (like `IChargeable` for charging devices) and implement it in different classes.
   ```csharp
    public interface IChargeable
    {
        void Charge();
    }

    public class Phone : IChargeable
    {
        public void Charge()
        {
            Console.WriteLine("Charging the phone");
        }
    }

    public class Laptop : IChargeable
    {
        public void Charge()
        {
            Console.WriteLine("Charging the laptop");
        }
    }
    ```
4. Create a simple example of the factory pattern, where a factory class creates instances of different classes based on a parameter.
   ```csharp
    public interface IShape
    {
        void Draw();
    }

    public class Circle : IShape
    {
        public void Draw()
        {
            Console.WriteLine("Drawing a circle");
        }
    }

    public class Square : IShape
    {
        public void Draw()
        {
            Console.WriteLine("Drawing a square");
        }
    }

    public class ShapeFactory
    {
        public IShape GetShape(string shapeType)
        {
            if (shapeType == "circle")
            {
                return new Circle();
            }
            else if (shapeType == "square")
            {
                return new Square();
            }
            return null;
        }
    }

    ShapeFactory factory = new ShapeFactory();
    IShape circle = factory.GetShape("circle");
    circle.Draw();  // Outputs: "Drawing a circle"

    IShape square = factory.GetShape("square");
    square.Draw();  // Outputs: "Drawing a square"
    ```
5. Research and implement the observer pattern in C# to create a simple event handling system.
   ```csharp
    public interface IObserver
    {
        void Update(string message);
    }

    public class MessagePublisher
    {
        private List<IObserver> _observers = new List<IObserver>();

        public void Subscribe(IObserver observer)
        {
            _observers.Add(observer);
        }

        public void Unsubscribe(IObserver observer)
        {
            _observers.Remove(observer);
        }

        public void Notify(string message)
        {
            foreach (var observer in _observers)
            {
                observer.Update(message);
            }
        }
    }

    public class MessageSubscriber : IObserver
    {
        public void Update(string message)
        {
            Console.WriteLine("Received message: " + message);
        }
    }

    MessagePublisher publisher = new MessagePublisher();
    MessageSubscriber subscriber1 = new MessageSubscriber();
    MessageSubscriber subscriber2 = new MessageSubscriber();

    publisher.Subscribe(subscriber1);
    publisher.Subscribe(subscriber2);

    publisher.Notify("Hello, observers!");
    // Outputs:
    // Received message: Hello, observers!
    // Received message: Hello, observers!
    ```
6. Create a simple example of the adapter pattern, where a class adapts to a different interface.
   ```csharp
    public interface ITarget
    {
        void Request();
    }

    public class Adaptee
    {
        public void SpecificRequest()
        {
            Console.WriteLine("Adaptee's specific request");
        }
    }

    public class Adapter : ITarget
    {
        private Adaptee _adaptee;

        public Adapter(Adaptee adaptee)
        {
            _adaptee = adaptee;
        }

        public void Request()
        {
            _adaptee.SpecificRequest();
        }
    }

    Adaptee adaptee = new Adaptee();
    ITarget target = new Adapter(adaptee);
    target.Request();  // Outputs: "Adaptee's specific request"
    ```
7. Research and implement the decorator pattern in C# to add new functionality to an existing class without altering its structure.
    ```csharp
     public interface IComponent
     {
          string Operation();
     }
    
     public class ConcreteComponent : IComponent
     {
          public string Operation()
          {
                return "ConcreteComponent";
          }
     }
    
     public abstract class Decorator : IComponent
     {
          protected IComponent _component;
    
          public Decorator(IComponent component)
          {
                _component = component;
          }
    
          public virtual string Operation()
          {
                return _component.Operation();
          }
     }
    
     public class ConcreteDecoratorA : Decorator
     {
          public ConcreteDecoratorA(IComponent component) : base(component) { }
    
          public override string Operation()
          {
                return $"ConcreteDecoratorA({base.Operation()})";
          }
     }
    
     public class ConcreteDecoratorB : Decorator
     {
          public ConcreteDecoratorB(IComponent component) : base(component) { }
    
          public override string Operation()
          {
                return $"ConcreteDecoratorB({base.Operation()})";
          }
     }
    
     IComponent component = new ConcreteComponent();
     Console.WriteLine(component.Operation());  // Outputs: "ConcreteComponent"
    
     IComponent decoratedComponentA = new ConcreteDecoratorA(component);
     Console.WriteLine(decoratedComponentA.Operation());  // Outputs: "ConcreteDecoratorA(ConcreteComponent)"
    
     IComponent decoratedComponentB = new ConcreteDecoratorB(decoratedComponentA);
     Console.WriteLine(decoratedComponentB.Operation());  // Outputs: "ConcreteDecoratorB(ConcreteDecoratorA(ConcreteComponent))"
     ```
8. Create a simple example of the strategy pattern, where a class can change its behavior at runtime by implementing different strategies.
   ```csharp
    public interface IStrategy
    {
        void Execute();
    }

    public class ConcreteStrategyA : IStrategy
    {
        public void Execute()
        {
            Console.WriteLine("Executing strategy A");
        }
    }

    public class ConcreteStrategyB : IStrategy
    {
        public void Execute()
        {
            Console.WriteLine("Executing strategy B");
        }
    }

    public class Context
    {
        private IStrategy _strategy;

        public void SetStrategy(IStrategy strategy)
        {
            _strategy = strategy;
        }

        public void ExecuteStrategy()
        {
            _strategy.Execute();
        }
    }

    Context context = new Context();
    context.SetStrategy(new ConcreteStrategyA());
    context.ExecuteStrategy();  // Outputs: "Executing strategy A"

    context.SetStrategy(new ConcreteStrategyB());
    context.ExecuteStrategy();  // Outputs: "Executing strategy B"
    ```

---