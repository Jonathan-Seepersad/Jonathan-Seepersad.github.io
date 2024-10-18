---
title: 'C# Reference & Cheat Sheet'
date: 2024-10-02T18:48:34-07:00
draft: false
description: ""
author: "Jonathan Seepersad"
keywords: []
---

**_This resource is still under construction. If you are using my website, feel free to comment using Giscus below (you
will need a GitHub account to leave comments this way)._**

# Vocabulary

## Types

The type of the data that can be used or stored in a program. For example, integers (int), [strings], floating point
decimal numbers (float, double) are types. If you create classes, those classes can be used as types to refer to an
instance of that class.

## Values

The actual data used and stored in a program. All values have a type. These can be passed into functions or manipulated
with code. For example, 42 can be a value of a type integer

## Strings

A string is a type of value that represents a sequence of characters. This can be used to contain text that will be
printed to a console or displayed on screen, or it can be used as a label or tag to compare against.

## Void

Void is a special return type used by functions. It denotes that this function will not return any value.

## Boolean

Boolean is a type where values can either be true or false. These values can be used where conditions are needed such as
`if`, `for`, and `while` statements.

## Float/Double

"Float" and "doubles" refer to decimal numbers where the decimal point can be repositioned. This allows it to represent
fractional numbers in between integers (like 0.5 or 3.141592), as well as very large numbers (3.4 ✕ 10³⁸), and very
small numbers (1 ✕ 10⁻⁴⁵).

The downside of using floats and doubles is that it sometimes cannot represent your entire decimal number in perfect
accuracy. Floats have limited space to store your numbers in memory, leading to the least significant digits to get
trimmed off.

```csharp
// Most significant digit
//  ⬇
    123456789.987654321
//                    ⬆
// Least significant digit
```

The difference between float and double is the size of memory each value takes up, thus leading to more accurate
representations of your numbers. Floats take up four bytes and can accurately store about six to nine most significant
digits. Doubles take up eight bytes and can accurately store about fifteen to seventeen digits. However, in both cases,
this accuracy can quickly degrade if numbers get too large or small.

The other thing to remember about floats and doubles is that the representation of your value is stored and calculated
in binary (base 2) as is everything else done on your computer. What this means is certain simple arithmetics in base 10
might seem to make sense on paper, but yield strange results from the computer.

```csharp
// You'd think the following would yield 0.3
0.1 + 0.2

// However the computer might print something like this instead
0.30000000000000004
```

For this reason, it is advised against checking whether a float equals another float, but instead checking whether
floats are less than or greater than certain values.

## Literals

A literal representation of a value. These values are constant and the data is always known because the literal always
represents that particular value.

```csharp
// An example of an integer literal
42 // A plain number
1_000_000 // Numbers can be seperated by underscores for organization

// More advanced examples of integer literals
// A number in the hexadecimal (base 16) number system
0xABCDEF // <- Note the "0x" at the start of the number
// A number in the binary (base 2) number system
0b_1101_1110_1010_1101_1011_1110_1110_1111 // <- Note the "0b" at the start of the number

// An example of a double literal
3.141592
3.0
.5
6.022e23 // <- using "e" we can specify a scientific notation exponential
10d // <- The "d" at the end makes this a double.

// An example of a float literal
3.141592f // <- Note the "f" at the end
6.022e23f // <- floats can also have exponents


// An example of a string literal
"Hello world" // <- Note that strings are
              //    surrounded with quotation mark characters (")
     
// Examples of booleans (there really is only two values here though)         
true
false
```

## Object

As C# is an object-oriented language featuring [classes] and [inheritance], classes all inherit from a base class of
`Object` (which itself is a class).

Using this type, a variable, function, or parameter can effectively work with a value of any type. Unfortunately, This
comes at the cost of not being able to access fields (variables) or methods (functions) created on those classes.

## Null

Null is a special value often used to represent _nothing_. In other words, null can be thought of as the absence of a
value. This can lead to errors when something expects a value but receives null and tries to use that value. Therefore,
it may be useful to check whether a value is null or not before using it (you can use a condition like `value == null`
or `value != null`).

Null does not necessarily have a type, but it is often used where a value is a reference (mainly classes, objects, and
array types)

## Variables

Variables are references that allow you to store values under recognizable names. They can allow you to retrieve the
value at a later point in your code. In C#, variables have types which require you to only store values of that type in
that variable.

Variables must be declared before use, and you cannot have two variables that share the same name declared in the same
scope.

## Functions

Functions are a list of instructions that you can call (or run, or execute) at a later time in your program.
See [Function Syntax] for more information on how to use and call functions.

## Parameters (Functions)

Functions can accept values which can be used for the duration of the function. These be thought of as special variables
that only exist in a function

## Return (Functions)

Functions can return or "spit out" a value after being called. This allows code to call functions and use its value
similar to how you can use a plain variable.

In functions, you can return by writing the `return` keyword, followed by the value to be returned. The type of that
return value must match the return type of that function.

```csharp
// Notice how the function has `int` as its return type...
int return42() {
  return 42; // ...so we must return a value that cooresponds to that type.
}
```

When the programs execution encounters the `return` keyword, it stops executing that function, returns the value, and
exits that function. Because of this, you can also use `return` to exit a function of type `void`. You simply use the
`return` keyword without any value.

```csharp
// This function has a return type of `void`, so it should not return anything.
void stopEarly() {
    Debug.Log("This line will run");
    return; // Notice this return has no value after it.
    Debug.Log("This line will not run");
}
```

## Class

Classes are [Objects] that can act as a container of [fields] and [methods]. When you create a class, you can use that
class as a type which can work with any value that is an instance of that class or any other class that [inherits] from
it. See [class syntax] for more information on how to create and use classes.

## Fields (Class)

A field is a reference to a value like a variable, but is attached to a class. This allows the value to be used
throughout the class across several functions, and (if the field/variable is declared public) used throughout your
project through the class it is attached to.

## Methods (Class)

A method is a function attached to a class. As it is a function, it can contain a list of instructions to execute,
accept parameters, and return values. Methods of a class also have access to fields/variables that are private to that
particular class. This allows them to do things with the private fields without exposing that field to other classes.

## Constructor (Class)

Constructors are special [methods] of your class that shares the same name as a class. It does not really have a return
type as it is used to initialize the [fields] of your class when you create a new instance of that class.

Calling constructors uses a special syntax as well. Instead of calling the method on the class (so not like
`MyClass variable = MyClass.MyClass();`) you instead use the `new` keyword (so like
`MyClass variable = new MyClass();`). The result of calling the constructor is a value that is an instance of that
class (even though the constructor does not return anything). See [class syntax] for more information on creating and
using constructors.

Note: In unity, you seldom call constructors on components and game objects (anything that uses `Monobehaviour`) as
Unity creates these for you.

## Visibility (Class)

[Fields] and [methods] at the class level may specify a visibility which determines where these fields and methods can
be used in your project. The two most commonly used ones are `private` and `public`. When a field or method is set to
`private`, that means it can be used inside your class, but cannot be used outside your class. Meanwhile, `public`
allows you to use that field or method in other scripts in your project.

## Overloading

Not to be confused with [overriding], overloading is when you use [methods] of the same name, but with different type
signatures.

```csharp
class MyClass {
    // Notice that these "addNumbers" methods have the same name,
    // but accept different types
    // (they function very similarly, but one can only deal with whole numbers). 
    public static int addNumebrs(int number1, int number2) {
        return number1 + number2;
    }
    
    public static float addNumbers(float number1, float number2) {
        return number1 + number2;
    }
}
```

## Overriding

Not to be confused with [overloading], overriding is when you create a function on a class you made that shares the same
name and type signature of a method in the class of its parent (if your class extends another class). Overloading allows
your class to be used wherever the parent class is used. However, when the method is called or executed, your overriding
method that you wrote in your class gets ran instead of the parents.

```csharp
// Monobehaviour already has the method "Setup" that takes no parameters and returns no values…
class MyClass : Monobehaviour {
    // …however, any instances of this class would use this "Setup" method instead as it overrides the previous method
    void Setup() {
        Debug.Log("Hello world");
    }
}
```

## Identifiers

Any time that you use something named, that name is known as an identifier. This includes the name of variables,
functions, classes, and types. This does not refer to language keywords like `for`, `while`, `if`, `class`, etc.

## Statements

A statement refers to an instruction that C# executes.

```csharp
// This is a statement that creates a variable `a` and assigns it with the value
// of `1`
int a = 1;
          
// This is a statement that replaces the value in variable `a` with `2` 
a = 2;

// Calling functions can be a statement
Debug.Log("Hello world");

// Curly braces denote "block" statements which can contain any number of
// statements inside it
{ Debug.Log("Hello world"); }

// "If" statements take a condition and a statement and executes the next
// statement if the condition is true
if (true) Debug.Log("Hello world");

// This makes "if" statements chainable because the next "if" statement is
// another statement (though it is generally not a good idea to use it like this
// example)
if (true)
    if (1 == 1)
        Debug.Log("Hello world");

// In order for an "if" statement to take more than one statement, you'd used a
// "block" statement
if (true) {
    Debug.Log("First");
    Debuf.Log("Second");
}

// "for", "while", "else" statements function similar to "if" statements
```

## Conditional

Conditionals are [statements] that will result in a value of type [bool] (so either true or false). Conditionals are
used in cases such as if statements and loops to determine whether its code should be executed or not.

You usually can get boolean values from comparing values together using the following operators.

| Comparison Operation     | Comparison Operator | Description                                                                                                                                                                                                                                         |
|:-------------------------|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Equality                 | `==`                | Results in true if the value on the left and right of the equality operator is of equal value. Note: equality is represented by **two equal signs**, not one. A single equal sign is to **assign** a variable and will almost always result in true |
| Inequality               | `!=`                | Results in true if the value on the left and the right of the inequality operator are not equal. In other words, the values do not match or are different.                                                                                          |
| Greater than             | `>`                 | Results in true if the value on the left is greater than the value on the right. This will return false if the values match.                                                                                                                        |
| Less than                | `<`                 | Results in true if the value on the left is less than the value on the right. This will return false if the values match.                                                                                                                           |
| Greater than or equal to | `>=`                | Results in true if the value on the left is greater than the value on the right. This will also return true if the values match, but false if the right value is greater.                                                                           |
| Less than or equal to    | `<=`                | Results in true if the value on the left is less than the value on right. This will also return true if the values match, but false if the right number is less.                                                                                    |

You can also combine and manipulate boolean values for your needs using the following operators.

| Boolean Operation | Boolean Operator | Description                                                                 | Example                                                                                                      |
|:------------------|:-----------------|:----------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------|
| Not               | `!`              | Negates the boolean value so it becomes the opposite of what it was before. | `!true` results in `false`, `!false` results in `true`                                                       |
| And               | `&&`             | Results in true if both the left and right value are true.                  | `true && true` results in `true`, `true && false` results in `false`, `false && false` results in `false`    |
| Or                | `\|\|`           | Results in true if either the left or right value is true                   | `true \|\| true` results in `true`, `true \|\| false` results in `true`, `false \|\| false` results in false |

Conditional values can also be obtained by calling functions that return boolean values.

## Inheritance

Classes in C# can extend another class to inherit the behavior attached to it. The class being extended is referred to
as the parent class while the class doing the extending is referred to as the child class. Extending the class also
allows the class to be used everywhere that the parent class is requested, and can modify the behavior of the parent
classes methods by [overriding] (or declaring a function with the same name, parameter, and visibility as the parent
class in the child class).

[Classes]:#class

[Function Syntax]:#function-syntax

[strings]:#strings

[inherits]:#inheritance

[inheritance]:#inheritance

[Objects]:#object

[fields]:#fields-class

[methods]:#methods-class

[overriding]:#overriding

[overloading]:#overloading

[statements]:#statements

[bool]:#boolean

[class syntax]:#class-syntax

-----

# Syntax

## Identifier

Identifiers must start with an alphabetic character or an underscore (`_`) but can be followed with any alphabetic,
numeric, or underscore character.

Usually if you create a function or variable using a specific identifier, you can't reuse that identifier to refer to
something else because the names will conflict. There are a few exceptions; however, this may cause confusion in your
code.

```csharp
// Valid identifiers
myVariable
myFunction4
MyClass
_myPrivateField

// Not valid identifiers
My variable // <- Cannot have spaces
"MyVariable" // <- The quotes make this a string literal, not an identifier
69Nice // <- Numbers cannot start with numbers. they must start with alphabetic or numeric characters or an underscore. 
```

Last thing to note, identifiers are case-sensitive and underscores matter.

```csharp
// These are all unique identifiers:
MyClass
myClass
my_Class
```

## Variable Syntax

[Variables] must be declared before they can be used. To declare a variable, you must specify the type of value that
this variable will contain, and an identifier that will be used to access this variable.

```csharp
// This variable is named "myNumber" and contains a value of type "int"
int myNumber;

// This variable is named "myString" and contains a value of type "string"
string myString;
```

Variables can be declared without any value, but should be set to a value before being used. If not, the value in our
variable may be [null] and could cause errors if we try to use it. To set a variable (change/replace the value that a
variable stores), you would use the single equal sign. The variable name, or the destination of where we want to put the
value goes on the left side of the equal sign. The value that we want to use goes to the right of the equal sign.

```csharp
myNumber = 42;
myString = "Hello world";

// Variables can also be set to the value that another variable contains (as long as the types match)
int newNumber;
newNumber = myNumber;

// Variables can also be set to the value returned by a function.
newNumber = getNumber();
```

Lastly, variables can be declared and set on the same line. Just like above, you specify the type and the name, but you
also put the equal sign followed by the value.

```csharp
string newString = "Another fun string!";

// You can also use the value stored in variables or returned from functions as well
string evenNewerString = newString;
int evenNewerNumber = getNumber();
```

## Function Syntax

[Functions] require a return type (which can be [void] if this function does not return any values), an [identifier] (or
the name of the function), the parameters encased in parentheses (a function can have no parameters, but it still needs
the parenthesis), and the function body.

```csharp
// The return type of this function is "void" (no return value)
// and the name of this function is "sayHello".
// It accepts no parameters.
void sayHello() {
    Debug.Log("Hello world");
} // These curly braces signify the start and end of this function

// The return type of this function is "int" (integer/whole number values)
// and the name of this function is "getNumber".
// It accepts no parameters.
int getNumber() {
    // since this function has a return type of "int",
    // it must return an integer number at some point.
    return 42;
}

// The return type of this function is "int"
// and the name of this function is "add2Numbers"
// It accepts 2 parameters which can be used as variables in this function.
int add2Numbers(int number1, int number2) {
    // We still need to return a value of type "int"
    // because our function signature says it will return int.
    return number1 + number2; // Also we can use our parmeters as variables but only in our function (they don't exist outside of our function).
}

void doNothing() {
    // void functions can use return to exit the function immediately,
    // but it does not accept any values (because "void" does not return values)
    return;
}
```

To call a function, you specify the identifier or name of the function, add parenthesis, and add values corresponding to
each parameter requested from the function signature.

```csharp

sayHello();

int myInt = getNumber(); // getNumber returns an "int"

int newInt = add2Numbers(7, 6); // "add2Numbers" takes 2 parameters of type "int" and returns and "int" 
```

## Class Syntax

[classes] begin with the `class` keyword, followed by an [identifier] for the name of the class, ending off with the
class body itself.

```csharp
class MyClass {

} // Anything inside of these curly braces is part of this class
```

Classes can contain any number of [fields] and [methods] inside its body, which can then be used throughout the class
itself (and even in other classes). Each field and method can specify a "[visibility]" which determines whether that
field or method is visible in only your current class or visible to all other class in your project.

```csharp
class MyClass {
    // this creates a field (variable that is part of the class)
    // with type "int" and name "myNumber".
    // It is public so it can be read or changed by other classes.
    // (another side effect of public fields is that they can be viewed and
    // edited directly in the unity editor)
    public int myNumber = 42;
    
    // This creates a field with type "int" and name "myPrivateNumber".
    // It is private so it is only accessible from this class
    // (attemtping to read or change this value from other classes will lead
    // to errors).
    private int myPrivateNumber = 69;
    
    // This creates a method with return type "void"
    // (so we won't return a value) and name "myMethod".
    // It is public so it can be used in other classes in our project.
    public void myMethod() {
        Debug.Log("Hello world");
    }
    
    // This creates a method with return type "int" and
    // name "getMyPrivateNumber". It is public so it can be ran from other
    // scripts in our project.
    public int getMyPrivateNumber() {
        // Since this "myPrivateNumber" is a private field on this class,
        // it has access to read it's value. This allows it to return the value
        // to anotherclass if they call this function.
        return myPrivateNumber;
    }
    
    // This creates a method with return type of "void"
    // (so we won't return a value) and a name "setMyPrivateNumber".
    // This method is private so other classes cannot access this
    // function directly, but we are able to use it in this current class. 
    private void setMyPrivateNumber(int newNumber) {
        // Set "myPrivateNumber" to whatever value is in "newNumber"
        myPrivateNumber = newNumber
    }
    
    // This is a special function known as a "constructor".
    // Constructors take a visibility and the name of the class as the
    // function name (notice no return type, because calling a constructor
    // should result in an instance of the class as a value)
    public MyClass(int number1, int number2) {
        myNumber = number1;
        myPrivateNumber = number2;
    }
}
```

In the above example, pay special attention to the last function. This is a [constructor], allowing you to create an
instance of your class so you can actually use its methods and fields.

To use the fields and methods of a class, we first must create an instance of our class

```csharp
// Creates a new instance of "MyClass" so we han use its fields and methods 
MyClass myClass = new MyClass();

// We can access fields from our class using the dot (".").
Debug.Log(myClass.myNumber);

// However we cannot access fields that are private.
// This results in error.
Debug.Log(myClass.myPrivateNumber);

// We can also call methods from our class using the dot.
myClass.myMethod();
Debug.Log(myClass.getMyPrivateNumber());

// However, again, we cannot call methods that are private outside of
// the function. This results in error.
myClass.setMyPrivateNumber(72);
```

## If/Else/Else If Syntax

If [statements] allow you to run code only if a certain condition is true.

If statements begin with the `if` keyword, followed by parenthesis. Inside the parenthesis must be
a [conditional statement], or a statement that will result in a `true` or `false` value. After the parenthesis follows
exactly one [statement] to be used as the body of your if statement. If you need to put multiple statements in the body
of your if statement, you can use a block statement to group multiple statements together.

```csharp
// Because the bool literal "true" is always true, this always runs.
if(true) Debug.Log("This will always run");

// Because the bool literal "false" is never true, this never runs.
if(false) Debug.Log("This will never run");

// Remember single equal sign is asignment (setting variable),
// double equal sign is a comparison (results in a bool value). 
int myNumber = 42;
if (myNumber == 42) { // Block statements allow you to have multiple
                      // statements in your "if" body
     Debug.Log("Hello world");
     Debug.Log("My Lucky number is:" + myNumber);
}
```

Sometimes you may want to run code when a condition is true, but sometimes you may also want to run other code if the
condition is false. This is where `else` comes in. Immediately following the body of the `if` statement, you can place
the `else` keyword to do something when the if condition is false. Because `else` only happens when the `if` statement's
condition is true, `else` does not take a condition. It only takes a single statement as a body (again, if you want to
execute multiple statements, you can use block statements to group multiple statements together).

```csharp
if (myNumber == 42)
    Debug.Log("Hey! that is my lucky number");
else // Notice no condition on "else" because it runs only when the if condition is false
    Debug.Log("Well, that isn't my lucky number");

//The same can be done with block statements as below:
if (myNumber == 42) {
    Debug.Log("Hey! that is my lucky number");
} else {
    Debug.Log("Well, that isn't my lucky number");
}
```

Lastly, you may want to run something if the first condition is false, but you may also want to do so only when a
certain condition is true. As I was talking about `if` statements above, `if` statements _are indeed_ statements. So you
can put an `if` statement as the body for another `if` or `else` statement like so:

```csharp
string myName = "Jonathan";

// Note: the following example of using an "if" statement in an "if" statement
// is valid, but can be simplified by using a boolean operator
// such as "&&" (and)
if (myNumber == 8)
    if (myName == "Jonathan")
        Debug.Log("Well, now that actually is my lucky number");
    else; // Note: Placing an else statement here is not a very good idea
         // because it is not clear which if statement this else cooresponds to
        
if (myNumber == 69)
    Debug.Log("Nice ;)");
else if(myNumber == 420) // This is an "if" statement used as the body
                         // of an "else" statement", or you can think of it
                         // as an "else if" statemtent
    Debug.Log("Blaze it");
else
    Debug.Log("Your no fun");
```

One thing to be careful about is that the for loop doesn't take semicolons after the parenthesis as it is not yet
complete without its body. Placing a semicolon after the conditional basically checks the comparison, and ends the `if`
statement immediately leading to undesirable behavior.

```csharp
if (myNumber == 12345);
{
    Debug.Log("Hey! you guessed my password!");
}
// Confusingly, regardless of the value in "myNumber", this code still prints
// that you guessed the password because the semicolon ends
// the "if" statement early.
```

## While Loop Syntax

While loops are [statements] similar to [if] statements, except it repeats its action for as long as the condition is
true.

You begin a while loop by writing the `while` keyword, followed by parenthesis. Inside the parenthesis must be a
conditional statement, or a statement that will result in a true or false value. One thing to note though is that you
want your condition to be able to change. If you use literal values, or you never change your condition, you'll find
that it either never runs (because the condition was false) or will never stop running (because it started true, but
will never change to false).

Following the parenthesis and condition, you can put exactly one statement to be used as the loop's body. If you need to
put multiple statements in the body of your for loop, you can use a block statement to group multiple statements
together.

```csharp
// This while loop will never end, which may cause Unity to freeze
while(true)
    Debug.Log("This while loop will never ever end!");
    
// Instead lets create a variable that will eventually result in the
// condition being false so we don't loop forever.
int myNumber = 10;
while(myNumber > 0) {
    Debug.Log("Countdown: " + myNumber);
    // Make "myNumber" set to itself minus 1 (so we are just counting down by 1)
    myNumber = myNumber - 1;
}
```

Alternatively, code inside the body can break out of the loop if we come across a `break` statement. Also, if we are in
a function, we can return inside our loop which causes the function to exit, thus also exiting our loop.

```csharp
// Even though we have the condition set to true, we use break so we
// can exit our loop.
while(true)
    break; // This basically exits the loop the first time it runs.

int myNumber = 10;
while(true) {
    Debug.Log("Countdown: " + myNumber);
    if (myNumber > 0)
        break; // We can put break statements inside an if statement to
               // break out of our loop under specific conditions. 
    myNumber = myNumber - 1;
}
```

While loops also have a variant called `do while` loops. This has the body before the condition guaranteeing that the
body runs at least once, regardless of what the condition may result in.

A `do while` loop consists of the `do` keyword, followed by exactly one statement, ending off with the `while` keyword
and our condition in parentheses (also, because we are ending this statement, we use a semicolon after our condition
this time).

```csharp
do {
    Debug.Log("This will run once at least");
} while(false);
```

## For Loop Syntax

The "for" loop is a [statement] that repeats its action for as long as its condition is true but, unlike while loops,
the for loop has extra parts that can allow you to keep track of a value (usually for counting but _it can_ be used for
more advanced purposes).

Creating a "for" loop consists of the `for` keyword, followed by parenthesis. However, inside these parentheses there
are three sections seperated by semicolons ("`;`"). The first section is the initializer, which can be used to set a
variable, but can also be used to define a variable that exists only in your for loop. The second section is the actual
condition that determines whether the loop runs or not. The third and final section is what I like to call the
incrementor, which runs after your "for" loop's body runs and is supposed to bring the condition closer to becoming
false. See the following example for an analogy comparing for loops to while loops.

```csharp
// This "for" loop…
for(initializer;condition;incrementor) body

// …basically cooresponds to this "while" loop
{
    initializer;
    while(condition) {
        body;
        incrementor;
    }
}

//or as a real example

// This "for" loop…
for (int i = 0; i < 10; i = i + 1) {
    Debug.Log("Count up: " + i);
}

// …basically cooresponds to this "while" loop
{
    int i = 0;
    while(i < 10) {
        {
            Debug.Log("Count up: " + i);
        }
        i = i + 1
    }
}
```

Similar to "while" loops, for loops can also use "break" to exit from a loop early. If they are part of a function, you
can also use `return` to exit the running function.

One other interesting thing about "for" loops is that the initializer, condition, and the incrementor are all optional.
You can omit any one of these fields from the condition if you don't need it (you still have to put a semicolon to
indicate that it is empty though). If the condition is omitted, it is treated as always being true, so you could make a
loop that never ends using the following example:

```csharp
for(;;) {
}
```

[variables]:#variables

[Functions]:#functionså

[identifier]:#identifier

[void]:#void

[null]:#null

[classes]:#class

[fields]:#fields-class

[methods]:#methods-class

[visibility]:#visibility-class

[constructor]:#constructor-class

[statements]:#statements

[conditional statement]:#conditional

[statement]:#statements

[if]:#ifelseelse-if-syntax
