# C# Notes

## Keywords
* namespace - 
* class - 
* public - An **Access Modifier** that allows the member to be accessed from outside the class
* private - Default **Access Modifier** that only allows the member to be accessed from within the class
* void - Applied to methods that do not return a value
* new - 
* static - Can be applied to fields or methods that can be accessed in code without an instance of the class. (Console.WriteLine)
* internal - Class that is only accessable from the same assembly
* ref - passes a reference of the variable instead of "by value" (pointer of a pointer)
  * Calling method must specify ref AND the method itself must specify ref
* out - Similar to ref, but must provide an output on the method and return a type (can't be void)
  * Calling method must specify out AND the method itself must specify out
* const - 
* null - 
* event - 
* this - references object being called from

## Types
* All types are 1 of 2 categories
  * Reference Types
    * Variables store a reference to an object
      * Multiple variables can point to the same object
    * Strings are reference types!
      * Strings function like a value type and are immutable
    * Arrays are always reference types
      * Arrays have a fixed size
      * Always 0 indexed 
  * Value Types
    * Variables hold the value
    * No pointers, no references
    * Most primitive types are value types
      * ints, floats, etc
    * Typically immutable
      * Can change the value but can't modify the value
      ```csharp
      DateTime date = new DateTime(2015, 1, 1);

      date.AddDays(1); // The work this code does is lost to the garbage! 
      date = date.AddDays(1); // OK!
      ```
* **struct** definitions create value types
  * struct should be used for single values instead of a class
  * should be small
* **enum** creates a value type
  * Assigns a symbolic reference to a value
    ```csharp
    public enum PayrollType
    {
        Contractor = 1,
        Salaried, //2
        Executive, //3
        Hourly //4
    }

    if (employee.Role == PayrollType.Hourly)
    {
        // ....
    }
    ```
* Parameters pass types "by value" to methods
  * Reference types pass a copy of the reference
    * Will point to the same object!
  * Value types pass a copy of the value
    * Only has a copy of the value and will not change the originating variable


    

## Operators

## .NET
### What is .NET?
* CLR
  * Common Language Runtime
  * Execution environmnet
  * CLR manages your application
    * Memory management
    * Virtualized your application
      * OS and Hardware Independent
    * Language Independent
      * C#, C++, F#, etc
* FCL
  * Framework CLass Library
    * Reusable software to build applications
    * So big, can't know it all

### C# Command Line Compiler
* Transforms C# code into Microsoft Intermediate Language (MSIL)
  * MSIL code for the CLR to translate to Native (Similar to Java)

## Classes
* Classes are nouns! Person, place, thing or idea!
* Classes are blueprints to create **objects**
* Convention is classes get their own .cs file
  * Can define more than 1 class in .cs file
* Classes start with the **class** keyword
* Will contain members
  * Members are used to craft an abstraction
  * State members (data)
    * **Field** that holds data
      * Grades in a gradebook
  * Behavior members (do work)
    * **Method** that does work (a verb!)
* Once a class is defined
  * Can create an **object** of that class with the **new** keyword
  * The object can now access members defined in the class
* Classes are **Reference Types**
  * The variable holds a **pointer** to the class object in memory (a memory address)

### Methods
* Methods define behavior
* Every method has a return type (even void)
* Every method has zero or more parameters
* Use **params** keyword to accept a variable number of parameters
  * Always the last parameter as an array
* Method signature is the method + parameters
  * Allows for method overloading
  * Return type is *not* part of the signature

### Fields
* Fields are variables of a class
* Contains the *data* inside a class
* Often want to protect your data by making fields private
* Then use public accessors to retrieve the data
  ```csharp
  public class Animal 
  {
    private readonly string _name;

    public Animal(string name)
    {
      _name = name;
    }
  }
  ```
### Properties
* Similar to a field
* Often used to expose and control fields
* Has syntax that define a **get** and/or **set** accessors
  ```csharp
  private string _name;

  public string Name
  {
    get { return _name; }
    set
    {
      if(!String.IsNullOrEmpty(value))
      {
        _name = value;        
      }
    }
  }
  ```
* Auto-implemented properties use a hidden field
  * Will automatically get and set a field value during the appropriate operations

### Events
* Allows a class to send notifications to other classes or objects
  * Publisher raises the event (button click is the publisher)
  * One or more subscribers process the event (other classes listen for the button click)
* **Events** are based on **delegates**
* Use the **event** keyword
* Can only += or -= subscribers from an event
* Convention of most events is that the first parameter of an event should be the **sender** and the second parameter should be an array with all information needed to describe the event
  ```csharp
    public class NameChangedEventArgs : EventArgs
    {
      public string ExistingName {get; set; }
      public string NewName {get; set; }
    }
  ```
  ```csharp
  public delegate void NameChangedDelegate(object sender, NameChangedEventArgs args);
  ```
### Delegates
* Related to Events
* **delegate** is a type that references methods
  * Define a Writer delegate
  ```csharp
  public delegate void Writer(string message);
  ```
  * Then we have a Logger class
  ```csharp
    public class Logger
  {
    public void WriteMessage (String message)
    {
      Console.WriteLine(message);
    }
  }
  ```
  * Now instantiate a logger and a delegate that references the WriteMessage method
  ```csharp
  Logger logger = new Logger();
  Writer writer = new Writer(logger.WriteMessage);
  writer("Success!!");
  ```
* Delegates can reference multiple methods
  * **Multicast** Delegates
  * Can add to a delegate with += and remove with -=
### Constructors
* Special method used to initalize objects
* All classes have a default constructor that takes no parameters
* Can define your own constructors
* Must have the same method name as the class name

## Interfaces
* Maintainability
* Extensibility
* Adds abstraction
* Mocking
* Unit Testing
* Dependency Injection

## Assemblies
* A compiled file with an .exe of .dll file extension
* Contain metadata about all types inside
* MSCORELIB.DLL contains Console and other .NET classes
* Global Assembly Cache
  * Central location to store assemblies for a machine
  * C:\Windows\assembly
* When a project in Visual Studio is Built, an assembly is created
  * <Project folder>\bin\Debug
* Properties >> Application Tab
  * Assembly options
  * Output type: Class Library would be a .dll
* Visual Studio References holds Assemblies added to the project
* Press F12 on a class to be taken to the assmebly metadata (not quite source code)
* Use the **Object Browser** to see all the Namespaces and Types inside an assembly
* Must be loaded in memory to use an assembly
  * Easy approach - reference the assembly in Visual Studio
  * Otherwise add dependencies in project.json and other steps (Google it!)

## Unit Testing
* Unit Test Project in Visual Studio
* Can be added to a Visual Studio Solution as another project
* Test Menu >> Run Tests
* Microsoft.VisualStudio.TestTools.UnitTesting namespace
* C# Attributes with square brackets
  * [TestClass] - Class that has Tests in it (must be public)
  * [TestMethod] - Method of a test class to be executed
* **Assert** Class that will make assertions about the test
  * Assert.AreEqual(3, 4); => Error
* Hard to Assert against Floating Point Numbers
  * floats and doubles have a **delta** that will check if a float/double is close enough.

## OOP
* Encapsalation
  * Enclose or hide details
  * Group details together

## Misc
* Code snippets!
  * ctor - constructor
  * cw - Console.WriteLine
  * prop - property
  * testm - test method
* Math class
  * Math.Min, Math.Max, etc
* Type converstion:
  ```csharp
  float test1 = 1.5f
  Console.WriteLine((int)test1)  // prints "1"
  ```

## Test