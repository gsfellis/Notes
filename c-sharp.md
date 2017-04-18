# C# Notes

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

## C# Command Line Compiler
* Transforms C# code into Microsoft Intermediate Language (MSIL)
  * MSIL code for the CLR to translate to Native (Similar to Java)

## Keywords
* namespace - 
* class - 
* public - An **Access Modifier** that allows the member to be accessed from outside the class
* private - Default **Access Modifier** that only allows the member to be accessed from within the class
* void - 
* new - 

## Types

## Classes
* Classes are nouns! Person, place, thing or idea!
* Classes are blueprints to create **objects**
* Convention is classes get their own .cs file
  * Can define more than 1 class in .cs file
* Classes start with the **class** keyword
* Will contain members
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

## OOP
* Encapsalation
  * Enclose or hide details