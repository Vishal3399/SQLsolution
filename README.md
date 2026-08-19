Task 1:
Create and Select a Database

Query ---->
create database company_db
use company_db





Task 2:

Choose the Correct Data Types

Column         Suggested data type

Employee ID         int
Employee name     varchar(50)
Email             varchar(50)
Department        varchar(50)
Salary            decimal(10,2)
Joining date      date




Task 3:

Create a table named employees using the following rules:

employee_id should store whole numbers.
name should store up to 50 characters.
email should store up to 100 characters.
department should store up to 30 characters.
salary should support two digits after the decimal point.
joining_date should store a date.
Do not add constraints in this task.

Query ---->
create table employees(
    Employee_ID int,
    Employee_Name varchar(50),
    Email varchar(100),
    Department varchar(30),
    Salary decimal(10,2),
    Joining_Date date
)


After creating the table, check its structure.

Query ---->
Select * from employees




Task 4:

Insert Aman using a single-row INSERT.

Query ---->
insert into employees values (101, 'Aman', 'aman@gmail.com', 'IT', 45000, '2026-01-10')


Insert Priya and Rahul using one multiple-row INSERT.

Query ----->
insert into employees (Employee_ID, Employee_Name, Email, Department, Salary, Joining_Date) values 
               (102, 'Priya', 'priya@gmail.com', 'HR', 40000, '2026-02-15'),
              (103, "Rahul", 'rahul@gmail.com', 'Sales', 38000, '2026-03-12')





Task 5:

Display all employee information.

Query ---->
Select * from employees

Display only employee names.

query ---->
Select Employee_Name from employees

Display employee names and salaries.

Query ---->
Select Employee_Name, Salary from employees

Display email, name and department in that exact order.

Query ---->
Select Email, Employee_Name, Department from employees


Task 6:

Create another table named validated_employees.

Apply the following rules:

Employee ID must uniquely identify every employee.
Employee ID must be generated automatically.
Name cannot be missing.
Email cannot be duplicated.
The default department should be General.
Salary must be greater than or equal to zero.
Joining date should use the DATE data type.

Query ---->

create table validated_employees(
    Employee_ID int auto_increment primary key,
    Employee_Name varchar(50) not null,
    Email varchar(100) unique not null,
    Department varchar(30) default 'General',
    Salary decimal(10,2) check (Salary >= 0),
    Joining_Date date
)


Task 7:

Test 1: Valid Record

INSERT INTO validated_employees
    (name, email, department, salary, joining_date)
VALUES
    ('Sneha', 'sneha@gmail.com', 'IT', 52000, '2026-04-10');

Prediction: Accepted / Rejected Reason: Accepted


Test 2: Missing Name

INSERT INTO validated_employees
    (email, department, salary, joining_date)
VALUES
    ('kiran@gmail.com', 'Sales', 42000, '2026-04-12');

Prediction: Accepted / Rejected Constraint involved:   Rejected


Test 3: Duplicate Email

INSERT INTO validated_employees
    (name, email, department, salary, joining_date)
VALUES
    ('Ravi', 'sneha@gmail.com', 'HR', 39000, '2026-04-14');

Prediction: Accepted / Rejected Constraint involved:   Rejected


Test 4: Department Not Provided

INSERT INTO validated_employees
    (name, email, salary, joining_date)
VALUES
    ('Meera', 'meera@gmail.com', 48000, '2026-04-16');

Prediction: Accepted / Rejected Department stored:    Accepted


Test 5: Invalid Salary

INSERT INTO validated_employees
    (name, email, department, salary, joining_date)
VALUES
    ('Arjun', 'arjun@gmail.com', 'Finance', -5000, '2026-04-18');

Prediction: Accepted / Rejected Constraint involved:   Rejected





Final Task:

Create a students table using the following business requirements:

Student ID should be generated automatically.
Every student must have a name.
Two students cannot use the same email.
The default course should be SQL.
Marks must remain between 0 and 100.
Joining date should store a date.

Query ---->
CREATE TABLE students (
         student_id int AUTO_INCREMENT PRIMARY KEY,
         name varchar(50) NOT NULL,
         email varchar(100) UNIQUE,
         course varchar(30) DEFAULT 'SQL',
         marks int CHECK (marks BETWEEN 0 AND 100),
         joining_date date
    );


1. Insert one student with all values 

Query ---->
INSERT INTO students (name, email, course, marks, joining_date)
VALUES ('Kavya', 'kavya@gmail.com', 'Python', 88, '2026-05-01');


2. Insert another student without providing the course

Query ---->
INSERT INTO students (name, email, marks, joining_date)
VALUES ('Rohan', 'rohan@gmail.com', 76, '2026-05-03');


3. Display all students

Query ---->
SELECT * FROM students
