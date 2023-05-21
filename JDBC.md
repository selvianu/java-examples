```java
package com.training.util;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class ConnectionUtil 
{
	public static void main(String[] args) throws ClassNotFoundException, SQLException
	{
		getConnection();
		//insertEmployee();
		//udpdateEmployee();
		//deleteEmployee();
}
public static Connection getConnection() throws ClassNotFoundException, SQLException
{
Class.forName("com.mysql.jdbc.Driver");
Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3306/employeedetails","root","Vais");
//System.out.println(con);
return con;
}
public static void insertEmployee() throws ClassNotFoundException, SQLException
{
Connection con = ConnectionUtil.getConnection();
String s1 = "INSERT INTO employee VALUES(5, 'Kala',30,'MedicalRep')";
PreparedStatement ps = con.prepareStatement(s1);
int executeUpdate = ps.executeUpdate(); 
System.out.println(executeUpdate);
}
public static void updateEmployee() throws ClassNotFoundException, SQLException 
{
Connection con = ConnectionUtil.getConnection();
String s2 = "UPDATE employee SET EmpName = 'kavitha' WHERE EmpId = 4";
PreparedStatement ps1 = con.prepareStatement(s2);
int executeUpdate = ps1.executeUpdate(); 
System.out.println(executeUpdate);
}
public static void deleteEmployee() throws ClassNotFoundException, SQLException 
{
Connection con = ConnectionUtil.getConnection();
String s3 = "DELETE FROM employee WHERE EmpId = 5";
PreparedStatement ps2 = con.prepareStatement(s3);
int executeUpdate = ps2.executeUpdate(); 
System.out.println(executeUpdate);
}
}
```