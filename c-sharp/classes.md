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