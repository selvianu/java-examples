#### JDBC - CRUD Operations
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.Scanner;

public class ConnectionUtil2 {

	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		// int rows = insertLoginDetails();
		// System.out.println(rows);
		// insertLoginDetails();
		// int i = insertProduct();
		// System.out.println(i);
		// productsName();
		// productsNameCost();
		// productListGreater();
		productList();
	}

	public static Connection getJDBC() throws ClassNotFoundException, SQLException {
		Class.forName("oracle.jdbc.driver.OracleDriver");
		Connection connection = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:XE", "system", "oracle");
		return connection;
	}

	public static Connection getConnection() throws ClassNotFoundException, SQLException {
		Class.forName("oracle.jdbc.driver.OracleDriver");
		Connection connection = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:XE", "system", "oracle");
		return connection;
	}

	public static void productList() throws ClassNotFoundException, SQLException {
		Connection con = getJDBC();
		// String query = "select * from product_ck"; - not recommended
		String query = "select p_id,p_name,price from product_ck";

		PreparedStatement ps = con.prepareStatement(query);
		ResultSet rs = ps.executeQuery();
		while (rs.next()) {
			// System.out.println("Product id : " + rs.getInt(1) + " Product Name : " +
			// rs.getString(2)
			// + " Product price :" + rs.getInt(3));

			int pId = rs.getInt(1);
			String name = rs.getString(2);
			Integer cost = rs.getInt(3);
			ArrayList list = new ArrayList();
			list.add(pId);
			list.add(name);
			list.add(cost);
			System.out.println(list);
		}
		rs.close();
		ps.close();
		con.close();
	}

	public static void productsName() throws ClassNotFoundException, SQLException {
		Connection con = getJDBC();
		String query = "select  p_name from product_ck";
		PreparedStatement ps = con.prepareStatement(query);
		ResultSet rs = ps.executeQuery();
		while (rs.next()) {
			System.out.println("Product Name : " + rs.getString(1));
		}
	}

	public static void productsNameCost() throws ClassNotFoundException, SQLException {
		Connection con = getJDBC();
		String query = "select price from product_ck";
		PreparedStatement ps = con.prepareStatement(query);
		ResultSet rs = ps.executeQuery();
		while (rs.next()) {
			System.out.println("Product cost : " + rs.getInt(1));
		}

	}

	public static void productListGreater() throws ClassNotFoundException, SQLException {
		Connection con = getJDBC();
		String query = "select  * from product_ck where price>30000";
		PreparedStatement ps = con.prepareStatement(query);
		ResultSet rs = ps.executeQuery();
		while (rs.next()) {
			System.out.println("Product ID : " + rs.getInt(1) + "Product Name : " + rs.getString(2) + "Product Cost : "
					+ rs.getInt(3));
		}
	}

	public static int insertLoginDetails() throws ClassNotFoundException, SQLException {
		// query
		// use conection
		// conn object with statement and pass the query.
		// preparedStatemt objet -->Execute sql command
		// String query = "insert into login(username, password)
		// values('Ramya','ramya@123')";
		// String query = "insert into login(username, password)
		// values('Ramya','ramya@123'),()";

		return insertToSave();

	}

	public static int insertToSave() throws ClassNotFoundException, SQLException {
		String query = "insert into login(username, password) values(?,?)";
		Connection conn = getJDBC();
		PreparedStatement ps = conn.prepareStatement(query);
		// ps.setString(1, "abi");
		// ps.setString(2, "abi@123");
		Scanner s = new Scanner(System.in);
		System.out.println("enter user name");
		String name = s.next();
		String userPassword = "riya@123";
		ps.setString(1, name);
		ps.setString(2, userPassword);
		ps.setInt(1, 0);
		ps.setLong(0, 0);
		ps.setBoolean(0, false);
		ps.setFloat(0, 0);

		int rows = ps.executeUpdate();// DML
		return rows;
	}

	public static int insertProduct() throws ClassNotFoundException, SQLException {
		String q = "INSERT INTO product_ck(p_id,p_name, price)VALUES(1,'Mobile',45000)";
		Connection con = getJDBC();
		PreparedStatement ps = con.prepareStatement(q);
		int i = ps.executeUpdate();
		return i;
	}

	public static int deleteProduct() throws ClassNotFoundException, SQLException {
		// delete from product_ck where p_id=11;
		String q1 = "delete from product_ck where p_id=12";
		Connection con = getJDBC();
		System.out.println("Connection obj " + con);
		PreparedStatement ps = con.prepareStatement(q1);
		System.out.println("Query invoked");
		int i = ps.executeUpdate();
		System.out.println("Completed");
		return i;

	}
}
```