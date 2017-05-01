## OOP
* 3 Pillars of Object Oriented Programming
  * Encapsalation
  * Inheritence
  * Polymorphism

### Encapsalation
* Enclose or hide complexity
* Group details together
* Allows someone to seperate the details of a the code in a method, and focus on what's important: What inputs does the method take, and what will it output?

### Inheritence
* Can define a relationship that two classes can share some code
```csharp
public class A
{
  public void DoWork()
  {
    // ... work!
  }  
}

public class B : A
{
  // will also have DoWork() method!
}
```
* Can only inherit from a single class
  * Can be chained, C inherits from B which inherits for A
  

### Polymorphism
