Static vs. Instance Methods
Static methods are declared using a static modifier.
Static methods can't access instance methods and instant variables directly.
They're usually used for operations that don't require any data from an instance of the class (from 'this').
If you remember, the this keyword is the current instance of a class.
So inside a static method, we can't use the this keyword.
Whenever you see a method that doesn't use instance variables, that method should probably be declared as a static method.
For example, main is a static method, and it's called by the Java virtual machine when it starts the Java application.

Instance methods belong to an instance, of a class.
To use an instance method, we have to instantiate the class first, usually by using the new keyword.
Instance methods can access instance methods and instance variables directly.
Instance methods can also access static methods and static variables directly.
![static Vs instance method](staticVsinstance.bmp)  

```java
public class Dog {
	private static String name;

	public Dog(String name) {
		this.name = name;
	}

	public void printName() {
		System.out.println(name);
	}
}
```
```java
public class DogTest {

	public static void main(String[] args) {

		Dog d=new Dog("tom");
		Dog d1=new Dog("Jim");
		d.printName();//Jim
		d1.printName();//Jim
		//Static variables are shared between instances
		
	}

}
```