Employee Management System
Overview
The Employee Management System is a Java-based application that allows you to manage employee data such as adding, updating, and removing employees, as well as viewing employee details. This system uses MySQL for database management.

Features
Add new employees
Update existing employee information
View employee details
Remove employees from the system
Login functionality for system access
Splash screen during application launch
Technologies Used
Java: Core language for building the application
MySQL: Database for storing employee information
JDBC: To interact with the MySQL database
Swing: Java GUI for user interaction
Prerequisites
Before running the project, ensure you have the following installed:

Java JDK 8+
MySQL
IDE (Eclipse, IntelliJ, etc.)
Database Setup
Open MySQL and create a database:

sql
Copy code
CREATE DATABASE EmployeeDB;
Create a table for storing employee data:

sql
Copy code
USE EmployeeDB;

CREATE TABLE employee (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(100),
  age INT,
  department VARCHAR(100),
  salary DECIMAL(10, 2)
);
Project Setup
Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/employee-management-system.git
cd employee-management-system
Import the project into your preferred IDE (Eclipse, IntelliJ, etc.).

Update the Conn.java file with your MySQL credentials:

java
Copy code
public class Conn {
    Connection con;
    Statement stmt;

    public Conn() {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            con = DriverManager.getConnection("jdbc:mysql://localhost:3306/EmployeeDB", "yourUsername", "yourPassword");
            stmt = con.createStatement();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
Run the project from the Splash.java or Login.java file.

Code Example
Here is an example of how to add a new employee:

java
Copy code
// AddEmployee.java
import javax.swing.*;
import java.awt.event.*;
import java.sql.*;

public class AddEmployee extends JFrame implements ActionListener {
    JTextField t1, t2, t3, t4;
    JButton b1;

    AddEmployee() {
        // GUI code
        // ...

        b1 = new JButton("Submit");
        b1.addActionListener(this);
        add(b1);
        
        setLayout(null);
        setVisible(true);
    }

    public void actionPerformed(ActionEvent ae) {
        String name = t1.getText();
        int age = Integer.parseInt(t2.getText());
        String department = t3.getText();
        double salary = Double.parseDouble(t4.getText());

        try {
            Conn c = new Conn();
            String query = "INSERT INTO employee(name, age, department, salary) VALUES('" + name + "', " + age + ", '" + department + "', " + salary + ")";
            c.stmt.executeUpdate(query);
            JOptionPane.showMessageDialog(null, "Employee Added Successfully");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static void main(String[] args) {
        new AddEmployee();
    }
}
How to Contribute
Fork the repository.
Create a feature branch: git checkout -b feature/feature-name.
Commit your changes: git commit -m "Add some feature".
Push to the branch: git push origin feature/feature-name.
Open a pull request.
License
This project is licensed under the MIT License.

You can modify the Conn.java section with your actual database connection details and the project URL for the repository once you upload it.
Attaching the some of the snips of the project

![image](https://github.com/user-attachments/assets/66f2894e-3d87-4734-8d9a-ccdab81cec03)

![image](https://github.com/user-attachments/assets/ccaef0b9-8b7e-4af8-898b-890424559823)

![image](https://github.com/user-attachments/assets/3910e1c7-caf4-4519-8c7a-45d19915d650)

![image](https://github.com/user-attachments/assets/553222b0-1c54-4377-bf1a-b127e82a83eb)

![image](https://github.com/user-attachments/assets/4d015f9a-7b4e-4b51-a2d0-fbc5c3dc0d8c)

![image](https://github.com/user-attachments/assets/f7ab3d58-e064-406c-adb0-6a7b38cc0857)






