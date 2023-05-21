Inheritance
We can look at Inheritance as a form of code re-use.
It's a way to organize classes into a parent-child hierarchy, which lets the child inherit (re-use), fields and methods from its parent.
Using "extends" specifies the superclass (or the parent class) of the class we're declaring.
A class can specify one, and only one, class in its extends clause.
Code Re-use
All subclasses can execute methods, even though the code is declared on the parent class. 
The code doesn't have to be duplicated in each subclass.
We can use code, from the parent.
Or we can change that code for the subclass. 

```java
public class Animal {

    private String type;
    private String size;
    private double weight;

    public Animal() {

    }

    public Animal(String type, String size, double weight) {
        this.type = type;
        this.size = size;
        this.weight = weight;
    }

    @Override
    public String toString() {
        return "Animal{" +
                "type='" + type + '\'' +
                ", size='" + size + '\'' +
                ", weight=" + weight +
                '}';
    }

    public void move(String speed) {
        System.out.println(type + " moves " + speed);
    }

    public void makeNoise() {
        System.out.println(type + " makes some kind of noise");
    }
}
```
```java
public class Dog extends Animal {

    public Dog() {
        super("Mutt", "Big", 50);
    }
}
```
```java
public class Main {

    public static void main(String[] args) {

        Animal animal = new Animal("Generic Animal", "Huge", 400);
        doAnimalStuff(animal, "slow");

        Dog dog = new Dog();
        doAnimalStuff(dog, "fast");
    }

    public static void doAnimalStuff(Animal animal, String speed) {

        animal.makeNoise();
        animal.move(speed);
        System.out.println(animal);
        System.out.println("_ _ _ _");
    }
}
```