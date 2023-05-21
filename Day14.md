#Day14

* In the below example, we can learn 
  * Abstraction

````java
package cys.training.day14;

public abstract class Bank {

	private String name;
	private String branchName;
	private String IFSC;
	private float rateOfInterest;
	private float balance;

	public Bank() {
		rateOfInterest = 0.4f;
		balance = 10000;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getBranchName() {
		return branchName;
	}

	public void setBranchName(String branchName) {
		this.branchName = branchName;
	}

	public String getIFSC() {
		return IFSC;
	}

	public void setIFSC(String iFSC) {
		IFSC = iFSC;
	}

	@Override
	public String toString() {
		return "Bank [name=" + name + ", branchName=" + branchName + ", IFSC=" + IFSC + "]";
	}

	public void displayBankDetails() {
		System.out.println("Bank name: " + name + " IFSC : " + IFSC);
	}

	public void savingsAccount(int accountNumber, int amount, int noOfDays) {
		/*
		 * Interest on savings account= Daily balance*Rate of interest* (No. of
		 * days/365) Interest= Principal*Rate of interest. Interest: 100,000*8%= 8000.
		 * Total Maturity value: 100,000+8000= Rs. 1,08,000.
		 * 
		 */
		float savingsAccount = balance * rateOfInterest * noOfDays / 365;
		System.out.println(savingsAccount);
	}

	public void savingsAccount(int accountNumber, int amount, int noOfDays, boolean seniorCitizen) {
		if (seniorCitizen == true) {
			float savingsAccount = balance * rateOfInterest * noOfDays / 365;
			System.out.println(savingsAccount + "Senior Citizen Calculation");
		} else {
			float savingsAccount = balance * rateOfInterest * noOfDays / 200;
			System.out.println(savingsAccount + "Normal Calculation");
		}

	}

	public abstract void educationLoan();
}
````