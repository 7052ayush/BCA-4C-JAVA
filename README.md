# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-

import java.util.Scanner;

public class Employee {
    private String nameOfEmp;
    private int empId;
    private double basicSalary;
    private double grossSalary;

    public Employee(String nameOfEmp, int empId, double basicSalary) {
        this.nameOfEmp = nameOfEmp;
        this.empId = empId;
        this.basicSalary = basicSalary;
        calculateGrossSalary();
    }

    private void calculateGrossSalary() {
        double hra = 0.25 * basicSalary; // HRA is 25% of BasicSalary
        double da = 0.4 * basicSalary;   // DA is 40% of BasicSalary
        grossSalary = basicSalary + hra + da;
    }

    public String getNameOfEmp() {
        return nameOfEmp;
    }

    public int getEmpId() {
        return empId;
    }

    public double getGrossSalary() {
        return grossSalary;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Employee[] employees = new Employee[3]; // Assuming there are 3 employees
        
        // Input employee details
        for (int i = 0; i < employees.length; i++) {
            System.out.println("Enter details for Employee " + (i + 1) + ":");
            System.out.print("Name: ");
            String name = scanner.nextLine();
            System.out.print("Employee ID: ");
            int empId = scanner.nextInt();
            System.out.print("Basic Salary: ");
            double basicSalary = scanner.nextDouble();
            scanner.nextLine(); // Consume newline
            employees[i] = new Employee(name, empId, basicSalary);
        }
        
        // Display employees whose name starts with a consonant
        System.out.println("\nEmployees whose name starts with a consonant:");
        for (Employee employee : employees) {
            if (!isVowel(employee.getNameOfEmp().charAt(0))) {
                System.out.println("Name: " + employee.getNameOfEmp() + ", Gross Salary: " + employee.getGrossSalary());
            }
        }

        // Display employees whose EmpId is between 101 and 150
        System.out.println("\nEmployees whose EmpId is between 101 and 150:");
        for (Employee employee : employees) {
            if (employee.getEmpId() >= 101 && employee.getEmpId() <= 150) {
                System.out.println("EmpId: " + employee.getEmpId() + ", Gross Salary: " + employee.getGrossSalary());
            }
        }

        // Count employees whose GrossSalary is less than 35000/-
        int count = 0;
        for (Employee employee : employees) {
            if (employee.getGrossSalary() < 35000) {
                count++;
            }
        }
        System.out.println("\nTotal number of employees whose GrossSalary is less than 35000/-: " + count);

        scanner.close();
    }

    private static boolean isVowel(char ch) {
        ch = Character.toLowerCase(ch);
        return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u';
    }
