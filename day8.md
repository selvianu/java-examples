#Day8

* In the below example, we can learn 
  * Array
    * An array is a container object that holds a fixed number of values of a single type.
  * Method

```java
package com.chainsys.w2.day8;

import java.util.Scanner;

public class Array {

	public static void main(String[] args) {
		String[] name = new String[4];
		Integer[] phoneNumber = new Integer[4];

		Scanner s = new Scanner(System.in);

		for (int i = 0; i < name.length; i++) {
			System.out.println("Enter user name");
			name[i] = s.nextLine();
			System.out.println(name[i]);
		}

		for (int i = 0; i < phoneNumber.length; i++) {
			System.out.println("Enter user phone");
			phoneNumber[i] = s.nextInt();
			System.out.println(phoneNumber[i]);
		}
	}

}

```
```
public class Array1 {

	public static void main(String[] args) {
		Scanner s = new Scanner(System.in);
//int[] id;
		long[] mobileNumber = { 6789, 234567, 9876,34567 };
		
		for (int i = 0; i < mobileNumber.length; i++) {
			System.out.println(mobileNumber[i]);
		}

		Float[] price = new Float[5];
		for (int i = 0; i < price.length; i++) {
			System.out.println("Enter Price");
			price[i] = s.nextFloat();
		}
		for (int i = 0; i < price.length; i++) {
		//	System.out.println("Enter Price");
			//price[i] = s.nextFloat();
			System.out.println(price[i]);
		}

	}
}
```
* Array of objects.

```
package com.chainsys.w2.day8;

import java.util.ArrayList;
import java.util.List;

public class TestEmpList {

	public static void main(String[] args) {
		Employee emp1 = new Employee("Raj", "Trainee");
		Employee emp2 = new Employee("Ram", "Trainee");
		Employee emp3 = new Employee("Priya", "Trainee");
		Employee emp4 = new Employee("Kumar", "Manager");
		Employee emp5 = new Employee("abc", "manger", 34);

		List empList = new ArrayList();
		empList.add(emp1);
		empList.add(emp2);
		empList.add(emp3);
		empList.add(emp4);
		// System.out.println(empList);

		for (Object object : empList) {
			// System.out.println(object);
		}
		for (Object listOfEmp : empList) {
			if (((Employee) listOfEmp).getDesignation().equals("Trainee")) {
				System.out.println(listOfEmp);
			}
		}

	}

}
```
