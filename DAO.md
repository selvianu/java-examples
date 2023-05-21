##### POJO
```java
public class Employee {
	private Integer id;
	private String name;
	private String designation;
	private Long basicSalary;

	public Employee() {

	}

	public Employee(Integer id, String name, String designation, Long basicSalary)
	{
		this.id=id;
		this.name=name;
		this.designation=designation;
		this.basicSalary=basicSalary;
	}

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getDesignation() {
		return designation;
	}

	public void setDesignation(String designation) {
		this.designation = designation;
	}

	public Long getBasicSalary() {
		return basicSalary;
	}

	public void setBasicSalary(Long basicSalary) {
		this.basicSalary = basicSalary;
	}

	@Override
	public String toString() {
		return "Employee [id=" + id + ", name=" + name + ", designation=" + designation + ", basicSalary=" + basicSalary
				+ "]";
	}

}
```
#### Connection Util
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConnectionUtil {

	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		getConnection();
	}

	public static Connection getConnection() throws ClassNotFoundException, SQLException {
		Class.forName("oracle.jdbc.driver.OracleDriver");
		Connection connection = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:XE", "system", "oracle");
		return connection;
	}

}
```

