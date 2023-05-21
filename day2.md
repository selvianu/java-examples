#Day2

* In the below example, we can learn 
  * variable
  * datatype
    * primitive data types(int, boolean)
  * variable declaration 
  * variable initialization
  * main method
  * String class

```java
package com.chainsys.day1;

public class Phone {
	public static void main(String[] args) {

		// data members, variable declaration, value assignment

		int modelNumber;// variable declaration
		int space = 2;
		boolean wireless = false;// variable initialization
		String name = "Realme";
		modelNumber = 6789;
		wireless = true;// value assignment
		// boolean canMove;

		System.out.println("Phone name : " + name + " with RAM : " + space + "model number " + modelNumber);
		System.out.print("Is is wireless ?" + wireless);
		System.out.print(modelNumber + "\n" + space + "\t" + name);
		// Create class Movie and define ur own data members

	}

}	
```

* In the below example, we can learn 
  * datatype and its range
    * assigning values to primitive data types
  * 


```java
package com.chainsys.datatype;

public class DatatypeEx {

	public static void main(String[] args) {
/*
 * byte
 * Minimum value is -128 (-2^7), 
 * Maximum value is 127 (inclusive)(2^7 -1),
 * short 
 * Minimum value is -32,768 (-2^15)
 * Maximum value is 32,767 (inclusive) (2^15 -1)
 * int
 * Minimum value is - 2,147,483,648 (-2^31)
 * Maximum value is 2,147,483,647(inclusive) (2^31 -1)
 * long
 * Minimum value is -9,223,372,036,854,775,808(-2^63)
 * Maximum value is 9,223,372,036,854,775,807 (inclusive)(2^63 -1)
 * float
 * double
 * boolean
 * char
 */
		int number1=907;
		byte byteVariable=50;
		short shortVariable=17856;
		char charVariable='s';
		float floatVariable=456789f;
		double doubleVariable=9876543;
		boolean booleanValue;
		long longVariable=5678843678876345l;
		System.out.println(number1+"\n"+byteVariable+"\n"+shortVariable);
	}

}
```

* In the below example, we can learn access modifiers.
  * public
  * private
  * protected
  * default
```java
package com.chainsys.access;

public class Movie {
	// public - can be accessed from any class
	public String hero;
	// can be accessed by subclass(extends)
	protected String name;
    //default - visible to package
	boolean theatreRelease;
	int rating;
	//private accessible only within class
	private String review;

}

```

*In the following example, we can learn 
    * To create a class with data members
    * To create object
    * Naming convention of variables
  
```java
package com.chainsys.day2;

public class Employee {
	// CaptialCamelCase

	// primitive datatype = 8
	// byte, short,
	// smallCamelCase
	int empId;
	char gender;
	String name;
	String domain;
	long phoneNumber;
	boolean graduate;
	String bloodGroup, address, mailId;

}
```
```java
package com.chainsys.day2;

public class EmployeeTest {

	public static void main(String[] args) {
		Employee emp = new Employee();
		emp.empId = 89;
		emp.name = "ram";
		emp.gender = 'm';

		System.out.println(emp.empId + "\n" + emp.name + "\n" + emp.gender);

	}
}

```
* In the following example, we can learn about 
  * Arithmetic Operators
  * To get input using Scanner Class

```java
package com.chainsys.day2;

import java.util.Scanner;

public class CalculatorArithmicOperatorEx {
//example for Arithmetic operator
	public static void main(String[] args) {
//Arithmetic - +,-,*,/,%
		int num1, num2;
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter 2 nos");
		int number1 = sc.nextInt();
		int number2 = sc.nextInt();
		System.out.println("Addition of given numbers : " + (number1 + number2));
		System.out.println(number1 * number2);
	}
}
```

