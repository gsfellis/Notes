## Control Flow

### Branching
#### IF...ELSE IF...ELSE
* Evaluates a boolean expression (the condition) and will execute the code block that follows the expression when the condition returns TRUE.
* If the age is less than 2, execute ServeMilk() method
* else if age is less than 21 (but inheriently greater than 2), execute the ServeSoda() method
* If none of the other conditions return TRUE, then the age must be over 21 and it's ok to execute the ServeDrink() method

  ```csharp
    if (age <= 2)
    {
        ServeMilk();
    }        
    else if (age < 21)
    {
        ServeSoda();
    }
    else
    {
        ServeDrink();
    }
  ```

#### Ternary Operator
    * Short hand if statement that sets a variable to 1 of 2 expressions.
    * If the expression is TRUE, then the value following the ? will be applied to the variable.
    * If the expression is FALSE, then the value following the : will be applied to the variable.
    ```csharp
    string pass = age > 20 ? "pass" : "nopass";
    ```

### Switching
* Restricted to integers, characters, strings and enums
  * Case labels are constants
  * Default label is option
  * Does not support switch fallthrough, and should specify the **break** keyword in each case.

  ```csharp
  switch(name)
  {
    case "Scott":
        ServeSoda();
        break;
    case "Bob":
        ServeMilk();
        ServeDrink();
        break;
    default:
        ServeSoda();        
  }
  ```

### Iteration
* Four iteration statements
  * foreach
  * for
  * while
  * do...while

#### foreach
```csharp
int[] ages = {2, 21, 40, 72. 100};
foreach (int value in ages)
{
    Console.WriteLine(value);
}
```

#### for
* Made up of 3 components
  * initializer
  * condition
  * iterator
* Same as many other language for statements
```csharp
for(int i = 0; i < age; i++)
{
    Console.WriteLine(i);
}
```

#### while
* Will execute only if the expression is true
```csharp
while(age > 0)
{
    age -= 1;
    Console.WriteLine(age);
}
```

#### do...while
* Will execute at least once, because the condition is evaluated after the statements execute
```csharp
do
{
    age++;
    Console.WriteLine(age);

} while (age < 100);
```

### Jumping
* 5 keywords that let you unconditional jump to a target
  * break
    * Can be used to break out of a loop, case, method, etc
  * continue
    * Similar to break, only it skips code after the continue statement and begins the next iteration of a loop
  * goto
    * Rarely used, but can be used to jump to a location with a labal "labal:"
  * return
    * Can be used with a **void** method to break out of a method and "return" to the calling method statement
  * throw
    * Used to raise an exception

## Exceptions
### Throwing
* Use **throw** to raise an exception
  * Exceptioons provide type safe and structured error handling in .NET
  ```csharp
  if (age == 21)
  {
      throw new ArgumentException("21 is not a legal value");
  }
  ```
* **Unhandled** exceptions will crash your program.
  * Will crash with a Stack Trace
    * As methods, call other methods, etc, the stack is formed by calling methods
    * Most recent method will be on the top of the stack
    * Followed by the line of code that called the method, further up the stack

### Handling
* Handle exceptions using a try block
  * Runtime will search for the closest matching catch statement
  ```csharp
  try
  {
      ComputeStatistics();
  }
  catch(DivideByZeroException ex)
  {
      Console.WriteLine(ex.Message);
      Console.WriteLine(ex.StackTrace);
  }
  ```
* Essentially you "try" to execute some code that may raise an exception
* Then you "catch" the type of exceptions you wish to explicitly handle
* Multiple catch blocks can be **chained** in the try block.
  * Place the most specific type in the first catch clause
  * Catching a System.Exception catches *nearly* everything
  * Visual Studio will show an error if lower exceptions are already caught in an exception that appears further up the chain
* The **finally** statement can be used with a **try** block, and will always run, regardless on whether an exception was caught or not.
  * Used for "finalization code" that can clean up resources
  ```csharp
  FileStream file = new FileStream("file.txt", FileMode.Open);
  try
  {

  }
  finally
  {
      file.Close();
  }
  ```
* A **using** statement will automatically close these resources and is often the preferred method when dealing with objects that implement the IDisposable interface.
```csharp
using (FileStream file = new FileStream("file.txt", FileMode.Open))
{
    file.Write("some text");
} // No need to close, the using statement automatically sets up a try...finally that will clean up unmanaged resources!
```

