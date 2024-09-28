---
id: CPTS
created_date: 2024-09-28
updated_date: 2024-09-28
type: note
tags:
  - "#csharp"
  - "#cpts321"
---

# C# Basics

- Managed language - dynamically allocated content is automatically freed.
	- Garbage collection - automatic
	- Disposal - explicitly invoked
- Has pointers but arent used generally
- Object-oriented & event-driven
- Predominantly statically typed, enforced static and dynamic type checking.

## Differences from C++

- Arrays are managed objects - not just a pointer
- **Everything** is a class or structure
- Classes are reference types, structures are value types
- No globals
- Variables cannot be used without first being initialized in C#

## Access Modifiers

Supports public, private, and internal (can be accessed by any code in the same assembly, but not another). Additionally the *protected* modifier can be used for classes.

Defaults
- For classes and structures: internal
- For members of classes and structures: private

## Reference Vs Value Types

Think of references as accessing via a pointer in C.
```csharp
/*
 * Since s is a reference type s & s2 point to the same object.
 */
string s = "Hello";  
string s2 = s;
```

Think of values as accessing via value in C.
```csharp
/*
 * Here the value of x is copied to y, so future changes to the value assigned
 * to x do not effect y.
 */
int x = 5, y = 6;
y = x;
x += 5;
```

*Note: Classes are reference types and structs are value types in C#*

## Classes & Structs

There are types of things we can declare in a C# class/struct
1. Methods
2. Fields (or attributes)
3. Properties

Properties ecapsulate a field like a wrapper, allow you to control how field is accessed.
```csharp
private string message = "message"; // Field

public string Message               // Property
{
	get { return message; }    // equivalent to: get => message;
	set { message = value; }   // equivalent to: set => message = value;
}
```

## Inheritance

C# supports inheritance but not multiple inheritance. We use interfaces to deal with the lack of multiple inheritance. Classes and structs can implement multiple interfaces. Interfaces can also define static members.

*Exeception: all classes and structures automatically inherit from the <u>object</u> class*

## Interface, Abstract Class, Concrete Class

Interface
- no state
- typically will not contain implmentation
- name starts with "I"
- cannot be instantiated

Abstract class
- can have state
- typicaly will ocntain methods with implmentation
- cannot be instatiated

## Overriding versus Hiding

**Overriding**

- Occurs when a derived class provides a specific implementation of a method defined in the base class.
- Requires the base method to be marked as `virtual`, `abstract`, `override`, and the derived class must use the `override` keyword to modify its behavior.
- The overriding function has the same signature as the base method.

**Hiding**

- Occurs when a derived class defines a method with the same name and signature as the method in the base class, but without the override keyword.
- To indicate that the derived class is intentionally hiding the base class method, the `new` keyword is used.
- The base method is still accessible via the base class reference.

```csharp
pubic class BaseClass
{
	public void Display()
	{
		Console.WriteLine("BASE CLASS");
	}
}

public class DerivedClass : BaseClass
{
	public new void Display()
	{
		Console.WriteLine("DERIVED CLASS");
	}
}

BaseClass obj1 = new BaseClass();
obj1.Display();  // BASE CLASS

DerivedClass obj2 = new DerivedClass();
obj2.Display();  // DERIVED CLASS

BaseClass obj3 = new DerivedClass();
obj3.Display();  // BASE CLASS    since its hiding not overriding
```

# Strings

- Strings in C# are immutable
- Once the object is instaciated, it cannot be changed
- If the string is initialized as "ABCDE" then it will stay that way in memory

# StringBuilder

- Class for mutable strings
- Better performance when the program has many string maniupulations

# Casting and Inheritance

When casting between objects in inheritance there is downcasting and upcasting. When upcasting there is no error because an instance of the class already exists. When downcasting it needs to be explicitly casted, and when calling a method only present in the downcasted class, it will yield a runtime error.

# Streams

Streams are an abstract data type that conceptually represents a linear sequence of **bytes**. Operations are `Read()`, `Write()`, and `Position`. The `Read()` and `Write()` functions start reading from and writing to the stream at the location specified by the property `Position`.

## Stream Arcitecture

- **Backing Store Streams**: lower level; tight to and end point (ex: file or network connection).
- **Decorator Streams**: feed off another stream and transform the data (ex: compress then encrypt).
- **Stream Adaptors**: wrap the bytes into a different format (ex: text)

# Event Driven Applications

To build an event-driven application **decouple** the UI (view) and the Logic/Data (Model) where the view is dependent on the model and the model is independent.

## Logic/Data Layer

contains all the logic to perform relevant actions with the data your application is designed to work with.

## UI Layer

Communicates with the logic/data layer telling it when the user has made alterations. It also responds to alterations in the underlying layer and updates the interface appropriately.

Ideally the UI should be flexibile.

# Events

**Broadcaster**

```csharp
Broadcaster : INotifyPropertyChange
{
	public PropertyChangedEventHandler PropertyChanged;
	private name;
	public Name
	{
		get => name
		set {
			name = value;
			PropertyChanged(this, new PropertyChangedEventArgs("Name"))
		}
	}
}
```

**Reciever**

```csharp
Reciever
{
	public Reciever()
	{
		Broadcaster.PropertyChanged += MyFunction;
	}
	
	private void MyFunction(Object sender, PropertyChangedEventArgs e)
	{
		Console.WriteLine("HI");
	}
}
```