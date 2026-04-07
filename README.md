# DAY-2-Assignment-03-Object-Oriented-Programming-OOPS-

**QUESTION 1. What are the six combinations of access modifier keywords and what do they do?**

**1. public**

public is Visible everywhere (no restrictions)
It Can be accessed from any class, project, or assembly.

public class Employee
{
    public string Name; // accessible anywhere
}

**2. private**

Private is Visible only inside the same class
Most restrictive. Default for class members (fields, methods).

class Employee
{
    private int salary; // cannot access outside Employee class
}

**3. protected**

Protected is Visible only inside the class and its derived (child) classes.
Not visible outside the inheritance chain.

class Employee
{
    protected string Dept;
}

class Manager : Employee
{
    void ShowDept()
    {
        Console.WriteLine(Dept); // OK, inherited
    }
}

**4. internal**

Internal is Visible only within the same assembly/project
Good for library code you don’t want exposed externally.

internal class Employee
{
    internal string Name; // accessible anywhere in this project
}

 **5. protected internal**
 
Protected is Visible to derived classes OR within the same assembly
Combines protected + internal.

protected internal string Dept; // derived classes OR same project can access

**6.private protected**

Visible only to derived classes in the same assembly
Combines private + protected but limits to same assembly.
private protected string Dept; // accessible only to derived classes in same project

**QUESTION 2. What is the difference between the static, const, and readonly keywords when applied to
a type member?**

**static**

Belongs to the class itself, not to any specific object.
Only one copy exists, shared by all objects of that class.
Can be changed (unless combined with readonly or const).

**const**

Constant value that cannot change after compilation.
Must be initialized when declared.
Always static by nature (you don’t need static keyword).

**readonly**

Can only be assigned once, either: When declared, OR In the constructor
Value can differ per object (unless combined with static)
Useful when value is fixed for the lifetime of an object, but not known at compile time.
SO, in simple we can say it as which is easy to remember

static → shared across everyone, 
const → forever fixed, like stone, 
readonly → set once when object is created, then can’t change


**QUESTION 3  What does a constructor do?**

Constructor: create instance; share the same name with the class
A constructor is a special method in a class that runs automatically when an object is created and is used to initialize the object’s data.
• Parameterless constructor: by default
• Overloaded constructors
• Static constructor: initializes static members of the type; parameterless

**QUESTION 4.Why is the partial keyword useful?**

The partial keyword allows you to split a class, struct, or interface into multiple files, and the compiler combines them into one final class.

partial is useful because it lets us to  break a big class into smaller files, so teams can work together easily and we can add our own code without touching automatically generated code.

**QUESTION 5.What is a tuple?**

A tuple is a lightweight container that can hold multiple values together, possibly of different types, without creating a separate class.

**QUESTION 6. What does the C# record keyword do?**

The C# record keyword creates a data-focused class that is immutable by default, compares objects by value instead of reference, and can be declared concisely in one line.


**QUESTION 7.What does overloading and overriding mean?**

**Method overriding**:

• Methods in base class and its subclasses share the same method name and
same input parameters
• Keyword: Virtual / Abstract in base class methods; Override in derived
class methods
• Runtime polymorphism

**Method overloading:**

• Methods in same class share the same method name, but different input
parameters
• Compile time polymorphism

**QUESTION 8.What is the difference between a field and a property?**

A field is a variable inside a class, while a property is a controlled way to access a field, often with extra logic.

**QUESTION 9.How do you make a method parameter optional?**

An optional parameter is a method parameter that the caller can omit, and it will automatically use the default value you specify.

**QUESTION 10. What is an interface and how is it different from abstract class?**

Interface: A contract that defines what methods or properties a class must implement, but provides no implementation. A class can implement multiple interfaces.
Abstract class: A partially built class that can have both implemented methods and abstract methods. A class can inherit only one abstract class.

**QUESTION 11. What accessibility level are members of an interface?**

Interface members are meant to be implemented by any class, so they must be accessible everywhere.
You cannot use private, protected, or internal on interface methods, properties, or events.

**QUESTION 12.True/False. Polymorphism allows derived classes to provide different implementations of the same method.** TRUE

**QUESTION 13. True/False. The override keyword is used to indicate that a method in a derived class is providing its own implementation of a method.** TRUE

**QUESTION 14. True/False. The new keyword is used to indicate that a method in a derived class is providing its own implementation of a method.** TRUE

**QUESTION 15. True/False. Abstract methods can be used in a normal (non-abstract) class.** FALSE Because, abstract methods requires the class itself to be abstract.


**QUESTION 16.True/False. Normal (non-abstract) methods can be used in an abstract class.** TRUE 

**QUESTION 17. True/False.Derived classes can override methods that were virtual in the base class.** TRUE

**QUESTION 18. True/False.Derived classes can override methods that were abstract in the base class.** TRUE

**QUESTION 19. True/False.In a derived class, you can override a method that was neither virtual non abstract in the base class.** FALSE, Because Only virtual or abstract methods can be overridden.


**QUESTION 20. True/False. A class that implements an interface does not have to provide an implementation for all of the members of the interface.** FALSE, Because A concrete class must implement all interface members.

**QUESTION 21. True/False. A class that implements an interface is allowed to have other members that aren’t defined in the interface.** TRUE

**QUESTION 22. True/False. A class can have more than one base class.**  FALSE C# supports single inheritance only.

**QUESTION 23. True/False. A class can implement more than one interface.** TRUE

WORKING WITH METHODS
**1.ARRAY**

using System;

class Program
{
    static void Main(string[] args)
    {
        // Generate an array of numbers (change length if you want)
        int[] numbers = GenerateNumbers(10);

        // Reverse the array
        Reverse(numbers);

        // Print the reversed array
        PrintNumbers(numbers);
    }

    // Method to generate an array of numbers from 1 to 'length'
    static int[] GenerateNumbers(int length)
    {
        int[] arr = new int[length];
        for (int i = 0; i < length; i++)
        {
            arr[i] = i + 1; // Fill array with 1, 2, 3, ...
        }
        return arr;
    }

    // Method to reverse an array in place
    static void Reverse(int[] arr)
    {
        int n = arr.Length;
        for (int i = 0; i < n / 2; i++)
        {
            int temp = arr[i];
            arr[i] = arr[n - i - 1];
            arr[n - i - 1] = temp;
        }
    }

    // Method to print the array
    static void PrintNumbers(int[] arr)
    {
        foreach (int num in arr)
        {
            Console.Write(num + " ");
        }
        Console.WriteLine(); // For newline at the end
    }
}

**2.FIBONACCI**


using System;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("First 10 numbers of the Fibonacci sequence:");
        for (int i = 1; i <= 10; i++)
        {
            Console.Write(Fibonacci(i) + " ");
        }
        Console.WriteLine();
    }

    // Recursive method to get the nth Fibonacci number
    static int Fibonacci(int n)
    {
        // Base cases: 1st or 2nd number is 1
        if (n == 1 || n == 2)
            return 1;

        // Recursive case: sum of previous two numbers
        return Fibonacci(n - 1) + Fibonacci(n - 2);
    }
}


Designing and Building Classes using object-oriented principles

**1.**

using System;

//  ABSTRACTION
abstract class Employee
{
    public string Name;

    // Abstract method
    public abstract void Work();

    // Normal method
    public void Display()
    {
        Console.WriteLine("Employee Name: " + Name);
    }
}

// INHERITANCE + POLYMORPHISM
class Developer : Employee
{
    public override void Work()
    {
        Console.WriteLine(Name + " is writing code");
    }
}

class Manager : Employee
{
    public override void Work()
    {
        Console.WriteLine(Name + " is managing the team");
    }
}

// ENCAPSULATION
class Student
{
    private int marks; // private field

    public int Marks
    {
        get { return marks; }
        set
        {
            if (value >= 0 && value <= 100)
                marks = value;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        // ENCAPSULATION
        Student s = new Student();
        s.Marks = 85;
        Console.WriteLine("Student Marks: " + s.Marks);

        // ABSTRACTION + INHERITANCE + POLYMORPHISM
        Employee e1 = new Developer();
        e1.Name = "Archana";

        Employee e2 = new Manager();
        e2.Name = "Ravi";

        e1.Display();
        e1.Work(); // Developer behavior

        e2.Display();
        e2.Work(); // Manager behavior
    }
}

EXPLANATION 

Abstraction → Employee defines common structure

Encapsulation → Student protects marks using property

Inheritance → Developer and Manager inherit from Employee

Polymorphism → Work() behaves differently for each role

**2.ABSTRACTION**

using System;

// ABSTRACTION (Base class)
abstract class Person
{
    public string Name;

    // Abstract method (must be implemented by child classes)
    public abstract void PerformRole();
}

// Student class
class Student : Person
{
    public override void PerformRole()
    {
        Console.WriteLine(Name + " is studying");
    }
}

// Instructor class
class Instructor : Person
{
    public override void PerformRole()
    {
        Console.WriteLine(Name + " is teaching");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person p1 = new Student();
        p1.Name = "Archana";

        Person p2 = new Instructor();
        p2.Name = "John";

        p1.PerformRole(); // Student behavior
        p2.PerformRole(); // Instructor behavior
    }
}

Abstraction: Person is an abstract class that defines a common method PerformRole()
Student & Instructor: Provide their own implementation of that method
Same method → different behavior.

Abstraction is used by creating a base class Person with an abstract method, and derived classes like Student and Instructor implement their own behavior.

**3. ENCAPSULATION**

using System;

// ABSTRACTION
abstract class Person
{
    // ENCAPSULATION (private fields)
    private string name;

    // Property to access private field
    public string Name
    {
        get { return name; }
        set
        {
            if (!string.IsNullOrEmpty(value))
                name = value;
        }
    }

    public abstract void PerformRole();
}

//  Student class
class Student : Person
{
    private int marks; // encapsulated field

    public int Marks
    {
        get { return marks; }
        set
        {
            if (value >= 0 && value <= 100)
                marks = value;
        }
    }

    public override void PerformRole()
    {
        Console.WriteLine(Name + " is studying and scored " + Marks);
    }
}

// Instructor class
class Instructor : Person
{
    private double salary; // encapsulated field

    public double Salary
    {
        get { return salary; }
        set
        {
            if (value > 0)
                salary = value;
        }
    }

    public override void PerformRole()
    {
        Console.WriteLine(Name + " is teaching with salary " + Salary);
    }
}

class Program
{
    static void Main(string[] args)
    {
        Student s = new Student();
        s.Name = "Archana";
        s.Marks = 90;

        Instructor i = new Instructor();
        i.Name = "John";
        i.Salary = 50000;

        s.PerformRole();
        i.PerformRole();
    }
}

**EXPLANATION**

Data like name, marks, salary is kept private
Access is given through public properties (get/set)
Validation is added (e.g., marks between 0–100)
Encapsulation is used by keeping fields private and accessing them through public properties with validation.

**4.INHERITANCE**

using System;

// Base class (Parent)
class Person
{
    public string Name;

    public void Display()
    {
        Console.WriteLine("Name: " + Name);
    }
}

// Derived class (Child)
class Student : Person
{
    public void Study()
    {
        Console.WriteLine(Name + " is studying");
    }
}

// Derived class (Child)
class Instructor : Person
{
    public void Teach()
    {
        Console.WriteLine(Name + " is teaching");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Student s = new Student();
        s.Name = "Archana";   // inherited property
        s.Display();          // inherited method
        s.Study();

        Instructor i = new Instructor();
        i.Name = "John";      // inherited property
        i.Display();          // inherited method
        i.Teach();
    }
}

**Explanation**

Student and Instructor inherit from Person
They reuse:
Name property
Display() method
No need to rewrite the same code again → saves time and avoids duplication 

Inheritance is used when Student and Instructor reuse properties and methods from the Person class instead of rewriting them.

**5.POLYMORPHISM**

using System;

// Base class (Abstraction + Inheritance + Polymorphism)
class Person
{
    public string Name;

    // Virtual method: can be overridden by derived classes
    public virtual void CalculateIncome()
    {
        Console.WriteLine(Name + " has no income defined.");
    }
}

// Derived class: Student
class Student : Person
{
    public int Stipend; // Example: stipend for student

    // Override method to provide specific behavior
    public override void CalculateIncome()
    {
        Console.WriteLine(Name + " receives a stipend of $" + Stipend);
    }
}

//Derived class: Instructor
class Instructor : Person
{
    public double Salary;

    // Override method to provide specific behavior
    public override void CalculateIncome()
    {
        Console.WriteLine(Name + " earns a salary of $" + Salary);
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Using Polymorphism
        Person p1 = new Student { Name = "Archana", Stipend = 500 };
        Person p2 = new Instructor { Name = "John", Salary = 60000 };

        // Same method call, different behavior
        p1.CalculateIncome(); // Student behavior
        p2.CalculateIncome(); // Instructor behavior
    }
}

**Explanation**

CalculateIncome() is virtual in the base class
Student and Instructor override it to provide their own behavior
Polymorphism: same method (CalculateIncome) → different outputs depending on object type
Polymorphism is achieved by using virtual methods in the base class and overriding them in derived classes to provide type-specific behavior.
6.



