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

**6.**


using System;
using System.Collections.Generic;
using System.Linq;

// INTERFACES
interface IPersonService
{
    int CalculateAge();
    decimal CalculateSalary();
    List<string> GetAddresses();
}

interface IStudentService : IPersonService
{
    double CalculateGPA();
    void EnrollCourse(Course course, string grade);
}

interface IInstructorService : IPersonService
{
    decimal CalculateBonus();
    int CalculateExperience(); // years since join date
}

interface ICourseService
{
    string CourseName { get; set; }
    List<Student> EnrolledStudents { get; }
    void EnrollStudent(Student student, string grade);
}

interface IDepartmentService
{
    string DepartmentName { get; set; }
    Instructor Head { get; set; }
    decimal Budget { get; set; }
    List<Course> Courses { get; }
}

// ABSTRACT BASE CLASS
abstract class Person : IPersonService
{
    public string Name { get; set; }
    public DateTime DateOfBirth { get; set; }
    private decimal salary;
    private List<string> addresses = new List<string>();

    public decimal Salary
    {
        get => salary;
        set
        {
            if (value < 0) throw new Exception("Salary cannot be negative.");
            salary = value;
        }
    }

    public void AddAddress(string address) => addresses.Add(address);

    public List<string> GetAddresses() => addresses;

    public int CalculateAge()
    {
        var today = DateTime.Today;
        int age = today.Year - DateOfBirth.Year;
        if (DateOfBirth.Date > today.AddYears(-age)) age--;
        return age;
    }

    public abstract decimal CalculateSalary();
}

// STUDENT CLASS
class Student : Person, IStudentService
{
    private Dictionary<Course, string> courseGrades = new Dictionary<Course, string>();

    public void EnrollCourse(Course course, string grade)
    {
        courseGrades[course] = grade.ToUpper();
        course.EnrollStudent(this, grade);
    }

    public double CalculateGPA()
    {
        if (courseGrades.Count == 0) return 0.0;

        double totalPoints = 0;
        foreach (var grade in courseGrades.Values)
        {
            totalPoints += grade switch
            {
                "A" => 4,
                "B" => 3,
                "C" => 2,
                "D" => 1,
                "F" => 0,
                _ => 0
            };
        }
        return totalPoints / courseGrades.Count;
    }

    public override decimal CalculateSalary()
    {
        return 0; // students don't have salary
    }
}

// INSTRUCTOR CLASS
class Instructor : Person, IInstructorService
{
    public DateTime JoinDate { get; set; }
    public Department Department { get; set; }

    public override decimal CalculateSalary()
    {
        return Salary + CalculateBonus();
    }

    public decimal CalculateBonus()
    {
        int years = CalculateExperience();
        return Salary * 0.05m * years; // 5% bonus per year of experience
    }

    public int CalculateExperience()
    {
        var today = DateTime.Today;
        int years = today.Year - JoinDate.Year;
        if (JoinDate.Date > today.AddYears(-years)) years--;
        return years;
    }
}

// COURSE CLASS
class Course : ICourseService
{
    public string CourseName { get; set; }
    public List<Student> EnrolledStudents { get; } = new List<Student>();
    private Dictionary<Student, string> grades = new Dictionary<Student, string>();

    public void EnrollStudent(Student student, string grade)
    {
        if (!EnrolledStudents.Contains(student))
            EnrolledStudents.Add(student);
        grades[student] = grade.ToUpper();
    }

    public string GetGrade(Student student)
    {
        return grades.ContainsKey(student) ? grades[student] : "N/A";
    }
}

// DEPARTMENT CLASS
class Department : IDepartmentService
{
    public string DepartmentName { get; set; }
    public Instructor Head { get; set; }
    public decimal Budget { get; set; }
    public DateTime StartDate { get; set; }
    public DateTime EndDate { get; set; }
    public List<Course> Courses { get; } = new List<Course>();
}

class Program
{
    static void Main(string[] args)
    {
        // Create department
        Department csDept = new Department
        {
            DepartmentName = "Computer Science",
            Budget = 100000,
            StartDate = new DateTime(2026, 1, 1),
            EndDate = new DateTime(2026, 12, 31)
        };

        // Create instructor
        Instructor instructor = new Instructor
        {
            Name = "John Smith",
            DateOfBirth = new DateTime(1980, 5, 20),
            Salary = 60000,
            JoinDate = new DateTime(2015, 6, 1),
            Department = csDept
        };
        csDept.Head = instructor;

        // Create courses
        Course cSharp = new Course { CourseName = "C# Basics" };
        Course algorithms = new Course { CourseName = "Algorithms" };
        csDept.Courses.Add(cSharp);
        csDept.Courses.Add(algorithms);

        // Create student
        Student student = new Student
        {
            Name = "Archana",
            DateOfBirth = new DateTime(2000, 3, 15)
        };
        student.EnrollCourse(cSharp, "A");
        student.EnrollCourse(algorithms, "B");

        // Display information
        Console.WriteLine($"{instructor.Name}, Age: {instructor.CalculateAge()}, Total Salary: {instructor.CalculateSalary()}, Bonus: {instructor.CalculateBonus()}, Experience: {instructor.CalculateExperience()} years");

        Console.WriteLine($"{student.Name}, Age: {student.CalculateAge()}, GPA: {student.CalculateGPA():0.00}");

        Console.WriteLine($"Department: {csDept.DepartmentName}, Head: {csDept.Head.Name}, Budget: ${csDept.Budget}");
        Console.WriteLine("Courses Offered:");
        foreach (var course in csDept.Courses)
        {
            Console.WriteLine($" - {course.CourseName}, Enrolled Students: {course.EnrolledStudents.Count}");
        }
    }
}

**Interfaces**

IPersonService → common person methods
IStudentService, IInstructorService inherit from IPersonService
ICourseService → course operations
IDepartmentService → department info

**Abstraction**

Person base class with abstract methods (CalculateSalary)

**Encapsulation**

Private fields for Salary, Marks, Addresses
Public properties with validation

**Inheritance**

Student and Instructor inherit from Person

**Polymorphism**

CalculateSalary() is overridden in Student and Instructor

**7.**

using System;

// Color Class
class Color
{
    private int red;
    private int green;
    private int blue;
    private int alpha;

    // Constructor with all four values
    public Color(int red, int green, int blue, int alpha)
    {
        this.Red = red;
        this.Green = green;
        this.Blue = blue;
        this.Alpha = alpha;
    }

    // Constructor with RGB, alpha defaults to 255
    public Color(int red, int green, int blue) : this(red, green, blue, 255) { }

    // Properties with validation (0-255)
    public int Red
    {
        get => red;
        set => red = Clamp(value);
    }

    public int Green
    {
        get => green;
        set => green = Clamp(value);
    }

    public int Blue
    {
        get => blue;
        set => blue = Clamp(value);
    }

    public int Alpha
    {
        get => alpha;
        set => alpha = Clamp(value);
    }

    // Helper method to clamp values between 0 and 255
    private int Clamp(int value)
    {
        if (value < 0) return 0;
        if (value > 255) return 255;
        return value;
    }

    // Method to get grayscale value
    public int GetGrayscale()
    {
        return (Red + Green + Blue) / 3;
    }
}

// Ball Class
class Ball
{
    public int Size { get; private set; }
    public Color Color { get; private set; }
    private int throwCount;

    // Constructor
    public Ball(int size, Color color)
    {
        this.Size = size;
        this.Color = color;
        this.throwCount = 0;
    }

    // Pop method
    public void Pop()
    {
        Size = 0;
    }

    // Throw method
    public void Throw()
    {
        if (Size > 0)
            throwCount++;
        else
            Console.WriteLine("Cannot throw a popped ball!");
    }

    // Get number of times thrown
    public int GetThrowCount()
    {
        return throwCount;
    }
}

// Program to test the classes
class Program
{
    static void Main(string[] args)
    {
        // Create a color (red = 100, green = 150, blue = 200)
        Color myColor = new Color(100, 150, 200);

        Console.WriteLine($"Grayscale of color: {myColor.GetGrayscale()}");

        // Create a ball with size 10 and the color
        Ball myBall = new Ball(10, myColor);

        // Throw the ball 3 times
        myBall.Throw();
        myBall.Throw();
        myBall.Throw();

        Console.WriteLine($"Ball thrown {myBall.GetThrowCount()} times.");

        // Pop the ball
        myBall.Pop();
        Console.WriteLine("Ball popped!");

        // Try throwing again
        myBall.Throw();
        Console.WriteLine($"Ball thrown {myBall.GetThrowCount()} times after popping.");
    }
}

**Color Class**

Stores Red, Green, Blue, Alpha (0–255)
Can create with RGB (alpha defaults to 255) or RGBA
GetGrayscale() returns average of RGB values

**Ball Class**

Has Size, Color, and throwCount
Pop() sets size to 0
Throw() increments throwCount only if size > 0
GetThrowCount() returns total throws

Write some code in your Main method to create a few balls, throw them around a few
times, pop a few, and try to throw them again, and print out the number of times that the
balls have been thrown. (Popped balls shouldn’t have changed.)

using System;

class Program
{
    static void Main(string[] args)
    {
        // Create some colors
        Color redColor = new Color(255, 0, 0);
        Color greenColor = new Color(0, 255, 0);
        Color blueColor = new Color(0, 0, 255);

        // Create some balls
        Ball ball1 = new Ball(10, redColor);
        Ball ball2 = new Ball(15, greenColor);
        Ball ball3 = new Ball(8, blueColor);

        // Throw balls multiple times
        ball1.Throw();
        ball1.Throw();

        ball2.Throw();
        ball2.Throw();
        ball2.Throw();

        ball3.Throw();

        // Pop ball2
        ball2.Pop();
        Console.WriteLine("Ball2 popped!");

        // Try throwing all balls again
        ball1.Throw(); // Should increment
        ball2.Throw(); // Should NOT increment
        ball3.Throw(); // Should increment

        // Print out throw counts
        Console.WriteLine($"Ball1 has been thrown {ball1.GetThrowCount()} times.");
        Console.WriteLine($"Ball2 has been thrown {ball2.GetThrowCount()} times.");
        Console.WriteLine($"Ball3 has been thrown {ball3.GetThrowCount()} times.");
    }
}

Ball1: Thrown 2 times, then again after popping → total 3
Ball2: Thrown 3 times, then popped → cannot throw anymore → total 3
Ball3: Thrown once, then again → total 2
The Pop() method prevents further throws

**Fields:** Variables declared inside a class to store data.

**Access Modifiers:** Keywords (public, private, etc.) that control visibility of class members.

**Enumeration Types (enum):** A named set of constant values.

**Constructors:** Special methods used to initialize objects of a class.

**Methods:** Functions defined in a class to perform actions or return values.

**Properties**: Class members that provide controlled access to private fields.

**Inheritance:** Mechanism where a class derives from another class to reuse code.

**Interfaces:** Contracts that define methods/properties a class must implement.

**Polymorphism:** Ability of objects to take many forms, allowing methods to behave differently in derived classes.





