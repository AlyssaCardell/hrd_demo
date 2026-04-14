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

1.  **Type the code live:** Watch the students follow along.
2.  **Break it on purpose:** Delete a semicolon or change `==` to `=` and show them the error message. This teaches them how to debug.
3.  **The "Challenge":** Ask the students to add a third condition—for example, if the user's name is "Guest," they get limited access regardless of age.