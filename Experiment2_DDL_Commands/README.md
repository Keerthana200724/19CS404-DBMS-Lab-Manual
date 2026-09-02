Experiment 2: DDL Commands
AIM

To study and implement DDL commands and different types of constraints.
THEORY
1. CREATE

Used to create a new relation (table).

Syntax:

CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);

2. ALTER

Used to add, modify, drop, or rename fields in an existing relation. (a) ADD

ALTER TABLE std ADD (Address CHAR(10));

(b) MODIFY

ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));

(c) DROP

ALTER TABLE relation_name DROP COLUMN field_name;

(d) RENAME

ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;

3. DROP TABLE

Used to permanently delete the structure and data of a table.

DROP TABLE relation_name;

4. RENAME

Used to rename an existing database object.

RENAME TABLE old_relation_name TO new_relation_name;

CONSTRAINTS

Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
1. NOT NULL

When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);

2. UNIQUE

Ensures that values in a column are unique. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);

3. CHECK

Specifies a condition that each row must satisfy. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);

4. PRIMARY KEY

Used to uniquely identify each record in a table. Properties: Must contain unique values. Cannot be null. Should contain minimal fields. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);

5. FOREIGN KEY

Used to reference the primary key of another table. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);

6. DEFAULT

Used to insert a default value into a column if no value is specified.

Syntax:

CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);

Question 1

Create a table named Products with the following constraints: ProductID as INTEGER should be the primary key. ProductName as TEXT should be unique and not NULL. Price as REAL should be greater than 0. StockQuantity as INTEGER should be non-negative.

-- create table Products(
ProductID integer primary key,
ProductName text not null unique,
Price real check(Price>0),
StockQuantity integer check(StockQuantity>=0)
);

Output:

Question 2

Write a SQL Query for inserting the below values in the table Customers

ID NAME AGE ADDRESS SALARY

1 Ramesh 32 Ahmedabad 2000 2 Khilan 25 Delhi 1500 3 Kaushik 23 Kota 2000

insert into Customers(ID,NAME,AGE,ADDRESS,SALARY)
values(1,"Ramesh",32,"Ahmedabad",2000),(2,"Khilan",25,"Delhi",1500),(3,"Kaushik",23,"Kota",2000)

Output:
Screenshot 2026-02-02 133135
Question 3

Write a SQL Query to change the name of attribute "name" to "first_name" and add mobilenumber as number ,DOB as Date in the table Companies.

alter table Companies rename column name to first_name;
alter table Companies add mobilenumber number;
alter table Companies add column DOB Date;

Output:
Screenshot 2026-02-02 133156
Question 4

Write a SQL query to Add a new column Mobilenumber as number in the Student_details table.

Sample table: Student_details

cid name type notnu dflt_value pk

0 RollNo int 0 1 1 Name VARCHAR(100) 1 0 2 Gender TEXT 1 0 3 Subject VARCHAR(30) 0 0 4 MARKS INT (3) 0 0

alter table Student_details add column Mobilenumber number;

Output:
Screenshot 2026-02-02 133226
Question 5

Create a table named Customers with the following columns:

CustomerID as INTEGER Name as TEXT Email as TEXT JoinDate as DATETIME

create table Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME);

Output:
Screenshot 2026-02-02 133242
Question 6

create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

create table jobs(
job_id,
job_title default"",
min_salary integer default 8000,
max_salary integer);

Output:
Screenshot 2026-02-02 133307
Question 7

Create a table named Shipments with the following constraints: ShipmentID as INTEGER should be the primary key. ShipmentDate as DATE. SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID). OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

create table Shipments (
ShipmentID integer primary key,
ShipmentDate date,
SupplierID integer,
OrderID integer,
FOREIGN KEY (SupplierID) references Suppliers(SupplierID),
FOREIGN KEY (OrderID) references Orders(OrderID)
);

Output:
Screenshot 2026-02-02 133321
Question 8

Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID Name Position

4 Emily White Analyst

Note: The Department and Salary columns will use their default values.

insert into Employee(EmployeeID,Name,Position)
values(4,"Emily White","Analyst");

Output:
Screenshot 2026-02-02 133335
Question 9

Create a table named Invoices with the following constraints: InvoiceID as INTEGER should be the primary key. InvoiceDate as DATE. Amount as REAL should be greater than 0. DueDate as DATE should be greater than the InvoiceDate. OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

create table Invoices(
InvoiceID integer primary key,
InvoiceDate fate,
Amount real check(Amount>0),
DueDate date check(DueDate>InvoiceDate),
OrderID integer,
foreign key (OrderID) references Orders(OrderID));

Output:
Screenshot 2026-02-02 133352
Question 10

Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

insert into Books select * from Out_of_print_books

Output:
Screenshot 2026-02-02 133405
RESULT

Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
