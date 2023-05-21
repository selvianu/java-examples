```java
public class Car {
	private String make;
	private String model;
	private String color;
	private int noOfDoors;
	private boolean convertible;

	public void describeCar() {
		System.out.println("Make : " + make + " Model : " + model + " Color : " + color + "Doors : " + noOfDoors);

	}
}
```

```java
public class CarTest {

	public static void main(String[] args) {

		Car car = new Car();
		car.describeCar();
	}

}
```

* Fields with primitive data types are never null.
  
