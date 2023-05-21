####Providing Access to Instance and Class Variables
Don't make any instance or class variable public without good reason. Often, instance variables don't need to be explicitly set or gotten-often that happens as a side effect of method calls.

One example of appropriate public instance variables is the case where the class is essentially a data structure, with no behavior. In other words, if you would have used a struct instead of a class.

####Referring to Class Variables and Methods
Avoid using an object to access a class (static) variable or method. Use a class name instead. For example:
```java
classMethod();             //OK
AClass.classMethod();      //OK
anObject.classMethod();    //AVOID!
```

####Constants
Numerical constants (literals) should not be coded directly, except for -1, 0, and 1, which can appear in a for loop as counter values.

####Variable Assignments
Avoid assigning several variables to the same value in a single statement. It is hard to read.
```java
if (c++ = d++) {        // AVOID! (Java disallows)
    ...
}
```
####Parentheses

It is generally a good idea to use parentheses liberally in expressions involving mixed operators to avoid operator precedence problems. Even if the operator precedence seems clear to you, it might not be to others-you shouldn't assume that other programmers know precedence as well as you do.

####Returning Values

Try to make the structure of your program match the intent. Example:
if (booleanExpression) {
    return true;
} else {
    return false;
}
should instead be written as
```java
return  
             booleanExpression;
```
```java
return (condition ? x : y);
```
If an expression containing a binary operator appears before the ? in the ternary ?: operator, it should be parenthesized

####Comments
Block Comments
Single-Line Comments
Trailing Comments
End-Of-Line Comments
Documentation Comments

####Declarations
#####Number Per Line
One declaration per line is recommended since it encourages commenting

####Class and Interface Declarations
When coding Java classes and interfaces, the following formatting rules should be followed:

No space between a method name and the parenthesis "(" starting its parameter list
Open brace "{" appears at the end of the same line as the declaration statement
Closing brace "}" starts a line by itself indented to match its corresponding opening statement, except when it is a null statement the "}" should appear immediately after the "{"

####try-catch Statements
```java
try {statements;
} catch (ExceptionClass e) {
statements;
} finally {
statements;
}
```