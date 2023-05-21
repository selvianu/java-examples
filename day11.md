#Day11

* In the below example, we can learn 
  * Method Overloading
````java
package com.chainsys.w2.day11;

public class Bank {

	public static void main(String[] args) {
		deposit(20000f, 45678789);
		deposit("Radhu", 987654, "IndianBank", "Ambattur");
		deposit("Sundar", 987654322, "IB893", 30000);
	}

	public static void deposit(float amount, int accountNumber) {
		System.out.println("Amount deposited - self");
	}

	public static void deposit(int amount, float phoneNumber) {
		System.out.println("Amount deposited - self");
	}

	public static void deposit(String beneficiaryName, int beneficiaryAccNo, String bank, String branch) {
		int amount = 7000;

		System.out.println("Amount " + amount + "deposited, will be refelecting in beneficiary  acc in 2 working");
	}

	public static void deposit(String beneficiaryName, int mobileNo, String IFSC, int amount) {

		System.out.println("Amount " + amount + "deposited, will be refelecting in beneficiary  acc with IFSC : " + IFSC
				+ " in 2 working");
	}

	public static void withdrawal(int amount, int accoutNumber, int phoneNumber) {
		//
	}

}
````
````java
package com.chainsys.w2.day11;

public class ABank {
//method definition
	public static void deposit(int amount, int accountNo) {
		int balance = 1000;
		balance = balance + amount;
		System.out.println("Your balacne : " + balance);
	}// 3000

	public void deposit(int amount, int accountNo, String depositerName) {
		int balance = 1000;
		balance = balance + amount;// 3000+2000=5000
		System.out.println("Your balane : " + balance + ", amount deposited by:  " + depositerName);
	}

	public void deposit(int amount, String IFSC, int mobileNo, String depositorName) {
		int interest = 100;
		// 5000
		int balance = 0;
		balance = balance + amount + interest;// 3000+2000=5000
		System.out.println("Your balance : " + balance + ", amount deposited by:  " + depositorName);
	}
	public void welcomeUser() {
		System.out.println("Welcome USer");
	}
}
````
````java
package com.chainsys.w2.day11;

public class ABankTest {
	public static void main(String[] args) {
		ABank bank = new ABank();
		// static method to access - ClassName.methodName
		// no need to create object for static method-how to access?
//bank.deposit(0, 0);
		ABank.deposit(2000, 45678);
//non-static class --> access with object
		bank.deposit(300, 9876567, "Raghu");
		bank.deposit(3000, "IB9834", 9745678, "Ramesh");

		ABankBranch1 b1 = new ABankBranch1();
		b1.deposit(60000, "AB1009", 56781, "Raj");
		b1.welcomeUser();
		ABank.deposit(0, 0);
		ABankBranch1.deposit(0, 0);
	}
}
````