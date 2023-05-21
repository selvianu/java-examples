```java
public class Customer {

	private String name;
	private static double creditLimit;
	private String email;

	public Customer() {
		this("Bob", "bob@gmail.com");
		System.out.println("Default Constructor");

	}

	public Customer(String name, double creditLimit, String email) {
		this.name = name;
		this.creditLimit = creditLimit;
		this.email = email;
	}

	public Customer(String name, String email) {
		this(name, creditLimit = 1000, email);
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public double getCreditLimit() {
		return creditLimit;
	}

	public void setCreditLimit(double creditLimit) {
		this.creditLimit = creditLimit;
	}

	public String getEmail() {
		return email;
	}

	public void setEmail(String email) {
		this.email = email;
	}

}
```

```java
public class TestCustomer {

	public static void main(String[] args) {

		Customer cus = new Customer();
		System.out.println(cus.getName());
		// Counstructor Chaining
		Customer cus1 = new Customer("mahi", "mahi@gmail.com");
		System.out.println(cus1.getEmail() + "  " + cus1.getCreditLimit());
        //Constructor Overloading
		Customer cus2 = new Customer("banu", 1500, "banu@gmail.com");
		System.out.println(cus2.getCreditLimit() + "\n" + cus2.getEmail());
	}

}
```