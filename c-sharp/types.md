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