# DAY-2-Assignment-03-Object-Oriented-Programming-OOPS-

**1. What are the six combinations of access modifier keywords and what do they do?**

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
