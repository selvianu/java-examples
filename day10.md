#Day10

* In the below example, we can learn 
  * Methods
    * Method definition
    * Method invocation
  ```java
package com.chainsys.w2.day10;

import java.util.Scanner;

public class MethodsEx {

	public static void main(String[] args) {
//method invocation
		welcomeUser();
	}
//method definition
	public static void welcomeUser() {
		Scanner s = new Scanner(System.in);
		String userName = s.nextLine();
		System.out.println("Welcome, " + userName);
	}

}
````
````java
package com.chainsys.w2.day10;

import java.util.Scanner;

public class Ex1Method {
	static int price = 50;

	public static void displayMenu() {
		Scanner s = new Scanner(System.in);
		System.out.println("MENU" + "\n" + "Lunch" + "\n" + "Chinese");
		System.out.println("Enter ur menu");
		String order = s.nextLine();
		System.out.println("Ur order : " + order);
		if (order.equals("Lunch") || order.equals("meals")) {
			price = 100;
			System.out.println(price);
		} else {
			price = 70;
			System.out.println(price);
		}
	}

	public static void main(String[] args) {
		// welcomeUser();
		// order();
		Scanner s = new Scanner(System.in);
		System.out.println("Total amount of table :");
		int bill = s.nextInt();
		System.out.println("Enter users mode of payment");
		String paymentMode = s.next();
		invoice(bill, paymentMode);
	}
	public static void invoice(float totalPrice, String paymentMode) {
		if (totalPrice < 200)
			System.out.println("Your payable bill amount : " + totalPrice + "\n" + "Thanks for dining with us");
		else if (totalPrice > 500)
			System.out.println("Your payable bill amount : " + (totalPrice - 100) + "\n" + "Thanks for dining with us");
	}


	public static void welcomeUser() {
		Scanner s = new Scanner(System.in);
		System.out.println("Enter ur name");
		String userName = s.nextLine();
		System.out.println("Welcome, " + userName);
	}

	public static void order() {
		Scanner s = new Scanner(System.in);
		System.out.println("Enter ur order");
		displayMenu();
		System.out.println("Enter quantity");
		int quantity = s.nextInt();
		if (quantity > 1) {
			price = price * quantity;
			System.out.println(price);
		} else
			System.out.println("Please do enter quantity");
		System.out.println("Thanks for placing order..Enjoy ur meal.");
	}
	}
````
* String Buffer and String Builder
````java
package com.chainsys.w2.day10;

public class StringBufferBuldeRExa {

	public static void main(String[] args) {
		/*
		 * String is immutable
		 */
		String name = "raj";
		System.out.println(name);// raj
		name.concat("Ganesh");
		System.out.println("After concat : " + name);// raj ganesh
		// String firstName = name.concat(" Kumar");
		System.out.println(name);
		// immutability - overcome --> StringBuffer and StringBuilder -->Classes
		StringBuffer firstName = new StringBuffer("Ramesh");
		System.out.println(firstName);
		firstName.append(" Babu");
		System.out.println(firstName);
		StringBuilder education = new StringBuilder("B.E");
		System.out.println(education);
		education.append(", M.E");
		System.out.println(education);
		education.delete(2, 5);
		System.out.println(education);
	}
}