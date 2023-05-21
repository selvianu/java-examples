 Define an interface with three methods – earnings(), deductions() and bonus() and define a Java class "Manager‟ which uses this interface without implementing bonus() method. Also define another Java class „Substaff‟ which extends from „Manager‟ class and implements bonus() method. Write the complete program to find out earnings, deduction and bonus of a sbstaff with basic salary amount entered by the user as per the following guidelines –

earnings --> basic + DA (80% of basic) + HRA (15% of basic)
deduction --> PF 12% of basic
bonus --> 50% of basic

```java
public interface Salary {
	void earnings();

	void deductions();

	void bonus();
}
````
```java
public abstract class Manager implements Salary {
	double basic_salary;

	Manager(double basic_salary) {
		this.basic_salary = basic_salary;
	}

	@Override
	public void earnings() {
		// TODO Auto-generated method stub
		System.out.println("Earnings: Rs. " + String.format("%.2f", basic_salary + (basic_salary * 0.95)));
	}

	@Override
	public void deductions() {
		// TODO Auto-generated method stub
		System.out.println("Deductions: Rs. " + String.format("%.2f", (basic_salary * 0.12)));

	}

	abstract public void bonus();

}
```
```java
public class Substaff extends Manager {

	Substaff(double basic_salary) {
		super(basic_salary);
		// TODO Auto-generated constructor stub
	}

	@Override
	public void bonus() {
		// TODO Auto-generated method stub
		System.out.println("Bonus: Rs. " + String.format("%.2f", (basic_salary * 0.5)));
	}

}
```
```java
public class TestStaff {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner sc = new Scanner(System.in);
		System.out.print("Enter the basic salary of the substaff: ");
		double basic = sc.nextDouble();
		sc.close();
		Substaff S1 = new Substaff(basic);
		S1.earnings();
		S1.deductions();
		S1.bonus();
	}

}
```