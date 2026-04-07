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


