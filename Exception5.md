Write a Program with a division method who receives two integer numbers and performs the division operation. The method should declare that it throws ArithmeticException. This exception should be handled in the main method.

/*
Write a Program with a division method who receives two integer numbers and performs the 
division operation. The method should declare that it throws ArithmeticException. 
This exception should be handled in the main method.
 * */

```java
import java.util.Scanner;

public class Assignment5 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int a = sc.nextInt();
		int b = sc.nextInt();
		
		try {
			double r = division(a, b);
			System.out.println(r);
		} catch (ArithmeticException e) {
			System.out.println(e.getMessage());
		}
		
		sc.close();
	}
	
	public static double division(int a, int b) throws ArithmeticException {
		return a / b;
	}

}
```