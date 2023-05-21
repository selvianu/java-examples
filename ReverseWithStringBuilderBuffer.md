```java
public class Strings {
	private static final Pattern PATTERN = Pattern.compile(" +");
	private static final String WHITESPACE = " ";

	private Strings() {
		throw new AssertionError("Cannot be instantiated");
	}

	public static String reverseWordsV1(String str) {

		if (str == null || str.isBlank()) {
			// or throw IllegalArgumentException
			return "";
		}

		String[] words = str.split(WHITESPACE);
		StringBuilder reversedString = new StringBuilder();

		for (String word : words) {

			StringBuilder reverseWord = new StringBuilder();

			for (int i = word.length() - 1; i >= 0; i--) {
				reverseWord.append(word.charAt(i));
			}

			reversedString.append(reverseWord).append(WHITESPACE);
		}

		return reversedString.toString();
	}

	public static String reverseWordsV2(String str) {

		// or throw IllegalArgumentException
		if (str == null || str.isBlank()) {
			return "";
		}

		return PATTERN.splitAsStream(str).map(w -> new StringBuilder(w).reverse())
				.collect(Collectors.joining(WHITESPACE));
	}

	public static String reverse(String str) {

		// or throw IllegalArgumentException
		if (str == null || str.isBlank()) {
			return "";
		}

		return new StringBuilder(str).reverse().toString();
	}
}
```
```java
public class Main {
	private static final String TEXT = "My high school, the Illinois Mathematics and Science Academy, "
			+ "showed me that anything is possible and that you're never too young to think big. "
			+ "At 15, I worked as a computer programmer at the Fermi National Accelerator Laboratory, "
			+ "or Fermilab. After graduating, I attended Stanford for a degree in economics and " + "computer science.";

	public static void main(String[] args) {

		System.out.println("Input text: \n" + TEXT + "\n");

		System.out.println("Reverse words in String via StringBuilder:");
		long startTimeV1 = System.nanoTime();

		String reversedV1 = Strings.reverseWordsV1(TEXT);

		displayExecutionTime(System.nanoTime() - startTimeV1);
		System.out.println("Reversed: \n" + reversedV1);

		System.out.println();
		System.out.println("Reverse words in String using Java 8 functional-style:");
		long startTimeV2 = System.nanoTime();

		String reversedV2 = Strings.reverseWordsV2(TEXT);

		displayExecutionTime(System.nanoTime() - startTimeV2);
		System.out.println("Reversed: \n" + reversedV2);

		System.out.println();
		System.out.println("Reverse String via StringBuilder:");
		long startTimeV3 = System.nanoTime();

		String reversedV3 = Strings.reverse(TEXT);

		displayExecutionTime(System.nanoTime() - startTimeV3);
		System.out.println("Reversed: \n" + reversedV3);
	}

	private static void displayExecutionTime(long time) {
		System.out.println("Execution time: " + time + " ns" + " ("
				+ TimeUnit.MILLISECONDS.convert(time, TimeUnit.NANOSECONDS) + " ms)");
	}
}
```