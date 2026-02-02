# Q-1) Which display() method is getting called
```java
package com.bharat.simpleprogram;

class Base{
	static void display() {
		System.out.println("Base display");
	}
}
class Derived extends Base{
	static void display() {
		System.out.println("Derived  display");
	}
}
public class OopConcept {
	public static void main(String arg[]) {
		Base b = new Derived();
		b.display(); //Base display	
	}
}

```
###  Which display() method should be called;
```
   Here both method are static
  In Java we cannot override the static method in Java
    So this statement call display method of Base class
```
### In case of non-static method 
```java
class Base{
	 void display() {
		System.out.println("Base display");
	}
}
class Derived extends Base{
	 void display() {
		System.out.println("Derived  display");
	}
}
public class OopConcept {
	public static void main(String arg[]) {
		Base b = new Derived();
		b.display(); //Derived display	
	}
}
```
### In case of non-static method
- The Base class can hold the refrence of the child class
- and the instance method of child class is getting called.
# Predict Output
```java
class Animal{
	 String sound() {
		return "Generic sound";
	}
}
class Dog extends Animal{
	String sound() {
		return "Bark";
	}
}
public class OopConcept {
	public static void main(String arg[]) {
		Animal myAnimal = new Dog();
		System.out.println(myAnimal.sound());//bark
	}
}
```
### What is output of this program.
```
   method are non-static
   so method should be overridden
  
	Animal myAnimal = new Dog();
	  Parent class hold reference of child object
	  
      Here actually object is created using Dog() class
	Here because of new Dog();    
	 overridden sound() method of Dog class is called. 
```
#  Which constructor is getting called?
```java
class Animal{
	Animal(){
		System.out.println("Animal is created");
	}
}
class Dog extends Animal{
	Dog(){
		System.out.println("Dog is created.");
	}
}
public class OopConcept {
	public static void main(String arg[]) {
		Dog d = new Dog(); 
		  /* output:Animal is created
				Dog is created. * */
	}
}
```
###  Which constructor is getting called?
```
 Animal is super/parent class
    Dog is sub/child class
      So this is Inheritance
      
    Whenever we create object of child class the parent class
     constructor gets automatically called.
```
# Can we override member variable from Parent class in subclass.
```java
package com.bharat.simpleprogram;

class A{
	String s = "Class A"; //member variable of Class A (parent class)
}
class B extends A{
	String s = "Class B";//member variable of Class B (child class)
	
	void display() {
		System.out.println(s);
		System.out.println(super.s);// super keyword is used to call
		                               //parent class member variable
	}
}
public class OopConcept {
	public static void main(String arg[]) {
		B b = new B();
		b.display(); 
		
/*	output:  Class B
		      Class A */		
	}
}
```
### Explain
```
In Java
 we cannot override member varialbe from Super class to Sub class
 So s variable of class A is different from
    s variable of class B

Remember:
 WE cannot override member variable from Parent to child.
 It is available but we can't override it
 
super keyword is used to call super class constructor/method/fileds
```
# Eg of Inheritance
```java
package com.bharat.simpleprogram;

class A {
	public A() {
		System.out.println("A");
	}
}

class B extends A {
	public B() {
		System.out.println("B");
	}
}

class C extends B {
	public C() {
		System.out.println("C");
	}
}

public class OopConcept {
	public static void main(String arg[]) {
		B b = new C();	
		
	}
}
```
## Explain
```txt
Eg of Inheritance

 Whenever we create object of child class the constructor of Parent class first invoke.

 ***Output:***
   A
   B
   C
```

