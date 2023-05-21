Write a program to print the following pattern.
A 
B B 
C C C 
D D D D 
E E E E E 
F F F F F F
```java
public class AlphaPattern {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int letter = 65; // ASCII value of capital A is 65
		// inner loop for rows
		for (int i = 0; i <= 5; i++) {
			// outer loop for columns
			for (int j = 0; j <= i; j++) {
				// prints the character
				System.out.print((char) letter + " ");
			}
			letter++;
			System.out.println();
		}
	}
}
```