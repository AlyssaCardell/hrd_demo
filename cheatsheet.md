# SEPARATE WINDOW

```CSharp
using System;

public class Program
{
    public static void Main()
    {
        // --- 1. VARIABLES ---
        // We use 'string' for text and 'int' for whole numbers
        string userName;
        int userAge;

        Console.WriteLine("Welcome to the C# Security Gate!");

        // --- 2. CONSOLE.READLINE() ---
        Console.Write("Enter your name: ");
        userName = Console.ReadLine();

        Console.Write("Enter your age: ");
        // ReadLine always gives us text (string), so we must "Parse" it to a number (int)
        string ageInput = Console.ReadLine();
        userAge = int.Parse(ageInput);

        // --- 3. CONDITIONALS & COMPARISON OPERATORS ---
        // We use '>' (Greater than) to check the age
        // We use '==' (Equal to) to check for a specific name
        
        if (userAge >= 21)
        {
            Console.WriteLine("Access Granted! Welcome to the VIP lounge, " + userName + ".");
        }
        else if (userName == "Admin")
        {
            // A "Secret" back door for the admin
            Console.WriteLine("Admin bypass detected. Welcome, Boss.");
        }
        else
        {
            // The default result if the 'if' and 'else if' are both false
            int yearsLeft = 21 - userAge;
            Console.WriteLine("Access Denied. Come back in " + yearsLeft + " years!");
        }
    }
}
```

# Instructor Guide

* **String vs. Int:** Explain that `Console.ReadLine()` only speaks in "Text." If you want to do math or compare numbers (like `userAge >= 21`), you must transform that text into an integer using `int.Parse()`.
* **The Difference between `=` and `==`:** * `=` is for **assignment** (e.g., `userName = "Bob"` means "Set name to Bob").
    * `==` is for **comparison** (e.g., `userName == "Admin"` means "Is the name equal to Admin?").
* **The Flow:** The computer starts at the top of the `if` statement. As soon as it finds a "True" answer, it runs that block of code and skips the rest of the `else` sections.

---

# C# Variables Cheatsheet

## Variable Declaration & Initialization

```csharp
// Declaration (declare first, assign later)
int age;
age = 25;

// Declaration + Initialization (all at once)
string name = "John";
double price = 19.99;

// Multiple variables (same type)
int x = 10, y = 20, z = 30;

// Implicit typing (compiler infers type)
var count = 5;        // inferred as int
var message = "Hi";   // inferred as string
```

## Primitive Data Types

| Type | Size | Range | Example |
|------|------|-------|---------|
| `bool` | 1 byte | `true` / `false` | `bool isActive = true;` |
| `byte` | 1 byte | 0 to 255 | `byte level = 100;` |
| `sbyte` | 1 byte | -128 to 127 | `sbyte temp = -50;` |
| `short` | 2 bytes | -32,768 to 32,767 | `short score = -1000;` |
| `ushort` | 2 bytes | 0 to 65,535 | `ushort port = 8080;` |
| `int` | 4 bytes | -2B to 2B | `int population = 1500000;` |
| `uint` | 4 bytes | 0 to 4B | `uint clicks = 50000;` |
| `long` | 8 bytes | Huge numbers | `long stars = 1000000000000L;` |
| `float` | 4 bytes | Decimal (less precision) | `float pi = 3.14f;` |
| `double` | 8 bytes | Decimal (more precision) | `double e = 2.71828;` |
| `decimal` | 16 bytes | Financial precision | `decimal money = 99.95m;` |
| `char` | 2 bytes | Single Unicode char | `char grade = 'A';` |
| `string` | Reference | Text | `string greeting = "Hello";` |

## Type Conversion

```csharp
// String to Number
string numStr = "42";
int num1 = int.Parse(numStr);           // Throws error if invalid
bool success = int.TryParse(numStr, out int num2);  // Safe conversion

// Number to String
int age = 25;
string ageStr = age.ToString();

// Explicit Casting
double pi = 3.14;
int rounded = (int)pi;  // Result: 3 (truncates decimal)

// Convert Class
bool flag = Convert.ToBoolean("true");
int val = Convert.ToInt32("123");
```

## Constants & Readonly

```csharp
// const (compile-time constant, cannot change)
const double Pi = 3.14159;
const string AppName = "MyApp";

// readonly (runtime constant, set once in constructor or declaration)
public class Config
{
    public readonly int MaxRetries = 3;
}
```

## String Operations

```csharp
string firstName = "Jane";
string lastName = "Doe";

// Concatenation
string fullName = firstName + " " + lastName;

// String Interpolation (C# 6+)
string greeting = $"Hello, {firstName} {lastName}!";

// Verbatim String (ignores escape characters)
string path = @"C:\Users\Jane\Documents";
string multiLine = @"
    Line 1
    Line 2
";

// Common Methods
string text = "Hello World";
text.Length;                    // 11
text.ToUpper();                 // "HELLO WORLD"
text.ToLower();                 // "hello world"
text.Contains("World");         // true
text.StartsWith("Hello");       // true
text.Replace("World", "C#");    // "Hello C#"
text.Split(' ');                // ["Hello", "World"]
text.Substring(0, 5);           // "Hello"
text.Trim();                    // Removes whitespace
```

## Variable Scope

```csharp
public class Example
{
    // Field (class-level variable)
    private int instanceVar = 10;
    private static int staticVar = 20;

    public void Method()
    {
        // Local variable (method-level)
        int localVar = 30;

        if (true)
        {
            // Block scope (only exists inside {})
            int blockVar = 40;
        }
        // blockVar is NOT accessible here
    }
}
```

## Nullable Types

```csharp
// Nullable value types (can be null)
int? nullableInt = null;
double? maybeDouble = 5.5;

// Check and access value
if (nullableInt.HasValue)
{
    int value = nullableInt.Value;
}

// Null-coalescing operator
int actualValue = nullableInt ?? 0;  // Use 0 if null

// Null-conditional operator (C# 6+)
string name = null;
int? length = name?.Length;  // Returns null instead of error
```

## Operators Quick Reference

| Operator | Description | Example | Result |
|----------|-------------|---------|--------|
| `=` | Assignment | `x = 5` | x = 5 |
| `==` | Equality | `x == 5` | true |
| `!=` | Not Equal | `x != 3` | true |
| `+` | Addition/Concatenation | `3 + 2` or `"a" + "b"` | 5 or "ab" |
| `-` | Subtraction | `10 - 3` | 7 |
| `*` | Multiplication | `4 * 5` | 20 |
| `/` | Division | `10 / 3` | 3 (int) or 3.33 (double) |
| `%` | Modulus (remainder) | `10 % 3` | 1 |
| `++` | Increment | `x++` | x = x + 1 |
| `--` | Decrement | `x--` | x = x - 1 |
| `+=` | Add and assign | `x += 3` | x = x + 3 |
| `&&` | Logical AND | `true && false` | false |
| `\|\|` | Logical OR | `true \|\| false` | true |
| `!` | Logical NOT | `!true` | false |

## Best Practices

1. **Use descriptive names**: `studentCount` instead of `sc`
2. **camelCase for local variables**: `int userAge`
3. **PascalCase for public fields/properties**: `public int TotalCount`
4. **Always initialize variables**: Avoid unpredictable values
5. **Use `var` when type is obvious**: `var list = new List<string>();`
6. **Prefer `decimal` for money**: Avoid floating-point precision errors
7. **Use constants for magic numbers**: `const int MaxLoginAttempts = 3;`

---

1.  **Type the code live:** Watch the students follow along.
2.  **Break it on purpose:** Delete a semicolon or change `==` to `=` and show them the error message. This teaches them how to debug.
3.  **The "Challenge":** Ask the students to add a third condition—for example, if the user's name is "Guest," they get limited access regardless of age.