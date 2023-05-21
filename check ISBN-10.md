An ISBN-10 (International Standard Book Number)consists of 10 digits: d1d2d3d4d5d6d7d8d9d10. 
The last digit, d10, is achecksum, which is calculated from the other nine digits using the following formula: 
(d1 * 1 + d2 * 2 + d3 * 3 + d4 * 4 + d5 * 5 + d6 * 6 + d7 * 7 + d8 * 8 + d9 * 9) % 11.
If the checksum is 10, the last digit is denoted as X according to the ISBN-10 convention. 

Write a program that prompts the
user to enter the first 9 digits and displays the 10-digit ISBN (including leading zeros). 

Your program should read the input as an integer.
```java
public class ISBN {

	public static void main(String[] args) {
		System.out.print("Enter the first 9 digits of an ISBN-10 number: ");
		Scanner input = new Scanner(System.in);
		String line = input.nextLine();
		line = line.trim();

		if (line.length() != 9) {
			System.out.println("Too many numbers entered. Try again, please enter exactly the first NINE digits of "
					+ "the isbn number: ");
			line = input.nextLine();
			line = line.trim();

			if (line.length() != 9) {
				System.out.println("Seriously?...");
			}
		}
		StringBuilder sb = new StringBuilder(line);
		line = sb.reverse().toString(); // Use StringBuilder to reverse the input nums to make operating on them easier
		int isbn = Integer.parseInt(line); // Convert the nums to an integer
		int temp = isbn;
		int t = 0;
		int sum = 0;
		int d10 = 0;
		for (int i = 1; i <= 9; i++) {
			int x = temp % 10; // Remove the last int

			System.out.print("d" + i + " = " + x + " ->: ");
			t = x * i;

			System.out.println("d" + i + " * " + i + " -> " + x + " * " + i + " = " + t);

			System.out.println("sum = " + sum + " + " + t);
			sum += t;
			System.out.println("sum = " + sum);

			temp /= 10; // Remove integer from the string
		}
		d10 = sum % 11;
		System.out.println("d10 = sum % 11 -> " + d10 + " = " + sum + " % 11");

		if (d10 == 10) {
			line = line + "X";
		} else {
			line = line + d10;
		}
		System.out.println("The ISBN-10 number is: " + line);
		input.close();
	}

}
```
Sample Output:

Enter the first 9 digits of an ISBN-10 number: 891303187
d1 = 8 ->: d1 * 1 -> 8 * 1 = 8
sum = 0 + 8
sum = 8
d2 = 9 ->: d2 * 2 -> 9 * 2 = 18
sum = 8 + 18
sum = 26
d3 = 1 ->: d3 * 3 -> 1 * 3 = 3
sum = 26 + 3
sum = 29
d4 = 3 ->: d4 * 4 -> 3 * 4 = 12
sum = 29 + 12
sum = 41
d5 = 0 ->: d5 * 5 -> 0 * 5 = 0
sum = 41 + 0
sum = 41
d6 = 3 ->: d6 * 6 -> 3 * 6 = 18
sum = 41 + 18
sum = 59
d7 = 1 ->: d7 * 7 -> 1 * 7 = 7
sum = 59 + 7
sum = 66
d8 = 8 ->: d8 * 8 -> 8 * 8 = 64
sum = 66 + 64
sum = 130
d9 = 7 ->: d9 * 9 -> 7 * 9 = 63
sum = 130 + 63
sum = 193
d10 = sum % 11 -> 6 = 193 % 11

The ISBN-10 number is: 7813031986