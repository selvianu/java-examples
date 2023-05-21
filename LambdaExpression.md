```java
// Filter example
String[] input = {"tiger", "cat", "TIGER", "Tiger", "leopard"};
List<String> cats = Arrays.asList(input);
String search = "tiger";
  // filter takes a lambda expression which takes in a string and returns a Boolean value
  // this is applied over the whole collection cats
String tigers = cats.stream()
                    .filter(s -> s.equalsIgnoreCase(search))
                    .collect(Collectors.joining(", "));
System.out.println(tigers);


// Map Example
/*
* The map idiom in Java 8 makes use of a new interface Function<T, R> in the package java.util.function. 
* Like Predicate<T>, this is a functional interface, and so only has one nondefaulted method, apply(). 
* The map idiom is about transforming a collection of one type in a collection of a potentially different type.
*/
List<Integer> namesLength = cats.stream()
                .map(String::length)
                .collect(Collectors.toList());
System.out.println(namesLength);



// ForEach Example
List<String> pets =
  Arrays.asList("dog", "cat", "fish", "iguana", "ferret");
pets.stream().forEach(System.out::println);


// Reduce example
/*
* takes 2 arguments: initial value, and a function to apply step by step
* It can help to imagine it works a bit like this:
public T reduce(T identity, BinaryOperator<T> aggregator) {
    T runningTotal = identity;
    for (T element : myStream) {
        runningTotal = aggregator.apply(runningTotal, element);
    }
    return result;
}
*/
double sumPrimes = ((double)Stream.of(2, 3, 5, 7, 11, 13, 17, 19, 23)
       .reduce(0, (x, y) -> {return x + y;}));
System.out.println("Sum of some primes: " + sumPrimes);
```