# Heap vs Pool
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
		
		String og = "opengenus"; //This is created inside String pool
		  //If this value opengenus is available already then the reference will attached to it.
		
		String og2 = new String(og); //This is created inside heap memory 
		

		System.out.println((og==og2) + " "+ (og.equals(og2))); // false true
		 //equals() method in String class ==> Used for content comparison
		 // == method always use for reference comparison
	}

}
```
# Correct Variable
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
		
		double num1 = 2.718; //Valid - since dot is allowed
		
		double num2 = 2.7_1_8; // _ Underscore is allowed between number
		
		double num3 = 2._718; // _ Underscore is between dot and number so Not allowed		

	}
}
```
# Varialbe eligible for Garbage collection 
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {

		String str1 = new String("open");
		String str2 = new String("source");
		String str3 = new String("opengenus");

		str3 = str1; // str3 = open
		str2 = str3; // str2 = open
		str1 = str2; // str1 = open

		//So Garbage collected String are 2 (str2 and str3)
	}

}
```
# Regarding byteValue() method
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {

		Integer int_data = new Integer(10);
		
		System.out.print(int_data.byteValue()); // 10
		System.out.print("-"); // 10-
		
		int int_data_2 = new Integer(10);
		
		System.out.print(int_data_2.byteValue()); //Compilation Error
		
		//byteValue() method return value of Object as byte
		// byteValue() method is available for Wrapper Class Integer
		  // and not for primitive data type int
	}
}
```
# double - float Compilation
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
		
		double d1 = 5f; // 5f can be store inside double d1
		
		double d2 = 5.0; // 5.0 is double value; U can store in double d2
		
		float f1 = 5f; // 5f is float value; U can store in float f1
		
		float f2 = 5.0; // 5.0 is double value; U can't store in float f2
		  //So compilation error
	}
}
```
# Initialization issue
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {

		String cycle;
//		System.out.println(cycle); //Compilation error
		cycle = ""; //initilaize sth with "" empty String
		System.out.println(cycle); //Its fine
		
		String plane;
		plane = null; //U can initialize with null value
		System.out.println(plane);
		
		String car, bus = "petrol";// Here bus is initialize with value petrol
		   //and car is not initialized		
		
		car = car + bus;  //Here car is used in operation 
		   //which is uninitialized variable so Compile time Error.
		
		System.out.println(car);

	}
}
```
# Default initialization concept
## For Static variable - default initialization concept exist
## For Instance variable - we need to initialize it otherwise we get CE.
# Declaration of data type in same line
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
		
		double num1, int num2 = 1; 
		
     //Java does not permit programmers to declare different data types in the same declaration.

	}
}
```
## Allowed
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
		
		int num1 = 2, num2 = 1; //This is allowed

	}
}
```
# Regarding for loop
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {

		//Compilation Error: 
		   // In for loop we check condition in middle
		    // CE: Cannot convert int into boolean value
		for(int i=0; 0; i++) {
			System.out.println("Hello World!");
		}

	}
}
```
## we can write like this
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {

	
		for(int i=0; true; i++) {
			System.out.println("Hello World!");
		}

	}
}
```
# Space calculation
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {

	
		for(int i = 0; i < 1; i++) {
			System.out.println(i+' ');// Decimal for char Space is 32 
		}
		/*  Here 0 (decimal) + "" (char) 
		 *   0 + 32 (decimal for sapce) = 32
		 * */

	}
}
```
# Regarding break
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
	
		 if (true)
	            break;  //CE- break cannot be used outside of switch or loop

	}
}
```
# Regarding $_
```java
 package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
	
		 int $_ = 5;
		 System.out.println($_); //5

	}
}
```
# Regarding _$
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
	
		 int _$ = 5;
		 System.out.println(_$); //5

	}
}
```
# Regarding $
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
	
		 int $ = 5;
		 System.out.println($); //5

	}
}
```
# _ sinlge underscore cannot be used as varible
```java
package com.example;

public class PredictTheOutput {

	public static void main(String[] args) {
	
		 int _ = 5;//'_' is a keyword from source level 9 onwards, cannot be used as identifier
		 System.out.println(_); 

	}
}
```
# main method overloaded
```java
package com.example;

public class PredictTheOutput {

	    public static void main(String[] arr){
	          
	    }
	    public static void main(String arr){
	          
	    }	
}
/*
 * main() function can be overloaded in Java
 * The main() function that has String[] will be the entry point and will be called by Java.
 *  No output right now* 
 */
```
# Char additon
```java
package com.example;

public class PredictTheOutput {
	
	    public static void main(String[] arr){
	    	
	    	 System.out.println('j' + 'a' + 'v' + 'a'); //418
	    }
	   
}
/*
As each character is enclosed in single quotes
  it is considered as a character and not a string by Java. 
 the characters are converted to ASCII value before concatenation that is addition.
 
 As the string "java" cannot fit in a character
 */
```
# Need to check
```java
package com.example;

public class PredictTheOutput {
	
	    public static void main(String[] arr){
	    	
	    	  Integer num1 = 400;
	          Integer num2 = 400;

	         
	          if(num1 == num2){
	              System.out.println(0);
	          }
	          else{
	              System.out.println(1); //1
	          }
	    }
	   
}
/*
 Integer class support the range of -128 to 127. If the number is within the range,
  autoboxing is applied. 
  This means the same reference is assigned for the same number as they are from the same pool.
     As 400 is outside the range, different references are assigned.
 */
```
# More dig
```java
package com.example;

public class PredictTheOutput {
	
	    public static void main(String[] arr){
	    	
	    	  Integer num1 = 100;
	          Integer num2 = 100;

	         
	          if(num1 == num2){
	              System.out.println(0); //0
	          }
	          else{
	              System.out.println(1); 
	          }
	    }
	   
}
/*
 Integer class support the range of -128 to 127. If the number is within the range,
  autoboxing is applied. 
  This means the same reference is assigned for the same number as they are from the same pool.
     As 100 is in the range, same references are assigned.
 */
```

