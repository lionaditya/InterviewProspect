# 1. Which print() method is getting called
```java
package com.bharat.simpleprogram;

class Parent {
	
	private void print() {
		System.out.println("Parent");
	}
	
	public void display() {
		print();
	}
}

class Child extends Parent {
	
	public void print() {
		System.out.println("Child");
	}	
}


public class OopConcept {

	public static void main(String arg[]) {
		
		Child child = new Child();
		child.display();
	}
}
```
## Explain
```
In Inheritance
 Child can inherit instance method from Parent class 
                   that also can be overrided(if requires)


In Inheritance				   
We cannot override private method of Parent class.

so Output:
  Parent
```

  
 


  

