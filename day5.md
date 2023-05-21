#Day 5

* In the following example, we can learn about Array of Object.

```java
package com.chainsys.day5;

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
package com.chainsys.day5;

public class BookArray {

	public static void main(String[] args) {
		BookExampleConstructor[] bookArray = new BookExampleConstructor[3];
		System.out.println(bookArray.length);
		bookArray[0] = new BookExampleConstructor("Tamil", 500.5f, 5, "thirukural");
		bookArray[1] = new BookExampleConstructor("English", 500.5f, 5, "HeadFirst");
		bookArray[2] = new BookExampleConstructor("Tamil", 500.5f, 5, "Java");
		for (int i = 0; i < bookArray.length; i++) {
			System.out.println("Book name : " + bookArray[i].name);
			System.out.println("Language : " + bookArray[i].language);

		}

	}

}

```
* In the following example, we can learn
  * String class
  * in-built methods of String

```java
package com.chainsys.day5;

public class StudentValidation {

	public static void main(String[] args) {

		/*
		 * String are immutabe-value cant be changed
		 */
		char id = 'n';
		int rollNo = 10;

		String name = "  Pr  iya  ";

		String valueOfRollNo = String.valueOf(rollNo);
		System.out.println(valueOfRollNo);
		String lastName = "priya";
		String mailId = new String();
		String fullName = name.concat(lastName);
		/*
		 * System.out.println(fullName); System.out.println(fullName.charAt(3));
		 * System.out.println(fullName.codePointAt(3)); int i =
		 * name.compareToIgnoreCase(lastName); System.out.println(i);
		 * System.out.println(name.contains("gu")); String copyValueOf =
		 * String.copyValueOf(id);//char array - String fullName.substring(i); String
		 * substring = name.substring(0,3); System.out.println(substring); String
		 * upperCase = lastName.toUpperCase(); System.out.println(upperCase);
		 */
		System.out.println(name.length());
		System.out.println(name.trim().length());

		Boolean student = true;
		System.out.println(student.valueOf(true));
	}
}
```