POJO
A plain old Java object (whose acronym is POJO) is a class that generally only has instance fields.
It's used to house data, and pass data, between functional classes.
It usually has few, if any methods other than getters and setters.
Many database frameworks use POJO's to read data from, or to write data to, databases, files or streams.
A POJO also might be called a bean, or a JavaBean. 
A JavaBean is just a POJO, with some extra rules applied to it. 
A POJO is sometimes called an Entity, because it mirrors database entities.  
Another acronym is DTO, for Data Transfer Object.
It's a description of an object, that can be modeled as just data.
IDE sllows us to generate getters, setters, and constructors in a uniform way.

```java
public class Student {
	private String admissionNumber;
	private String name;
	private String dateOfBirth;
	private String standard;
//to  generate getters and setters
// generating constructors through IDE
	public Student(String admissionNumber, String name, String dateOfBirth, 
			String standard) {
		super();
		this.admissionNumber = admissionNumber;
		this.name = name;
		this.dateOfBirth = dateOfBirth;
		this.standard = standard;
	}
	@Override
	public String toString() {
		return "Student [admissionNumber=" + admissionNumber + ", name=" + name 
				+ ", dateOfBirth=" + dateOfBirth
				+ ", standard=" + standard + "]";
	}
}
```
```java
public class StudentTest {

	public static void main(String[] args) {
		for (int i = 0; i <= 5; i++) {
			Student student = new Student("CCS1" + i, "Priya", "11-09-2000", "second");
			System.out.println(student);
		}

	}

}
```
