#Day12

* In the below example, we can learn 
  * Method Overriding

* Method Overloading
````java
  package com.chainsys.w3.day14;

public interface BankInterface {

	public float saving();

	public float deposit(float amount, int accountNumber) throws Exception;

	public float withdrawal(float amount);

	public String updateProfile(String name) throws Exception;

}
````
````java
package com.chainsys.w3.day14;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.Scanner;

public class BankImplTest {

	public static void main(String[] args) throws Exception {
		int rating = 0;
		BankImpl bankImpl = new BankImpl();
		// System.out.println(bankImpl.deposit(900, 678));
		/*
		 * String updateProfile = bankImpl.updateProfile("    h");
		 * System.out.println(updateProfile); //
		 * System.out.println(bankImpl.deposit(1000, 678)); //
		 * System.out.println(bankImpl.deposit(1000, 678));
		 * 
		 * Bank bank = new Bank(); bank.setAmount(5000);
		 * System.out.println(bankImpl.deposit(bank.getAmount(), 678));
		 */
		// 1.Parameterized constuctor-value insitalize
		Bank user1 = new Bank(4000, 20000, 4567, "Ram", "Axtyu89");
		Bank user2 = new Bank(4000, 800, 4545, "Raj", "Axtyu89");
		Bank user3 = new Bank(4000, 3000, 4545, "Raj", "BI5678");
		Bank user4 = new Bank(1000, 2000, 4545, "Raj", "BI5678");
//2ArrayList
		// 3.ArrayList obj - add Bank obj
		// 4.Iterate and print
		ArrayList<Bank> bankAccHolder = new ArrayList();
		bankAccHolder.add(user1);
		bankAccHolder.add(user2);
		bankAccHolder.add(user3);
		bankAccHolder.add(user4);
		bankAccHolder.add(user1);
		for (Object userdata : bankAccHolder) {
			System.out.println("General Object" + userdata);
		}
		for (Bank bankObj : bankAccHolder) {
			System.out.println("Bank Type : " + bankObj);
		}

		List<Bank> Axtyu89Branch = new ArrayList();
		System.out.println("Displays account holder details in IFSC : Axtyu89");
		for (Bank account : bankAccHolder) {
			if (account.getIFSC().equals("Axtyu89")) {
				Axtyu89Branch.add(account);
				System.out.println("Accounts in IFSC " + account);
			}
		}
		System.out.println("Displays rating ");
		for (Bank account : bankAccHolder) {
			System.out.println("Enter 1 for good and 0 for bad rating");
			Scanner s = new Scanner(System.in);
			rating = s.nextInt();
			if (rating == 1)
				System.out.println(rating++);
			else
				System.out.println(rating--);
			System.out.println(rating);
		}
		/*
		 * List<Bank> amount = new ArrayList(); for (Bank balanceAmount : bankAccHolder)
		 * { if (balanceAmount.getBalance() > 2000) { amount.add(balanceAmount);
		 * System.out.println("Accounts with lesser than given balance : " +
		 * balanceAmount); } }
		 */
	}
}
````
````java
package com.chainsys.w3.day14;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.Scanner;

public class BankImplTest {

	public static void main(String[] args) throws Exception {
		int rating = 0;
		BankImpl bankImpl = new BankImpl();
		// System.out.println(bankImpl.deposit(900, 678));
		/*
		 * String updateProfile = bankImpl.updateProfile("    h");
		 * System.out.println(updateProfile); //
		 * System.out.println(bankImpl.deposit(1000, 678)); //
		 * System.out.println(bankImpl.deposit(1000, 678));
		 * 
		 * Bank bank = new Bank(); bank.setAmount(5000);
		 * System.out.println(bankImpl.deposit(bank.getAmount(), 678));
		 */
		// 1.Parameterized constuctor-value insitalize
		Bank user1 = new Bank(4000, 20000, 4567, "Ram", "Axtyu89");
		Bank user2 = new Bank(4000, 800, 4545, "Raj", "Axtyu89");
		Bank user3 = new Bank(4000, 3000, 4545, "Raj", "BI5678");
		Bank user4 = new Bank(1000, 2000, 4545, "Raj", "BI5678");
//2ArrayList
		// 3.ArrayList obj - add Bank obj
		// 4.Iterate and print
		ArrayList<Bank> bankAccHolder = new ArrayList();
		bankAccHolder.add(user1);
		bankAccHolder.add(user2);
		bankAccHolder.add(user3);
		bankAccHolder.add(user4);
		bankAccHolder.add(user1);
		for (Object userdata : bankAccHolder) {
			System.out.println("General Object" + userdata);
		}
		for (Bank bankObj : bankAccHolder) {
			System.out.println("Bank Type : " + bankObj);
		}

		List<Bank> Axtyu89Branch = new ArrayList();
		System.out.println("Displays account holder details in IFSC : Axtyu89");
		for (Bank account : bankAccHolder) {
			if (account.getIFSC().equals("Axtyu89")) {
				Axtyu89Branch.add(account);
				System.out.println("Accounts in IFSC " + account);
			}
		}
		System.out.println("Displays rating ");
		for (Bank account : bankAccHolder) {
			System.out.println("Enter 1 for good and 0 for bad rating");
			Scanner s = new Scanner(System.in);
			rating = s.nextInt();
			if (rating == 1)
				System.out.println(rating++);
			else
				System.out.println(rating--);
			System.out.println(rating);
		}
		/*
		 * List<Bank> amount = new ArrayList(); for (Bank balanceAmount : bankAccHolder)
		 * { if (balanceAmount.getBalance() > 2000) { amount.add(balanceAmount);
		 * System.out.println("Accounts with lesser than given balance : " +
		 * balanceAmount); } }
		 */
	}

}
````