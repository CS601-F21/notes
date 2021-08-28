Object-Oriented Principles Worksheet
====
Adapated from Terence Parr's OO Worksheet

This worksheet explores your understanding of the fundamental principles behind object-oriented programming including dynamic binding, polymorphism, data hiding, and inheritance. Express your answers using Java syntax.

**1. Given the following class definition is it possible to create an instance of `Animal`?**

```java
abstract class Animal {
  ...
  public abstract void speak();
}
```

**2. Will the following definition of Tiger compile without error?**

```java
class Tiger extends Animal {
  public void scratch() {;}
  public String getName() { return "tigger"; }
}
```

**3. Considering Tiger and the Animal class, which class is the subclass and which is the superclass?**

**4. What is the difference between an instance of Tiger and the class Tiger? Does the following compile properly?**

```java
  String n = Tiger.getName();
```

**5. Is it possible toredefine Tiger to make the speak() method private like the following? Why or why not?**

```java
class Tiger extends Animal {
  ...
  private void speak() {
    System.out.println("roar!");
  }
}
```

**6. Assume Dog and Cat are subclasses of Animal. Which of the following assignments will result in compile-time warnings?**

```java
  Animal a = ... ;
  Dog d = ... ;
  Cat c = ... ;

  a = d;
  a = (Animal)d;
  d = a;
  d = (Dog)a;
  c = d;
  d = c;
```

**7. Which method is called in each of the following:**

```java
Bag b = ...;
b.insert("some string");
b.insert(3);
b.insert("3");
```

given the following:

```java
class Bag {
  ...
  public void insert(String s) {...}
  public void insert(int i) {...}
  public void insert(float f) {...}
}
```

**8. Consider the following class definitions:**

```java
class Human {
	String name;
	...
	public String getName() {
		return name;
	}
	public String getInfo() {
		return getName();
	}
}
class Student extends Human {
	String ID;
	...
	public String getName() {
		return name+":"+ID;
	}
}
...
Student s = new Student("Madonna","111-22-3333");
Human h = s;
```

 * What does s.getName() return?

 * What does h.getName() return?

 * What does s.getInfo() return?

 * What does h.getInfo() return?

**9. Which of the following assignments result in compile-time errors? Will any assignments compile properly, but eventually lead to run-time errors (ClassCastException)?**

```java
Airplane a = ...;
Bird b = ...;
FlyingSquirrel s = ...;

CanFly f;

f = a;
f = b;
f = s;
f = (CanFly)s;
a = b;
```

Assume the following definitions:

```java
interface CanFly {
  public void fly();
}

class Airplane implements CanFly {
  public void fly() {...}
}

class Bird implements CanFly {
  public void fly() {...}
}

class FlyingSquirrel {
  public void fly() {...}
}
```


**10. Can two individual employee objects refer to two different company names given the following class? Can they each have a different ID?**

```java
class Employee {
    String ID;
    static String companyName;
    public static void setCompanyName(String n) {
        companyName = n;
    }
    public String getID() {
        return ID;
    }
    ...
}
```

 * Could getID() refer to method setCompanyName()?
 * Could setCompanyName() refer to getID()? 