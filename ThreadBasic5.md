![alt text](image-278.png)![alt text](image-279.png)![alt text](image-280.png)
# Simple Program to find factorial 5! = 5*4*3*2*1; = 120
![alt text](image-281.png)![alt text](image-282.png)![alt text](image-283.png)![alt text](image-284.png)
### Pgm
```java
package com.bharat.simpleprogram.executor;

public class Main {

	public static void main(String[] args) {
		
		long startTime = System.currentTimeMillis();
		
		for(int i = 1; i < 10; i++) {
			System.out.println(factorial(i));
		}

		System.out.println("Total time = "+ (System.currentTimeMillis() - startTime));
	}

	private static long factorial(int n) {	
		
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			throw new RuntimeException();
		}
		
		long result = 1;
		for(int i = 1; i <= n; i++) {
			result *= i;			
		}
		
		return result;
	}

}
```
# Now use Multithreading
![alt text](image-285.png)![alt text](image-286.png)![alt text](image-287.png)![alt text](image-288.png)
### Pgm
```java
package com.bharat.simpleprogram.executor;

public class Main {

	public static void main(String[] args) {
		
		long startTime = System.currentTimeMillis();
		
		for(int i = 1; i < 10; i++) {
			
			int finalI = i;
			
			Thread thread = new Thread(
					() -> {
						long result = factorial(finalI);
						System.out.println(result);
					});
			thread.start();
		}

		System.out.println("Total time = "+ (System.currentTimeMillis() - startTime));
	}

	private static long factorial(int n) {	
		
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			throw new RuntimeException();
		}
		
		long result = 1;
		for(int i = 1; i <= n; i++) {
			result *= i;			
		}
		
		return result;
	}

}
```
# Solution
![alt text](image-289.png)![alt text](image-290.png)
### Pgm
```java
package com.bharat.simpleprogram.executor;

public class Main {

	public static void main(String[] args) {
		
		long startTime = System.currentTimeMillis();
		
		Thread[] threads = new Thread[9]; //Creates an array of threads
		
		for(int i = 1; i < 10; i++) {
			
			int finalI = i;
			 threads[i-1] = new Thread(
					() -> {
						long result = factorial(finalI);
						System.out.println(result);
					});
			threads[i-1].start();
		}

		for(Thread thread : threads) {
			try {
				thread.join();  //wait for thread completion
				
			} catch (InterruptedException e) {
				Thread.currentThread().interrupt();
			}
		}
		System.out.println("Total time = "+ (System.currentTimeMillis() - startTime));
	}

	private static long factorial(int n) {	
		
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			throw new RuntimeException();
		}
		
		long result = 1;
		for(int i = 1; i <= n; i++) {
			result *= i;			
		}
		
		return result;
	}

}
```
# Via Executor framework
![alt text](image-291.png)![alt text](image-292.png)![alt text](image-293.png)![alt text](image-294.png)
### Pgm
```java
package com.bharat.simpleprogram.executor;

import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Main {

	public static void main(String[] args) {
		
		long startTime = System.currentTimeMillis();
		
		//We create fixed thread pool of 9 threads
		ExecutorService executorService = Executors.newFixedThreadPool(9); 		
		
		for(int i = 1; i < 10; i++) {
			
			int finalI = i;
			
			executorService.submit(() -> {
				long result = factorial(finalI);
				System.out.println(result);
			});			
			 
		}

		executorService.shutdown();
//		System.out.println("Total time = "+ (System.currentTimeMillis() - startTime));
	}

	private static long factorial(int n) {	
		
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			throw new RuntimeException();
		}
		
		long result = 1;
		for(int i = 1; i <= n; i++) {
			result *= i;			
		}
		
		return result;
	}

}
```
# You can reuse the thread 
![alt text](image-295.png)![alt text](image-296.png)![alt text](image-297.png)![alt text](image-298.png)![alt text](image-299.png)![alt text](image-300.png)![alt text](image-301.png)![alt text](image-302.png)![alt text](image-303.png)![alt text](image-304.png)![alt text](image-305.png)![alt text](image-306.png)![alt text](image-307.png)

