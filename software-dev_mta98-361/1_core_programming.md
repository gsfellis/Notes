## Computer Storage
* Computer memory is finite
* ASCII chart represents symbools in a binary computer system in decimal and hexadecimal
* Language compiles down to CPU readable code
* Higher level languages like C#, C++, JAva, etc, seperate the need to understand CPU machine languages

### Variables, Constants, and Data Types
* Variable - provides a temporary named storage location in computer memory
* Constant - either a named storage location or literal value. Cannot be changed during program execution
* Data Types - numeric, character, special
   Data Type | Range | Description
   --- | --- | ---
   byte | 0 to 255 | A sigle byte (8 bits)
   char | Any unicode character | Characters used in most languages in the world
   short | -32,768 to 32,767 | Signed integer values
   int | -2,147,483,648 to 2,147,483,647 | Larger signed integer values
   long | -9,334,372,036,854,775,808 to 9,334,372,036,854,775,807 | Even larger signed integer values
   float | +/- 1.5 x 10^-45 to +/- 3.4 x 10^38 | Floating point signed values
   Double | +/- 5.0e-324 to +/- 1.8e308 | Larger floating point signed values
   String | String of characters | Words, sentences, phrases, etc
   Boolean | True or False | Used to represent tru or false, 1 or 0

* Setting a variable as a particular type sets asside an amount of memory required for the data type
* Data types enhances performance of the program
* Reduces errors such as trying to add a string to an integer

## Data Structures
* Common Data Structures
   * Arrays
      * A collection of similar data types accessed by index
      * Typically 0 based indexing
      * Ordered by how the data is being added to the Array
         * First value will go to index 0, second to index 1, etc
    ```csharp
    string[] myArray = new string[] {"Item1", "Item2", "Item3", "Item4"}
    ```
    
   * Stack
      * A collection of objects, accessed by pop and push
      * Similar to a cafeteria tray system
      * FILO (First in, Last Out)
      * Push a value onto a stack (value is on the top)
      * Pop a value off of the stack (remove the top value)
      * Operating Systems and programs use a stack as the instruction flow
         * On an error you typically get a Stack Trace that can be read to locate the error and flow of the program instructions
    ```csharp
    Stack myStack = new Stack();
    myStack.Push("Item1")
    myStack.Push("Item2")    
    myStack.Push("Item3")
    myStack.Push("Item4")

    Object item = myStack.Pop(); // Item4 will be removed from myStack
    item = myStack.Pop(); // Item3 will be removed from myStack
    Console.WriteLine(myStack.Count); // Prints 2
    ```
    * Queue
      * A collection of objects, accessed by queuing and dequeing.
      * Similar to a line at the DMV
      * FIFO (First in, First Out)
    ```csharp
    Queue myQueue = new Queue();
    myQueue.Enqueue("Item1");
    myQueue.Enqueue("Item2");
    myQueue.Enqueue("Item3");
    myQueue.Enqueue("Item4");

    Console.WriteLine(myQueue.Peek()); // prints Item1
    Console.WriteLine(myQueue.Count); // Prints 4

    Object qValue = myQueue.Dequeue(); // Removes Item1 from myQueue

    Console.WriteLine(myQueue.Peek()); // prints Item2
    Console.WriteLine(myQueue.Count); // Prints 3
    ```
    * Dictionary  
      * A collection of objects that are acccessed by using a key
      * Stores Key-Value pairs
    ```csharp
    Dictionary<string, string> myDictionary = new Dictionary<string, string>();
    myDictionary.Add("key1", "First Item");
    myDictionary.Add("key2", "Second Item");
    myDictionary.Add("key3", "Third Item");
    myDictionary.Add("key4", "Fourth Item");

    Console.WriteLine(myDictionary("key3")); // prints "Third Item"

    myDictionary.Remove("key4"); //Removes the fourth item
    ```
## Algorithms
* A solution to a problem
* Like a recipe that can produce a logical outcome
* Bubble Sort (Incomplete!)
   * Start Sort
   * Get Value 1
   * Get Value 2
   * Is 2 > 1?
      * Yes... Swap 1 and 2
      * No... Do nothing
   * End of List?
      * Yes... List Sorted
      * No... Increment Values and Repeat
* Bubble Sort is a slow algorithm for sorting
   * If you have 10 items, and item 1 is in slot 10, it will take many iterations to bubble item 1 to the first slot   

## Decision Making
* Code that askes questions
* Kinds of Decision Making statements
   * if, if-else, if-else-if
   * switch or Select Case
* Changes program flow based on values and decisions
```csharp
int condition1 = 1;
int condition2 = 2;

// If sample
if (condition1 == 1) // true
{
    Console.WriteLine("Print this if condition1 is 1");
}

// if-else sample
if (considiton1 == 0) // false
{
    Console.WriteLine("Print this if condition1 is 0");
}
else
{
    Console.WriteLine("Print this if condition1 is not 0");
}

// if-else-if sample
if (condition1 == 0) // false
{
    Console.WriteLine("Print this if condition1 is 0");
}
else if (condition2 == 1) // true
{
    Console.WriteLine("Print this if condition2 == 1");
}
else
{
    Console.WriteLine("Nothing cool!");
}

// switch sample
int switchCondition = 3;

switch (switchCondition)
{
    case 1: // if switchCondition == 1
        Console.WriteLine("Value is 1");
        break;
    case 2: // if switchCondition == 2
        Console.WriteLine("Value is 2");
        break;
    case 3: // if switchCondition == 3
        Console.WriteLine("Value is 3");
        break;
    default: // will run if none of the above conditions is true
        Console.WriteLine("I don't know the value!");
        break;
}
```

## Repetition
* Used a lot in algorithms (Bubble sort algorithm)
* Types of repetition
   * for loops
     * runs as long as a boolean condition is true
     * boolean condition related to the **sentinal** value
     ```csharp
     // for loop sample
     for (int i = 0; i < 5; x++) // will run and print 5 times, 0-4
     {
         Console.WriteLine("x is " + x); 
     }
     ```
   * while loops
   ```csharp
   // while loop sample
   int counter = 0;
   while (counter < 5)
   {
       Console.WriteLine("counter = " + counter); // prints 5 times
       counter++;
   }
   * do-while loops
   ```csharp
   // do-while sample
   int counter = 0;
   do
   {
       Console.WriteLine("count is at " + counter);
       counter++;       
   } while (counter < 5) // this condition isn't checked until the loop runs at least once
   ```
   * recursion
      * Call a function from itself
   ```csharp
   // recursion sample
   // Factorial takes an upper limit for a range of values and multiples all the numbers in the range together
   static void Main(string[] args)
   {
       long value = Factorial(10);
       Console.WriteLine(value);
   }

   static long Factorial(int n)
   {
       if (n == 0)
       {
           return 1;
       }

       return n * Factorial(n - 1);    
   }
   ```