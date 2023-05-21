#####Lambda expressions
Let's start with a simple example of how to sort a list of strings in prior versions of Java:
```java
List<String> names = Arrays.asList("peter", "anna", "mike", "xenia");

Collections.sort(names, new Comparator<String>() {
    @Override
    public int compare(String a, String b) {
        return b.compareTo(a);
    }
});
```
The static utility method Collections.sort accepts a list and a comparator in order to sort the elements of the given list. You often find yourself creating anonymous comparators and pass them to the sort method.

Instead of creating anonymous objects all day long, Java 8 comes with a much shorter syntax, lambda expressions:
```java
Collections.sort(names, (String a, String b) -> {
    return b.compareTo(a);
});
```
As you can see the code is much shorter and easier to read. But it gets even shorter:

```java
Collections.sort(names, (String a, String b) -> b.compareTo(a));
```
For one line method bodies you can skip both the braces {} and the return keyword. But it gets even shorter:
```java
names.sort((a, b) -> b.compareTo(a));
```
List now has a sort method. Also the java compiler is aware of the parameter types so you can skip them as well.
https://github.com/winterbe/java8-tutorial