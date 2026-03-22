# Completable Future
![alt text](image-363.png)![alt text](image-364.png)![alt text](image-365.png)![alt text](image-366.png)
- Main thread waits here since completable future. get () method 
### Pgm
```java
package com.bharat.simpleprogram.executor;

import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CF {

	public static void main(String[] args) {

		
		CompletableFuture<String> completableFuture = CompletableFuture.supplyAsync(() -> {
			try {
				Thread.sleep(5000);
				System.out.println("Worker"); 
			  }catch (Exception e) {

			   }
			
			return "OK";
		});
		
		String s = null;
		try {
			s = completableFuture.get();//If you want to wait then	
		} catch (InterruptedException e) {
			
			e.printStackTrace();
		} catch (ExecutionException e) {
			
			e.printStackTrace();
		} 
		
		System.out.println(s);
		
		System.out.println(" Main ");
		
	}

}
```
## Other methods in CF
![alt text](image-367.png)![alt text](image-368.png)![alt text](image-369.png)![alt text](image-370.png)![alt text](image-371.png)![alt text](image-372.png)![alt text](image-373.png)![alt text](image-374.png)
# 
# 22Mar2026