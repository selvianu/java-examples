#Day 3
* In the following example, we can learn to use Unary Operator.

```java
package com.chainsys.day3;

public class UnaryOperator {

	public static void main(String[] args) {
//Unary - ++,--
		int x = 5;
		System.out.println(x++);// x=x+1=>x=5(+1)//5
		System.out.println(x);
		System.out.println(++x);//x=1+x=>1+6//7
		System.out.println(x);
		System.out.println(x--);
		System.out.println(x);//6
		System.out.println(--x);//5

	}

}   
```
* In the following example, we can learn about Relational Operator.

```java
package com.chainsys.day3;

import java.util.Scanner;

public class RelationalOperator {

	public static void main(String[] args) {
		String state = "Karanataka";
		System.out.println("Enter your age");
		Scanner sc = new Scanner(System.in);
		int userAge = sc.nextInt();
		if (userAge > 18) {
			System.out.println("Enter Nationality");
			String nationality = sc.next();
			if (nationality.equals("Indian")) {
				System.out.println("Enter our state");
				state = sc.next();
				if (state.equals("Tamilnadu") || (state.equals("Pondy"))) {
					System.out.println("User is eligible to vote");
				} else if (state.equals("Andhra")) {
					System.out.println("No elections in your state now");
				} else {
					System.out.println("No election");
				}
			} else
				System.out.println("You are not an indian");

		} else
			System.out.println("Not eligible");
	}
}
```
* In the following example, we can learn about Logical Operators.

```java
package com.chainsys.day3;

import java.util.Scanner;

public class LogicalOperator {

	public static void main(String[] args) {
		long accountNumber;
		int aadharNumber = 45678, transactionPin = 1234, password = 9876;
		System.out.println("Enter account holder name");
		Scanner sc = new Scanner(System.in);
		String accountHolderName = "Ajay";
		accountHolderName = sc.next();
		if ((accountHolderName.equals("Ajay")) && (accountHolderName.length() >= 3)) {
			System.out.println("  Enter account number ");
			accountNumber = sc.nextLong();
			System.out.println("  Enter aadhar number ");
			aadharNumber = sc.nextInt();
			if (aadharNumber == 45678) {
				System.out.println("  Enter transaction pin and password ");
				transactionPin = sc.nextInt();
				password = sc.nextInt();
				if ((transactionPin == 1234) || (password == 9876)) {
					System.out.println("Successfull Transaction");
				} else {
					System.out.println("Invalid credentials");
				}
			} else {
				System.out.println("Invalid Aaadhar details");
			}

		} else {
			System.out.println("Enter valid Account holder name");
		}

	}

}
```