# Spring Jdbc Template

#### Prerequisites
* **Dependencies**: spring-jdbc, oracle

#### Task 1: Database Credentials
* application.properties
```java
spring.datasource.driverClassName=oracle.jdbc.driver.OracleDriver
spring.datasource.url=jdbc:oracle:thin:@localhost:1521:XE
spring.datasource.username=system
spring.datasource.password=oracle
```

#### Task 2: Define JdbcTemplate Bean
```java

@Configuration
public class DataSourceConfiguration {

  @Bean
  public JdbcTemplate jdbcTemplate(DataSource dataSource) {
    JdbcTemplate jdbcTemplate = new JdbcTemplate(dataSource);
    return jdbcTemplate;
  }
}
```

##### Task 3: Insert Query

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;

public class BookDAO {

	@Autowired
	JdbcTemplate jdbcTemplate;
	
	
	public void addBook(String bookName) {
		String sql= "insert into books(title) values ( ?)";
		Object[] params = { bookName };
		int rows = jdbcTemplate.update(sql, params);
		
	}
	
	
}

```

##### Task 4: Select Query
```java
package dao;
 
import java.util.List;
 
import org.springframework.jdbc.core.JdbcTemplate;
 
import model.QuestionType;
import util.ConnectionUtil;
 
public class QuestionTypeDAO {
 
    private static JdbcTemplate jdbcTemplate = ConnectionUtil.getJdbcTemplate();
 
    public static void insert(String name) {
        String sql = "insert into seed_question_type ( name ) values ( ? ) ";
        int rows = jdbcTemplate.update(sql, name);
        System.out.println("Insert:" + sql + ", no of rows inserted: " + rows);
    }
 
    public static void update(int id, String name) {
        String sql = "update seed_question_type set name=? where id = ?";
        int rows = jdbcTemplate.update(sql, name, id);
        System.out.println("Update:" + sql + ", no of rows update:" + rows);
    }
 
    public static void delete(int id) {
        String sql = "delete from seed_question_type where id = ? ";
        int rows = jdbcTemplate.update(sql, id);
        System.out.println("Delete :" + sql + ", no of rows delete:" + rows);
    }
 
    public static List<QuestionType> findAll() {
        String sql = "select id,name from seed_question_type";
        System.out.println("FindAll:" + sql);
 
        List<QuestionType> list = jdbcTemplate.query(sql, (rs, rowNum) -> {
            QuestionType qt = new QuestionType();
            qt.id = rs.getInt("id");
            qt.name = rs.getString("name");
            return qt;
        });
        return list;
    }
 
    public static QuestionType findByQuestionType(String name) {
        String sql = "select id,name from seed_question_type where name= ?";
        System.out.println("FindByName:" + sql);
 
        QuestionType q = jdbcTemplate.queryForObject(sql, (rs, rowNum) -> {
            QuestionType qt = new QuestionType();
            qt.id = rs.getInt("id");
            qt.name = rs.getString("name");
            return qt;
        });
        return q;
    }
}
```