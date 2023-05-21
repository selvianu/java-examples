# Day 6

* In the following examples, we can learn about 
  * method syntax
  * method declaration
  * method invocation
  * different types of method

```java
package com.chainsys.day6;

public class Book {
	int bookId;
	String name;
	float price;
	int rating;
	String language, couponCode = "firstorder";
	int noOfCopies = 3;

	public void sharingReview(String bookName) {
		if (bookName.trim() != null) {
			System.out.println("Worth to read , 4* ");
		} else
			System.out.println("Invalid book name");

	}

	public Boolean order(String bookName) {
		if (bookName.trim() != null) {
			if (noOfCopies > 2) {
				System.out.println("You are aviable for discount");
				if (couponCode.equals("firstorder")) {
					price = price - 100;
					System.out.println("Amount payable : " + price);
				} else {
					System.out.println("Invalid Coupon code");
				}
			} else {
				System.out.println("Amount payable: " + price);
			}
			return true;
		} else
			return false;
	}

	// Class - Blueprint - defined its data members and function/method
	// modules - modules -
	/*
	 * purchase()/order() reading() sharingReview writing()
	 * 
	 * 
	 * //syntax
	 * 
	 * private ,public, protected
	 * 
	 * accessModifer returnType functionName(listOfArgs) { } public void order() {
	 * syout(); }
	 * 
	 */
	public String writing(String bookName, String authorName) {
		System.out.println(authorName + " drafting book on Java, and the book name is:" + bookName);
		return bookName;

	}
}
```

```java
package com.chainsys.day6;

public class BookTestMethod {

	public static void main(String[] args) {

		Book book = new Book();

		book.bookId = 23;
		book.language = "tamil";
		book.name = "Thirukkural";
		book.price = 500f;
		book.rating = 5;

		  Boolean orderStatus = book.order("HeadFirstJava");
		if (orderStatus == true) {
			System.out.println("First order, share ur comments");
		}
	}

}

```