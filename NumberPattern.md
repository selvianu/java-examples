               1
             2  2
          3   3   3
       4   4    4   4

```java
public class NumberPattern {
	public static void main(String[] args) {
		int n = 5; // n is the number of rows you want to print
		for (int i = 1; i < n; i++) {
			for (int j = n - i; j > 1; j--) {
				System.out.print(" ");
			}

			for (int k = 0; k < i; k++) {
				System.out.print(i + " ");
			}
			System.out.println();
		}
	}
}
```