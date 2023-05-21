Write a program that reads an array of ints and outputs the maximum product
of two adjacent elements in the given array of numbers.
Sample O/P:
Enter number of number to find the product..
4
Enter 4 numbers
9
9
4
5
The maximum product: 81

```java
public class MaxProductArray {
	public static void main(String[] args) {
		Scanner max = new Scanner(System.in);
		int arr[] = { 9, 10, 4, 5 };
		int num = arr.length;
		maxProduct(arr, num);
	}

	static void maxProduct(int arr[], int num) {
		if (num < 2) {
			System.out.println("No pairs exists");
			return;
		}

		// Initialize max product pair
		int a = arr[0], b = arr[1];

		// Traverse through every possible pair and keep track of max product
		for (int i = 0; i < num; i++)
			for (int j = i + 1; j < num; j++)
				if (arr[i] * arr[j] > a * b) {
					a = arr[i];
					b = arr[j];
				}

		System.out.println("Max product pair is {" + a + ", " + b + "}");
	}
}
```