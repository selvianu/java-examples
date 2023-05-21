#Day 4

* In the following example, we can learn about switch

```java
package com.chainsys.day4;

public class ExampleSwitch {

	public static void main(String[] args) {
		String programmingLanguage = "servlet";
		int month = 11;
		
		/*
		 * switch (programmingLanguage) { case "Java": {
		 * System.out.println("Platform independent language"); break; } case "HTML":
		 * System.out.println("Markup Language"); break; default:
		 * System.out.println("Invalid input"); break; case "CSS":
		 * System.out.println("gives Look and feel"); break; }
		 */
		switch (month) {
		case 1: {
			System.out.println("Jan");
			break;
		}
		default:
			System.out.println("Invalid");
			break;

		case 11:
			System.out.println("November");
			break;
		}

	}
}

```
* In the following example, we can learn about loops
  * for
  * while
  * do-while

```java
package com.chainsys.day4;

public class SampleFor {

	public static void main(String[] args) {
		/*
		 * int i = 2; for (; i <= 5; i++); { System.out.println("Value of i : " + i +
		 * "\t" + "Product : " + (5 * i)); // i=0;0<5;//true-prints value of i,
		 * increment/decrement // i=1;1<5; // i=2;2<5; // i=5;5<=5 }
		 */

		// int i = -10;
		/*
		 * while(i>=1) { System.out.println(i); i--; }
		 */

		/*
		 * do
		 * 
		 * { System.out.println(i); i--; } while (i >= 1);
		 */

		for (int i = 1; i < 10; i++) {
			for (int j = 5; j < 10; j++) {
				System.out.println("J value :" + j);

			}
			System.out.println("Value of i : " + i);
		}

	}
}
```
* In the following example, we can learn about Constructor.
  * Default Constructor
  * Parametrized Constructor 
  * "this" keyword 

```java
package com.chainsys.day4;

public class BookExampleConstructor {
	String language;
	float price;
	int rating;
	String name;

	BookExampleConstructor() {
		rating = 0;
	}

	BookExampleConstructor(String language, float price, int rating, String name) {
		this.language = language;
		this.price = price;
		this.rating = rating;
		this.name = name;
	}

	BookExampleConstructor(String language, String name) {
		this.language = language;
		this.name = name;
	}
}

```
```java
package com.chainsys.day4;

public class BookExampleConstructor {
	String language;
	float price;
	int rating;
	String name;

	BookExampleConstructor() {
		rating = 0;
	}

	BookExampleConstructor(String language, float price, int rating, String name) {
		this.language = language;
		this.price = price;
		this.rating = rating;
		this.name = name;
	}

	BookExampleConstructor(String language, String name) {
		this.language = language;
		this.name = name;
	}
}

```


* In the following example, we can learn about array.
  * array declaration
  * array initialization
  * Iteration of array

```java
package com.chainsys.day4;

public class EampleArray {

	public static void main(String[] args) {
		int rollNo[] = new int[5];
		rollNo[0] = 2;
		rollNo[3] = 8;
		rollNo[2] = 7;
		rollNo[1] = 9;
		for (int i = 0; i <= 4; i++) {
		System.out.println(rollNo[i]);
		}
		int marks[] = { 45, 67, 24, 5, 2, 6 };
		for (int i = 0; i <= 5; i++) {
			System.out.println(marks[i]);
		}
	}

}

```
