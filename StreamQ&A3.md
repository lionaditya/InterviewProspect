![alt text](image-91.png)
# Q-1) Sort list of employees by salary
![alt text](image-92.png)
- If we try to sort object in normal way we get up ending Class Cast Exception.
- You ask me to sort the object but i don't know which field should be taken.
## Natural order
![alt text](image-93.png)
```java
package com.example.stream;

import java.util.Arrays;
import java.util.Comparator;
import java.util.List;

public class CreateStream {

	public static void main(String arg[]) {	
		
		List<Employee> employees = Arrays.asList(
				new Employee(101, "John", 50000.0),
				new Employee(102, "Alice", 70000.0),
				new Employee(103, "Bob", 45000.0),
				new Employee(104, "David", 90000.0)
			);
		
		//sort list of employee by salary
		
		List<Employee> list = employees.stream() //convert it into stream
		       .sorted(Comparator.comparing(Employee::getSalary))   //U want to sort based on salary
		        .toList();
		
		System.out.println(list);
	/*
	 * [Employee [id=103, name=Bob, salary=45000.0], 
	 * Employee [id=101, name=John, salary=50000.0],
	 *  Employee [id=102, name=Alice, salary=70000.0],
	 *   Employee [id=104, name=David, salary=90000.0]]	
	 */
	}
}
````
## Employee class
```java
package com.example.stream;

public class Employee {

	private Integer id;
	private String name;	
	private Double salary;
	public Employee(Integer id, String name, Double salary) {
		super();
		this.id = id;
		this.name = name;
		this.salary = salary;
	}
	public Integer getId() {
		return id;
	}
	public void setId(Integer id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public Double getSalary() {
		return salary;
	}
	public void setSalary(Double salary) {
		this.salary = salary;
	}
	@Override
	public String toString() {
		return "Employee [id=" + id + ", name=" + name + ", salary=" + salary + "]";
	}
}
```
## descending order
```java
package com.example.stream;

import java.util.Arrays;
import java.util.Comparator;
import java.util.List;

public class CreateStream {

	public static void main(String arg[]) {	
		
		List<Employee> employees = Arrays.asList(
				new Employee(101, "John", 50000.0),
				new Employee(102, "Alice", 70000.0),
				new Employee(103, "Bob", 45000.0),
				new Employee(104, "David", 90000.0)
			);
		
		//sort list of employee by salary
		
		List<Employee> list = employees.stream() //convert it into stream
		       .sorted(Comparator.comparing(Employee::getSalary).reversed())   
		        .toList();
		
		System.out.println(list);
	/*
	[Employee [id=104, name=David, salary=90000.0],
	 Employee [id=102, name=Alice, salary=70000.0],
	  Employee [id=101, name=John, salary=50000.0], 
	  Employee [id=103, name=Bob, salary=45000.0]]
	 */
	}
}
```
## Sorted based on id
```java
package com.example.stream;

import java.util.Arrays;
import java.util.Comparator;
import java.util.List;

public class CreateStream {

	public static void main(String arg[]) {	
		
		List<Employee> employees = Arrays.asList(
				new Employee(101, "John", 50000.0),
				new Employee(102, "Alice", 70000.0),
				new Employee(103, "Bob", 45000.0),
				new Employee(104, "David", 90000.0)
			);
		
		//sort list of employee by salary
		
		List<Employee> list = employees.stream() //convert it into stream
		       .sorted(Comparator.comparing(Employee::getId))   
		        .toList();
		
		System.out.println(list);
	/*
	[Employee [id=101, name=John, salary=50000.0],
	 Employee [id=102, name=Alice, salary=70000.0],
	  Employee [id=103, name=Bob, salary=45000.0], 
	  Employee [id=104, name=David, salary=90000.0]]
	 */
	}
}
```
## Sorted based on name
```java
package com.example.stream;

import java.util.Arrays;
import java.util.Comparator;
import java.util.List;

public class CreateStream {

	public static void main(String arg[]) {	
		
		List<Employee> employees = Arrays.asList(
				new Employee(101, "John", 50000.0),
				new Employee(102, "Alice", 70000.0),
				new Employee(103, "Bob", 45000.0),
				new Employee(104, "David", 90000.0)
			);
		
		//sort list of employee by salary
		
		List<Employee> list = employees.stream() //convert it into stream
		       .sorted(Comparator.comparing(Employee::getName))   
		        .toList();
		
		System.out.println(list);
	/*
	[Employee [id=102, name=Alice, salary=70000.0], 
	Employee [id=103, name=Bob, salary=45000.0],
	 Employee [id=104, name=David, salary=90000.0],
	  Employee [id=101, name=John, salary=50000.0]]
	 */
	}
}
```
#  Q-2) Calculate the average age of a list of Person objects using Java Stream.


