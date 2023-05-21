Polymorphism
Polymorphism simply means 'many forms’.
And as you've seen, some advantages of Polymorphism are:
It makes code simpler.
It encourages code extensibility.
```java
public class Animal {

    protected String type;
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

    private String earShape;
    private String tailShape;

    public Dog() {
        super("Mutt", "Big", 50);
    }

    public Dog(String type, double weight) {
        this(type, weight, "Perky", "Curled");
    }

    public Dog(String type, double weight, String earShape, String tailShape) {
        super(type, weight <  15 ? "small" : (weight < 35 ? "medium" : "large"),
                weight);
        this.earShape = earShape;
        this.tailShape = tailShape;
    }

    @Override
    public String toString() {
        return "Dog{" +
                "earShape='" + earShape + '\'' +
                ", tailShape='" + tailShape + '\'' +
                "} " + super.toString();
    }

    public void makeNoise() {

        if (type == "Wolf") {
            System.out.print("Ow Wooooo! ");
        }
        bark();
        System.out.println();
    }

    @Override
    public void move(String speed) {
        super.move(speed);
//        System.out.println("Dogs walk, run and wag their tail");
        if (speed == "slow") {
            walk();
            wagTail();
        } else {
            run();
            bark();
        }
        System.out.println();
    }

    private void bark() {
        System.out.print("Woof! ");
    }

    private void run() {
        System.out.print("Dog Running ");
    }

    private void walk() {
        System.out.print("Dog Walking ");
    }

    private void wagTail() {
        System.out.print("Tail Wagging ");
    }
}
```
```java
public class Fish extends Animal {

    private int gills;
    private int fins;

    public Fish(String type, double weight, int gills, int fins) {
        super(type, "small", weight);
        this.gills = gills;
        this.fins = fins;
    }

    private void moveMuscles() {
        System.out.print("muscles moving ");
    }

    private void moveBackFin() {
        System.out.print("backfin moving ");
    }

    @Override
    public void move(String speed) {
        super.move(speed);
        moveMuscles();
        if (speed == "fast") {
            moveBackFin();
        }
        System.out.println();
    }

    @Override
    public String toString() {
        return "Fish{" +
                "gills=" + gills +
                ", fins=" + fins +
                "} " + super.toString();
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

        Dog yorkie = new Dog("Yorkie", 15);
        doAnimalStuff(yorkie, "fast");
        Dog retriever = new Dog("Labrador Retriever", 65,
                "Floppy", "Swimmer");
        doAnimalStuff(retriever, "slow");

        Dog wolf = new Dog("Wolf", 40);
        doAnimalStuff(wolf, "slow");

        Fish goldie = new Fish("Goldfish", 0.25, 2, 3);
        doAnimalStuff(goldie, "fast");
    }

    public static void doAnimalStuff(Animal animal, String speed) {

        animal.makeNoise();
        animal.move(speed);
        System.out.println(animal);
        System.out.println("_ _ _ _");
    }
}
```