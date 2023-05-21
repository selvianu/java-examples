#Day9

* In the below example, we can learn 
  * Exception handling
    * Checked Exception
    * Unchecked Exception

```java
//ArithmeticException
package com.chainsys.w2.day9;

public class Main {

	public static void main(String[] args) {

		int a = 10, b = 0;
		// System.out.println(a / b);

		try {
			// code that generates exception
			int divideByZero = a / b;
			System.out.println(divideByZero);
		}

		catch (ArithmeticException e) {
			System.out.println("ArithmeticException => " + e.getMessage());
		}

		finally {
			System.out.println("This is the finally block");

		}
	}

}


```

```java
//ArrayIndexOutOfBoundsException
package com.chainsys.w2.day9;

public class ArrayExp {

	public static void main(String[] args) {
		int[] rollNo = { 2, 4, 6, 10, 12, 5 };// size/length=6--->0-5
		for (int i = 0; i <= 6; i++) {
			// System.out.println(rollNo[i]);
		}

		try {
			for (int i = 0; i <= 7; i++) {
				System.out.println(rollNo[i]);
			}
		} catch (ArithmeticException ae) {
			System.out.println(ae.getMessage());
		} catch (ArrayIndexOutOfBoundsException arr) {
			System.out.println(arr.getMessage());
		} catch (NullPointerException arr) {
			System.out.println(arr.getMessage());
		}

		catch (Exception e) {
			System.out.println(e.getMessage());
		}

	}
}
```

````java
//NumberFormatException
package com.chainsys.w2.day9;

public class NumberFormat {

	public static void main(String[] args) {
		String name = "raj";
		int i = Integer.parseInt(name);
		//System.out.println(i);

		try {
			Integer.parseInt(name);
		} catch (NumberFormatException n) {
			n.printStackTrace();
		}
	}

}
````

* UserDefined Exception / Custom Exception

```` java
package com.chainsys.w2.day9;

public class UserName {

	public static void main(String[] args) throws InvalidAgeException  {

		int age = 2;

		if (age > 18) {
			System.out.println("eligible");
							
		} else
			throw new InvalidAgeException();
	}

}
````

````java

package com.chainsys.w2.day9;

public class InvalidAgeException extends Exception {
	{
		System.out.println("InvalidAge");
	}
}   
````

````javas
package com.chainsys.w2.day9;

public class CustomExcep {

	public static void main(String[] args) throws InvalidUserDataLengthException {
		int no1 = 10, no2 = 0, no3 = 2;
		// System.out.println(no1 / no2);
		// try, catch, finally

		String name = "ramesh", mailId = "te.com";
		try {
			int result = no1 + no2;
			System.out.println(result);
			int avg = no1 / no2;
			System.out.println(avg);

		} catch (Exception e) {
			System.out.println(e.getMessage());
		}

		if (name.length() < 5)
			throw new InvalidUserDataLengthException();

		if (mailId.length() < 7)
			throw new InvalidUserDataLengthException();
		else {

		}
	}

}
````