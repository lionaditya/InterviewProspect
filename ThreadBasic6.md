![alt text](image-308.png)![alt text](image-309.png)![alt text](image-310.png)![alt text](image-311.png)![alt text](image-312.png)![alt text](image-313.png)![alt text](image-314.png)
# About submit method
![alt text](image-315.png)![alt text](image-316.png)![alt text](image-317.png)![alt text](image-318.png)![alt text](image-319.png)![alt text](image-320.png)![alt text](image-321.png)![alt text](image-322.png)![alt text](image-323.png)![alt text](image-324.png)
## Pgm
```java
package com.bharat.simpleprogram.executor;

import java.util.Arrays;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class Main {

	public static void main(String[] args) throws InterruptedException, ExecutionException {
		
		ExecutorService executorService = Executors.newFixedThreadPool(2);	
		
		Callable<Integer> callable1 = () -> {
			System.out.println("Task1");
			return 1;
		};
		
		Callable<Integer> callable2 = () -> {
			System.out.println("Task2");
			return 2;
		};
		
		Callable<Integer> callable3 = () -> {
			System.out.println("Task3");
			return 3;
		};
		
		List<Callable<Integer>> list = Arrays.asList(callable1,callable2,callable3);	
		
		List<Future<Integer>> futures = executorService.invokeAll(list);
	
		for(Future<Integer> f : futures) {
			System.out.println(f.get()); 
		}
		executorService.shutdown();
		
		System.out.println("Hello World");
	}

}
```
# invokeAll() overloaded method
![alt text](image-325.png)![alt text](image-326.png)![alt text](image-327.png)
### Pgm
```java
package com.bharat.simpleprogram.executor;

import java.util.Arrays;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.CancellationException;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.concurrent.TimeUnit;

public class Main {

	public static void main(String[] args) {
		
		ExecutorService executorService = Executors.newFixedThreadPool(2);	
		
		Callable<Integer> callable1 = () -> {
			Thread.sleep(1000);
			System.out.println("Task1");			
			return 1;
		};
		
		Callable<Integer> callable2 = () -> {
			Thread.sleep(1000);
			System.out.println("Task2");
			return 2;
		};
		
		Callable<Integer> callable3 = () -> {
			Thread.sleep(1000);
			System.out.println("Task3");
			return 3;
		};
		
		List<Callable<Integer>> list = Arrays.asList(callable1,callable2,callable3);	
		
		List<Future<Integer>> futures = null;
		try {
			futures = executorService.invokeAll(list,1,TimeUnit.SECONDS);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
	
		for(Future<Integer> f : futures) {
			try {
				System.out.println(f.get());
			} catch (InterruptedException e) {
			
			} catch (ExecutionException e) {
				
			} catch(CancellationException e) {
				
			}
		}
		executorService.shutdown();
		
		System.out.println("Hello World");
	}

}
```
# invokeAny() Overloaded method (with or without time)
![alt text](image-328.png)![alt text](image-329.png)
### pgm
```java
package com.bharat.simpleprogram.executor;

import java.util.Arrays;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Main {

	public static void main(String[] args) {
		
		ExecutorService executorService = Executors.newFixedThreadPool(3);	
		
		Callable<Integer> callable1 = () -> {
			Thread.sleep(1000);
			System.out.println("Task1");			
			return 1;
		};
		
		Callable<Integer> callable2 = () -> {
			Thread.sleep(1000);
			System.out.println("Task2");
			return 2;
		};
		
		Callable<Integer> callable3 = () -> {
			Thread.sleep(1000);
			System.out.println("Task3");
			return 3;
		};
		
		List<Callable<Integer>> list = Arrays.asList(callable1,callable2,callable3);
		
		try {
			Integer i = executorService.invokeAny(list); //Direct integer return instead of Future
			System.out.println(i); 
			
		} catch (InterruptedException e) {
			e.printStackTrace();
		} catch (ExecutionException e) {
			e.printStackTrace();
		}		
		executorService.shutdown();		
		System.out.println("Hello World");
	}

}
```
# Future
![alt text](image-330.png)![alt text](image-331.png)![alt text](image-332.png)![alt text](image-333.png)![alt text](image-334.png)![alt text](image-335.png)![alt text](image-336.png)![alt text](image-337.png)![alt text](image-338.png)![alt text](image-339.png)![alt text](image-340.png)
# Scheduled Executor Service
![alt text](image-341.png)![alt text](image-342.png)![alt text](image-343.png)![alt text](image-344.png)![alt text](image-345.png)
### pgm
```java
package com.bharat.simpleprogram.executor;

import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class Main {

	public static void main(String[] args) {

		ScheduledExecutorService schedular = Executors.newScheduledThreadPool(1); 
		
		schedular.scheduleAtFixedRate( 
				() -> System.out.println("Task executed after every 5 seconds "),
				5, //initial delay
				5,  //period
				TimeUnit.SECONDS
				);
		
		schedular.schedule( 
				() -> {
					System.out.println("Initating shutdown");
					schedular.shutdown();
				}, 20, TimeUnit.SECONDS);		
		
	}

}
```
# Catch
![alt text](image-346.png)![alt text](image-347.png)![alt text](image-348.png)

# 10Mar2026
