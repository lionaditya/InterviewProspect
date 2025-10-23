# SingleThreaded Application
```java
package com.adi;

public class SingleThreaded {

	public static void main(String[] args) {

		SingleThreaded st = new SingleThreaded();
		st.printNumber();
		
		for (int j = 0; j <= 200; j++) {
			System.out.print("j:" + j + "\t");
		}

	}

	void printNumber() {
		for (int i = 0; i <= 200; i++) {
			System.out.print("i:" + i + "\t");
		}
	}
	
	/*
	 * Observation:
	 *  Starting form i:0 to i: 200 then j:0 to j:200
	 * Output is sequential.
	 * 1 method execute first then second method
	 * No multithreaded here.
	 */
}
```
# Multithreaded Application
```java
package com.adi;

/*
 * 2 way of multi-threading
 *   extends the Thread class (present in java.lang)
 *   Implements the Runnable Interface.
 */
public class Multithreaded extends Thread {

	public static void main(String[] args) {

		Multithreaded mt = new Multithreaded();
		mt.start(); // for starting a thread - 
		 // it will create thread space  and invoke run() method internally
		  

		for (int j = 0; j <= 200; j++) {
			System.out.print("j:" + j + "\t");
		}

	}

	// over-ride the run method
	// also called starting point of execution of thread mehtod.
	public void run() {
		for (int i = 0; i <= 200; i++) {
			System.out.print("i:" + i + "\t");
		}
	}

	/*
	 * Observation:
	 * starting from j:0 then i:0 - u cant predict o/p
	 * O/p is not sequential anymore
	 * IIn case of multi-processor.
	 * We utilizes the processor(not wasting the processor time)
	 */
}
```
# Sleep method
```java
package com.adi;

public class Multithreaded extends Thread {

	public static void main(String[] args) throws InterruptedException {

		Multithreaded mt = new Multithreaded();
		mt.start();

		for (int j = 0; j <= 200; j++) {
			System.out.print("j:" + j + "\t");
			Thread.sleep(1000);
		}

	}

	public void run() {
		for (int i = 0; i <= 200; i++) {
			System.out.print("i:" + i + "\t");
			
			/*
			 * sleep() is a static method in Thread class It will push the invoking thread
			 * in sleep mode. The particular thread will not do anything for time (in
			 * milliseconds) we mention in sleep method. sleep method throws checked
			 * Exception
			 */

			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {

				System.out.println("Child Thread Exiting"); //User friendly message
			}

		}
	}

	/*
	 * Observation:
	 * See the way of printing
	 * There is a 1 second of gap in each of the print statement.
	 * 
	 * Usage:
	 * waiting for a particular resources - database connection or web service connection
	 *  for connecting to another server. 
	 *  then our application try for retry (try to connect to the server)
	 *  then we use sleep () method our app try after sleep mehtod execution.
	 */
}
```
# Join method
## Without Join method
```java
package com.adi;

import java.util.Scanner;

/*
 * We asked end user to enter a number;
 *   and will calculate the sum of all the number till that number.
 * Eg - if someone enter 5 then calculate 1+2+3+4+5
 *  so i/p gathering should be from main method
 *    and calculation will be happen on different thread.
 */
public class JoinDemo extends Thread {

	//2- Require global variable.
	static int n,sum = 0; //Since we need to access this variable in main thread(method) and other thread.
	public static void main(String[] args) {
		
		//1
		System.out.println("Sum of first 'N' numbers");
		System.out.println("Enter a value");
		
		//Scanner class taken input stream i.e System.in
		 // Reading i/p from console.
		Scanner scanner = new Scanner(System.in);
		JoinDemo.n = scanner.nextInt(); 
		
		JoinDemo jd = new JoinDemo();
		jd.start();
		
		//We don't want this line to be executed until thread finish completely
		System.out.println("Sum of first "+ JoinDemo.n+ "numbers is "+ JoinDemo.sum);
	}

	//override run method
	public void run() {
		for(int i =1 ; i <= JoinDemo.n; i++) {
			JoinDemo.sum += i; 
		}
	}
}
/*
 * Observation
 * Sum of first 'N' numbers
    Enter a value
     5
    Sum of first 5 numbers is 0
    
    main thread will not wait until the execution of another thread.
 */
```
## With Join method

```java
package com.adi;

import java.util.Scanner;

/*
 * We asked end user to enter a number;
 *   and will calculate the sum of all the number till that number.
 * Eg - if someone enter 5 then calculate 1+2+3+4+5
 *  so i/p gathering should be from main method
 *    and calculation will be happen on different thread.
 */
public class JoinDemo extends Thread {

	//2- Require global variable.
	static int n,sum = 0; //Since we need to access this variable in main thread(method) and other thread.
	public static void main(String[] args) throws InterruptedException {
		
		//1
		System.out.println("Sum of first 'N' numbers");
		System.out.println("Enter a value");
		
		//Scanner class taken input stream i.e System.in
		 // Reading i/p from console.
		Scanner scanner = new Scanner(System.in);
		JoinDemo.n = scanner.nextInt(); 
		
		JoinDemo jd = new JoinDemo();
		jd.start();
		/*
		 * The particular thread on which join() method is invoke
		 *   here on child thread join is invoke
		 *   It will complete it's exeution and go to dead state 
		 *     then only it will execute other thread
		 *     
		 *     So first child thread completes it's execution and then main thread will complete
		 */
		jd.join();
		System.out.println("Sum of first "+ JoinDemo.n+ " numbers is "+ JoinDemo.sum);
	}

	//override run method
	public void run() {
		for(int i =1 ; i <= JoinDemo.n; i++) {
			JoinDemo.sum += i; 
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
/*
 * Observation
Sum of first 'N' numbers
Enter a value
5
Sum of first 5 numbers is 15
 */
}
```
## With join method
```java
package com.adi;

import java.util.Scanner;

/*
 * We asked end user to enter a number;
 *   and will calculate the sum of all the number till that number.
 * Eg - if someone enter 5 then calculate 1+2+3+4+5
 *  so i/p gathering should be from main method
 *    and calculation will be happen on different thread.
 */
public class JoinDemo extends Thread {

	//2- Require global variable.
	static int n,sum = 0; //Since we need to access this variable in main thread(method) and other thread.
	public static void main(String[] args) throws InterruptedException {
		
		//1
		System.out.println("Sum of first 'N' numbers");
		System.out.println("Enter a value");
		
		//Scanner class taken input stream i.e System.in
		 // Reading i/p from console.
		Scanner scanner = new Scanner(System.in);
		JoinDemo.n = scanner.nextInt(); 
		
		JoinDemo jd = new JoinDemo();
		jd.start();
		/*
		 * The particular thread on which join() method is invoke
		 *   here on child thread join is invoke
		 *   It will complete it's exeution and go to dead state 
		 *     then only it will execute other thread
		 *     
		 *     So first child thread completes it's execution and then main thread will complete
		 */
		jd.join();
		System.out.println("Sum of first "+ JoinDemo.n+ " numbers is "+ JoinDemo.sum);
	}

	//override run method
	public void run() {
		for(int i =1 ; i <= JoinDemo.n; i++) {
			JoinDemo.sum += i; 
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}
/*
 * Observation
Sum of first 'N' numbers
Enter a value
5
Sum of first 5 numbers is 15
 */
```

