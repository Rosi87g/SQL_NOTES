# SQL & DATABASE FUNDAMENTALS

### Complete Course Notes

*From Data Fundamentals to Keys & Constraints — Definitions, Diagrams, Tables, SQL Examples and Interview Questions*

---

## 📚 Table of Contents

- [Chapter 1 — Data: The New Fuel](#data-the-new-fuel)
- [Chapter 2 — Understanding DBMS, RDBMS and SQL](#understanding-dbms-rdbms-and-sql)
- [Chapter 3 — SQL Command Categories](#sql-command-categories)
- [Chapter 4 — Database, Schema, Table, Row and Column](#database-schema-table-row-and-column)
- [Chapter 5 — Installing MySQL Server and MySQL Workbench](#installing-mysql-server-and-mysql-workbench)
- [Chapter 6 — SQL Data Types](#sql-data-types)
- [Chapter 7 — Modifying Database Structure](#modifying-database-structure)
- [Chapter 8 — Keys and Constraints](#keys-and-constraints)
- [Chapter 9 — DML: Managing Data (INSERT, UPDATE, DELETE)](#dml-managing-data-insert-update-delete)

---

# Chapter 1 — Data: The New Fuel

You use data every single day — you just never called it that. The photos on your phone, a friend's contact number, your bank balance, last night's match score — all of it is data: small pieces of information about the world.

## 1.1 What Is Data?

*Data is a collection of raw facts, figures, and details — such as numbers, text, or dates — that describe something. On its own, data has no meaning; it becomes information once it is organized and given context.*

Example: your friend's contact card.

| Field | Value |
| --- | --- |
| Name | Rahul |
| Number | 98765 43210 |
| City | Bangalore |

**Data vs Information (a favourite interview question): **data is the raw fact (the number 25); information is data with meaning ("Rahul is 25 years old").

## 1.2 Why Is Data Called "the New Fuel"?

A hundred years ago, the most valuable resource was oil — it powered cars, factories, and entire economies. Today, the most valuable resource is data. Google knows what you search, Amazon knows what you buy, Netflix knows what you watch and uses it to decide what to recommend next. The biggest companies in the world don't just sell products — their real treasure is the data they hold about people. Just as oil powered the last century, data powers this one.

## 1.3 Types of Data

Data comes in three types, depending on how neat and organized it is.

### 1. Structured Data

Data that fits perfectly into rows and columns, like a table. Every piece has a clear, labelled place.

| RollNo | Name | City | Marks |
| --- | --- | --- | --- |
| 1 | Rahul | Bangalore | 85 |
| 2 | Priya | Mysore | 92 |
| 3 | Amit | Bangalore | 78 |

**More examples: **bank transaction records, an Excel sheet of products, an employee list.

### 2. Unstructured Data

Data with no fixed shape — it cannot be squeezed into rows and columns.

- A photo from a birthday party
- A WhatsApp voice note
- A YouTube video
- A free-text message such as "Hey, are we still meeting tomorrow?"

**More examples: **images, videos, audio files, social media posts, PDF documents.

### 3. Semi-structured Data

Not a neat table, but not a total mess either — it has some structure (labels or tags) without being a rigid table.

An email has fields (From, To, Subject) but a free-text Body:

```
From:    ajay@kod.com
To:      anuj@kod.com
Subject: Meeting Tomorrow
Body:    Hi Anuj, are we still on for the project
         meeting tomorrow at 4 PM? Let me know!
```

A JSON snippet is another common example — labelled fields, but not a rigid table:

```json
{
  "name": "Rahul",
  "city": "Bangalore",
  "age": 25
}
```

**More examples: **XML files, NoSQL documents.

| Type | Shape | Real-life analogy | Examples |
| --- | --- | --- | --- |
| Structured | Fixed rows & columns | A filled-in form | Excel sheet, SQL table |
| Unstructured | No fixed format | A handwritten diary | Photos, videos, audio |
| Semi-structured | Partly tagged | A form with an "anything else?" box | Email, JSON, XML |

> 💡 Why This Matters
> All this data — neat or messy — has to be stored, organized so it can be found again, and protected so it isn't lost. Companies hold billions of records, and different types of data are stored and handled differently. Learning to store, organize, and work with data (which is exactly what SQL and databases do) is a skill that sits underneath almost every app and company in the world.

## 1.4 Interview Questions — Chapter 1

**Q1. What do you understand by "data"?**

***Ideal answer: ****Data is a collection of raw facts and figures — like numbers, text, or dates — that describe something. On its own it's just a fact; it becomes useful information once it is organized and given context.*

**Q2. What is the difference between data and information?**

***Ideal answer: ****Data is the raw fact with no meaning by itself — e.g., the number 25. Information is data given context and meaning — e.g., "Rahul is 25 years old." Information is processed, organized data.*

**Q3. What are the different types of data?**

***Ideal answer: ****Three types: Structured (fits rows & columns, e.g. a marks table), Unstructured (no fixed format, e.g. images, videos, free text), and Semi-structured (in between, has some tags but isn't a strict table, e.g. email, JSON).*

**Q4. Give an example of structured versus unstructured data.**

***Ideal answer: ****A table of customer names, cities, and phone numbers is structured — it fits perfectly into rows and columns. A folder of photos or WhatsApp voice notes is unstructured — real data, but with no fixed row-and-column format.*

*Interview tip: for "types of X" questions, name all the types first, then give one example each — naming shows breadth, examples show understanding. For any "what is X" question, give the clean definition first, then a quick real-life example.*

# Chapter 2 — Understanding DBMS, RDBMS and SQL

Applications generate and use huge amounts of data. That data has to be stored, retrieved, updated, and protected efficiently. DBMS, RDBMS, and SQL work together to make this possible.

*The relationship in one line: A database stores the data, an RDBMS manages relational databases, and SQL is the language used to communicate with the RDBMS.*

## 2.1 What Is a Database?

A database is an organized collection of related data. For example, a college database may store:

- Student details
- Course details
- Attendance
- Examination marks
- Placement information

A database contains the data, but software is required to manage it — that software is called a DBMS.

## 2.2 What Is a DBMS?

**DBMS** stands for **Database Management System**. It is software that allows you to create, store, retrieve, update, and delete data in a database. A DBMS provides an interface between:

- The user or application
- The stored data

Without a DBMS, applications would need to manage stored data directly.

### Responsibilities of a DBMS

A DBMS helps you:

- Create databases
- Store data
- Retrieve required data
- Modify existing data
- Remove unwanted data
- Control access to data
- Protect data from unauthorized users
- Maintain consistency
- Support backup and recovery

Examples of database management systems: MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server, SQLite, MongoDB. These systems do not all store data using the same model — systems based on the relational model are called RDBMSs.

## 2.3 What Is an RDBMS?

**RDBMS** stands for **Relational Database Management System**. An RDBMS is a type of DBMS that stores data in related tables. Each table contains:

- **Columns** — the properties or attributes of the data
- **Rows** — the individual records
- **Keys** — columns used to identify and connect records
### Example — a Students table

| StudentID | StudentName | Branch |
| --- | --- | --- |
| 101 | Aarav | CSE |
| 102 | Bhavna | ECE |
| 103 | Charan | CSE |

- Students is the table.
- StudentID, StudentName and Branch are columns.
- Each student is represented by one row.
- StudentID can uniquely identify each student.
### Relationships Between Tables

Suppose the database also contains a Marks table:

| MarkID | StudentID | Subject | Score |
| --- | --- | --- | --- |
| 1 | 101 | SQL | 85 |
| 2 | 102 | SQL | 78 |
| 3 | 101 | Python | 90 |

The StudentID column connects the Students and Marks tables. This relationship lets the database answer questions such as:

- What marks did Aarav receive?
- Which students scored above 80?
- What is the average score of each student?
### Important Features of an RDBMS

- Data is organized into tables.
- Every table can have a primary key.
- Tables can be connected using foreign keys.
- Constraints maintain valid data.
- Duplicate and inconsistent data can be reduced.
- Multiple users can work with the database.
- Transactions help maintain data consistency.

Examples of RDBMSs: MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server, SQLite.

## 2.4 DBMS vs RDBMS

*RDBMS is not separate from DBMS — it is a specialized type of DBMS. Every RDBMS is a DBMS, but every DBMS is not necessarily an RDBMS.*

| DBMS | RDBMS |
| --- | --- |
| General term for software that manages databases | A DBMS based on the relational model |
| Can use different data models | Organizes data into related tables |
| Relationships are not required in every model | Relationships are established using keys |
| Structure depends on the database model | Uses rows, columns, tables and constraints |
| Examples include relational and non-relational systems | Examples include MySQL, PostgreSQL and Oracle Database |

## 2.5 What Is SQL?

**SQL** stands for **Structured Query Language**. SQL is the language used to communicate with a relational database management system. You write SQL commands, and the RDBMS executes them on the database.

SQL can be used to:

- Create databases and tables
- Insert records
- Retrieve records
- Filter and sort data
- Update records
- Delete records
- Combine data from multiple tables
- Calculate totals and averages
- Control user permissions
- Manage transactions
### Examples of SQL Commands

Create a table:

```sql
CREATE TABLE Students (
  StudentID   INT PRIMARY KEY,
  StudentName VARCHAR(50),
  Branch      VARCHAR(20)
);
```

Insert a record:

```sql
INSERT INTO Students
VALUES (101, 'Aarav', 'CSE');
```

Retrieve records:

```sql
SELECT *
FROM Students;
```

Update a record:

```sql
UPDATE Students
SET Branch = 'ISE'
WHERE StudentID = 101;
```

Delete a record:

```sql
DELETE FROM Students
WHERE StudentID = 101;
```

## 2.6 How They Work Together

Suppose a college wants to manage student data:

1. The student information is stored in a database.
1. MySQL manages that database, so MySQL is the RDBMS.
1. You write SQL commands to create, retrieve, and modify the data.

| Term | Role in the College Application |
| --- | --- |
| Database | Contains student, course and marks data |
| DBMS | Software that manages the database |
| RDBMS | Manages data using related tables |
| MySQL | The RDBMS being used |
| SQL | Language used to communicate with MySQL |

### SQL and MySQL Are Not the Same

- **SQL** is a language.
- **MySQL** is an RDBMS that understands SQL.

Other RDBMSs — such as PostgreSQL, Oracle Database, and SQL Server — also use SQL, though their syntax may differ slightly for some operations.

*A useful comparison: SQL is the language, while MySQL is the software that understands and executes that language.*

### Common Confusions, Cleared Up

| Question | Answer |
| --- | --- |
| Is a database the same as a DBMS? | No. A database contains the data. A DBMS is the software used to manage that data. |
| Are DBMS and RDBMS opposites? | No. RDBMS is one type of DBMS. |
| Is SQL a database? | No. SQL is a language used to work with relational databases. |
| Is MySQL a programming language? | No. MySQL is an RDBMS. It accepts and executes SQL commands. |
| Can SQL be used with every database? | SQL is mainly used with relational databases. Non-relational databases may use different query languages or APIs. |

# Chapter 3 — SQL Command Categories

SQL can perform many different types of operations. To make these operations easier to understand, SQL commands are divided into five main categories, each with a specific responsibility.

- DDL — Data Definition Language
- DML — Data Manipulation Language
- DQL — Data Query Language
- DCL — Data Control Language
- TCL — Transaction Control Language
## 3.1 DDL — Data Definition Language

DDL is used to define and manage the structure of a database. It works with databases, tables, columns, data types, constraints, and other database objects.

Common DDL commands:

| Command | Purpose |
| --- | --- |
| CREATE | Creates a new database, table, or object |
| ALTER | Changes the structure of an existing table |
| RENAME | Renames a table or column |
| TRUNCATE | Removes all rows from a table, keeping its structure |
| DROP | Permanently deletes a table or database |

*Simple understanding: DDL creates or changes the structure that will hold the data.*

## 3.2 DML — Data Manipulation Language

DML is used to manage the records stored inside database tables. It lets you add new records, modify existing records, and remove selected records.

| Command | Purpose |
| --- | --- |
| INSERT | Adds new records to a table |
| UPDATE | Modifies existing records |
| DELETE | Removes selected records |

*Simple understanding: DML works with the data stored inside the structure.*

## 3.3 DQL — Data Query Language

DQL is used to retrieve information from a database. It lets you view stored records, search for required information, filter and sort records, calculate summaries, and combine information from different tables.

The main DQL command is SELECT.

```sql
SELECT column1, column2
FROM table_name
WHERE condition;
```

*Simple understanding: DQL asks questions about the stored data.*

## 3.4 DCL — Data Control Language

DCL is used to control access to databases and tables. It determines who can access the database, what data a user can view, what operations a user can perform, and which permissions should be removed.

| Command | Purpose |
| --- | --- |
| GRANT | Gives a user specific permissions |
| REVOKE | Removes previously granted permissions |

*Simple understanding: DCL controls who is allowed to use the data.*

## 3.5 TCL — Transaction Control Language

TCL is used to manage related database changes as a single transaction. It lets you permanently save changes, cancel changes, create checkpoints during a transaction, and keep multi-step operations consistent.

| Command | Purpose |
| --- | --- |
| COMMIT | Permanently saves all changes made in the transaction |
| ROLLBACK | Cancels changes made in the transaction |
| SAVEPOINT | Creates a checkpoint within a transaction to roll back to |

*Simple understanding: TCL decides whether related changes should be saved or cancelled.*

## 3.6 How the Categories Connect

Imagine you are building a student management database:

| Category | Responsibility |
| --- | --- |
| DDL | Creates the database and table structures |
| DML | Adds or changes student records |
| DQL | Retrieves required student information |
| DCL | Controls who can access the information |
| TCL | Saves or cancels related changes |

### Quick Comparison Table

| Category | Full Form | Main Purpose | Key Commands |
| --- | --- | --- | --- |
| DDL | Data Definition Language | Defines database structure | CREATE, ALTER, DROP, TRUNCATE, RENAME |
| DML | Data Manipulation Language | Manages stored records | INSERT, UPDATE, DELETE |
| DQL | Data Query Language | Retrieves information | SELECT |
| DCL | Data Control Language | Controls permissions | GRANT, REVOKE |
| TCL | Transaction Control Language | Manages transactions | COMMIT, ROLLBACK, SAVEPOINT |

> 💡 Final Takeaway
> SQL is the language used to work with relational databases. DDL defines the structure, DML manages the records, DQL retrieves the data, DCL controls access, and TCL manages transactions. Each category is learned separately with its own commands and practical examples.

# Chapter 4 — Database, Schema, Table, Row and Column

Relational databases organize data in a clear structure. Before creating a database, you need to understand the different levels used to store and arrange data.

*The structure can be viewed as: MySQL Server → Database/Schema → Table → Rows and Columns → Values*

## 4.1 Database

A database is an organized collection of related data. It acts as a main container that holds:

- Tables
- Relationships
- Views
- Indexes
- Other database objects

For example, a college may create a database called CollegeManagement, which can contain information about:

- Students
- Courses
- Trainers
- Attendance
- Marks
- Placements

All this information belongs to the same college application, so it can be stored inside one database.

## 4.2 Schema

A schema represents the logical organization or design of a database. It describes:

- What tables exist
- What columns each table contains
- What type of data each column stores
- How tables are connected
- What rules are applied to the data

*A schema can be understood as the blueprint of a database.*

For example, a college database schema may define a Students table, a Courses table, an Enrollments table, and the relationship between students and courses.

### Schema in MySQL

In MySQL, the terms database and schema are generally used interchangeably. Therefore, when MySQL Workbench displays a section called Schemas, it is showing the databases available on the MySQL server.

## 4.3 Table

A table stores data about one particular type of entity. An entity is something about which data is stored. Examples include: Student, Employee, Product, Customer, Course. A table organizes data using rows and columns.

Consider a Students table:

| StudentID | StudentName | Branch | City |
| --- | --- | --- | --- |
| 101 | Aarav | CSE | Bengaluru |
| 102 | Bhavna | ECE | Pune |
| 103 | Charan | CSE | Hyderabad |

The table stores information about multiple students. A database can contain many tables, and each table should normally represent one main entity or concept.

## 4.4 Column

A column represents one property or attribute of an entity. In the Students table:

- StudentID represents the student's identification number.
- StudentName represents the student's name.
- Branch represents the student's branch.
- City represents the student's city.

Every column has a column name, a data type, and rules or constraints (when required). A column defines what kind of information can be stored in that part of the table. Columns are also sometimes called fields or attributes.

## 4.5 Row

A row represents one complete record in a table. Consider this row:

| StudentID | StudentName | Branch | City |
| --- | --- | --- | --- |
| 101 | Aarav | CSE | Bengaluru |

This row contains all the stored information about one student. In the complete Students table, the first row represents Aarav, the second row represents Bhavna, and the third row represents Charan. Rows are also called records.

## 4.6 Value

A value is the actual data stored at the intersection of a row and a column. In the record below:

| StudentID | StudentName | Branch | City |
| --- | --- | --- | --- |
| 101 | Aarav | CSE | Bengaluru |

- 101 is the value under StudentID.
- Aarav is the value under StudentName.
- CSE is the value under Branch.
- Bengaluru is the value under City.

Each value belongs to one row and one column.

## 4.7 Complete Structure

Suppose a MySQL server contains a college application:

| Level | Example | Purpose |
| --- | --- | --- |
| MySQL Server | Local MySQL Server | Manages databases |
| Database / Schema | CollegeManagement | Contains related database objects |
| Table | Students | Stores information about students |
| Column | StudentName | Defines one property |
| Row | Aarav's complete record | Represents one student |
| Value | Aarav | Stores the actual data |

### Database and Table Are Not the Same

A database is the complete container, while a table stores data about one particular entity. For example, database CollegeManagement may contain the Students, Courses, Trainers, Attendance, and Marks tables. The database contains the tables — a table does not contain the database.

### Row and Column Are Not the Same

| Row | Column |
| --- | --- |
| Represents one complete record | Represents one property |
| Moves horizontally across the table | Moves vertically through the table |
| Example: one student | Example: names of all students |
| Also called a record | Also called a field or attribute |

## 4.8 Mental Model

Think of a database as a collection of organized registers, kept in a cupboard:

| Real-world object | Database concept |
| --- | --- |
| The complete cupboard | The database |
| The arrangement of registers | The schema |
| Each register | A table |
| Each heading in a register | A column |
| Each filled entry | A row |
| Each individual piece of information | A value |

> 💡 Final Takeaway
> A database contains related data and database objects. A schema describes how the database is organized (in MySQL, database and schema usually refer to the same thing). A table stores data about one type of entity. A column represents one property. A row represents one complete record. A value is the actual data stored inside a table.

# Chapter 5 — Installing MySQL Server and MySQL Workbench

To practise SQL on your computer, you need to install two applications:

| Application | Role |
| --- | --- |
| MySQL Server | Stores databases and executes SQL queries |
| MySQL Workbench | Provides a graphical interface for writing queries and working with MySQL Server |

*MySQL Workbench alone is not enough — the server must also be installed and running.*

## 5.1 System Requirements

- A Windows computer
- Administrator access
- A stable internet connection
- At least 2 GB of free storage
## 5.2 Step-by-Step Installation

### Step 1 — Download the MySQL Installer

1. Open the official MySQL Installer download page.
1. You will see two installer options — Web Installer (smaller, downloads components during installation) or Full Installer (larger, contains all required components). Download the Web Installer if you have a stable internet connection.
1. Click Download.
1. If the website asks you to sign in, click "No thanks, just start my download".
### Step 2 — Start the Installer

1. Open the downloaded .msi file and allow it to make changes to your computer.
1. Select Developer Default as the setup type. This normally installs MySQL Server, MySQL Workbench, MySQL Shell, and required connectors/tools.
1. Click Next. (If Developer Default is unavailable, select Custom and manually choose MySQL Server and MySQL Workbench.)
### Step 3 — Install the Required Components

1. The installer may check for additional software required by MySQL — click Execute to install the requirements.
1. Wait until all required components show a completed status, then click Next.
1. Click Execute again to install MySQL Server and MySQL Workbench.
1. After all products are installed successfully, click Next.
### Step 4 — Configure MySQL Server

Use the following settings and keep everything else at its default:

| Setting | Value |
| --- | --- |
| Server Configuration | Standalone MySQL Server |
| Configuration Type | Development Computer |
| Connectivity | TCP/IP |
| Port | 3306 |
| Authentication | Strong Password Encryption |

### Step 5 — Create the Root Password

The root user is the administrator account for MySQL.

1. Enter a password for the root user.
1. Re-enter the same password to confirm it.
1. Write down or safely store the password — you will need it to connect through Workbench (Username: root, Password: the one you just created).

*Do not forget the root password.*

### Step 6 — Configure the Windows Service

MySQL runs as a Windows service in the background.

1. Keep "Configure MySQL Server as a Windows Service" selected.
1. Keep the default service name shown by the installer.
1. Select "Start the MySQL Server at System Startup".
1. Keep "Standard System Account" selected, then click Next.

*Starting MySQL with Windows ensures the server is available whenever you open Workbench.*

### Step 7 — Apply the Configuration

1. Click Execute and wait while the installer applies the configuration.
1. Confirm that every configuration step shows a success status.
1. Click Finish, then continue through the remaining screens to complete the installation.
### Step 8 — Open MySQL Workbench

1. Open the Windows Start menu and search for MySQL Workbench.
1. Under MySQL Connections, select the local connection (it may appear as "Local instance MySQL" or "Local instance 3306").
1. Enter the root password created during installation.
1. Optionally select "Save password in vault" so you don't enter it every time, then click OK.

The SQL Editor will open once the connection is successful.

### Step 9 — Verify the Installation

Open a new SQL tab and execute:

```sql
SELECT VERSION();
```

This displays the installed MySQL Server version. Next, execute:

```sql
SHOW DATABASES;
```

You should see the databases currently available on your server.

### Step 10 — Create a Test Database

```sql
CREATE DATABASE sql_course;
USE sql_course;

CREATE TABLE Students (
  StudentID   INT PRIMARY KEY,
  StudentName VARCHAR(50)
);

INSERT INTO Students
VALUES (101, 'Aarav');

SELECT * FROM Students;
```

Expected output:

| StudentID | StudentName |
| --- | --- |
| 101 | Aarav |

*If this result appears, MySQL Server and MySQL Workbench have been installed and connected successfully.*

## 5.3 How the Connection Works

You write a query in MySQL Workbench → Workbench sends the query to MySQL Server → MySQL Server executes the query → Workbench displays the result. MySQL Workbench is the interface, while MySQL Server performs the actual database operations.

## 5.4 Common Installation Problems

| Problem | Likely Cause / Fix |
| --- | --- |
| Cannot connect to MySQL Server | The MySQL service may not be running. Press Windows + R, enter services.msc, find the MySQL service, right-click it and select Start or Restart. |
| Access denied for user root | The entered root password is incorrect. Enter the same password created during server configuration. |
| Workbench installed but no local connection appears | MySQL Server may not have been installed. Run MySQL Installer again and add MySQL Server. |
| Port 3306 is unavailable | Another application may already be using port 3306. Select another available port, such as 3307, and use it when creating the Workbench connection. |

### Server Connection Settings (Local Installation)

| Setting | Value |
| --- | --- |
| Hostname | localhost |
| Port | 3306 |
| Username | root |
| Password | Root password created during installation |

> 💡 Final Check
> Your installation is complete when: MySQL Server is installed, the MySQL Windows service is running, MySQL Workbench opens successfully, Workbench connects to the local server, and SQL queries execute without connection errors.

# Chapter 6 — SQL Data Types

Every column in a table must be given a data type. A data type tells MySQL what kind of value a column can hold (a number, text, a date, and so on), how much storage it needs, and what operations are valid on it. Choosing the right data type keeps your database fast, accurate, and free of wasted storage.

*Definition: A data type is a rule that defines the kind of data a column can store, the range of values it accepts, and the amount of memory it occupies.*

## 6.1 Working With Numeric Data Types

Numeric types store numbers — either whole numbers (integers) or numbers with decimal points. MySQL offers several integer sizes so you only pay for the storage you actually need.

### Integer Types

| Type | Storage | Approx. Range (Signed) | Typical Use |
| --- | --- | --- | --- |
| TINYINT | 1 byte | -128 to 127 | Small flags, age, small counters |
| SMALLINT | 2 bytes | -32,768 to 32,767 | Year, small quantity fields |
| MEDIUMINT | 3 bytes | -8,388,608 to 8,388,607 | Medium-range counts |
| INT / INTEGER | 4 bytes | -2.1 billion to 2.1 billion | IDs, general whole numbers |
| BIGINT | 8 bytes | -9.2 quintillion to 9.2 quintillion | Very large counters, big IDs |

**UNSIGNED: **Any integer type can be marked UNSIGNED to store only non-negative numbers, which doubles the positive range. Example:

```
Age TINYINT UNSIGNED   -- stores 0 to 255 instead of -128 to 127
```

### Decimal (Fixed-Point) Types

Used when exact precision matters — money, for example, must never be rounded incorrectly.

| Type | Description | Example |
| --- | --- | --- |
| DECIMAL(M, D) | Exact fixed-point number. M = total digits, D = digits after the decimal point. | DECIMAL(8,2) stores up to 999999.99 |
| NUMERIC(M, D) | Identical to DECIMAL in MySQL — just another name for it. | NUMERIC(10,2) |

```
Price DECIMAL(8,2)   -- e.g. 45999.99
```

### Floating-Point Types

Used for scientific or approximate values where tiny rounding differences are acceptable — never use these for money.

| Type | Storage | Precision |
| --- | --- | --- |
| FLOAT | 4 bytes | Approximate, ~7 significant digits |
| DOUBLE | 8 bytes | Approximate, ~15 significant digits (more accurate than FLOAT) |

> 💡 Advantage of Choosing the Right Numeric Type
> Using TINYINT instead of INT for a column that only ever stores 0–150 (like age) saves 3 bytes per row. Across millions of rows that adds up to real disk-space and memory savings, and smaller columns are also faster to index and scan.

## 6.2 Working With CHAR, VARCHAR and TEXT Data Types

These types store text. The key difference between them is how the storage size is decided and how MySQL handles the actual length of the text.

### CHAR(n) — Fixed-Length String

Always reserves exactly n characters, no matter how short the actual text is. MySQL pads shorter values with spaces internally (and removes trailing spaces on retrieval).

```
Gender CHAR(1)     -- always stores exactly 1 character, e.g. 'M' or 'F'
StateCode CHAR(2)  -- e.g. 'KA', 'TN'
```

Best for values that are always the same length — gender codes, fixed country codes, fixed-length IDs.

### VARCHAR(n) — Variable-Length String

Stores only as many characters as are actually entered, up to a maximum of n. It uses 1–2 extra bytes to record the actual length, so it is more storage-efficient for text that varies in length.

```
StudentName VARCHAR(50)  -- stores 'Aarav' using only 5 characters + length bytes
```

Best for names, emails, addresses, city names — anything whose length genuinely varies.

### TEXT — Large Variable-Length Text

Used for long text that can exceed VARCHAR's practical limits — paragraphs, descriptions, comments, articles.

| Type | Maximum Size | Typical Use |
| --- | --- | --- |
| TINYTEXT | 255 bytes | Very short notes |
| TEXT | 65,535 bytes (~64 KB) | Comments, descriptions |
| MEDIUMTEXT | 16 MB | Articles, long descriptions |
| LONGTEXT | 4 GB | Very large documents |

### CHAR vs VARCHAR vs TEXT — Comparison

| Feature | CHAR | VARCHAR | TEXT |
| --- | --- | --- | --- |
| Length | Fixed | Variable (up to a limit) | Variable, much larger |
| Storage used | Always n characters | Actual length + 1-2 bytes | Actual length + overhead |
| Speed | Slightly faster for fixed data | Efficient for typical text | Slower; stored separately from the row for large values |
| Can be indexed fully | Yes | Yes | Only a prefix, by default |
| Example use | CHAR(2) state code | VARCHAR(100) email | TEXT blog post body |

> 💡 Advantage of Choosing Correctly
> Picking VARCHAR over TEXT for short fields like names or emails keeps the row itself compact and lets MySQL index and sort the column efficiently. Reserve TEXT only for genuinely long content — using it everywhere "just in case" makes queries slower and indexing harder.

## 6.3 Working With Date, Time, and Boolean Values

### Date and Time Types

| Type | Format | Range / Notes |
| --- | --- | --- |
| DATE | YYYY-MM-DD | Stores only the date, e.g. 2026-09-10 |
| TIME | HH:MM:SS | Stores only the time of day, e.g. 14:30:00 |
| DATETIME | YYYY-MM-DD HH:MM:SS | Stores date and time together; not affected by time zone |
| TIMESTAMP | YYYY-MM-DD HH:MM:SS | Like DATETIME, but stored in UTC and auto-converted to the connection's time zone; smaller range (1970–2038) |
| YEAR | YYYY | Stores just a 4-digit year, e.g. 2026 |

Example table using date/time columns:

```sql
CREATE TABLE Attendance (
  AttendanceID INT PRIMARY KEY,
  StudentID    INT,
  AttendDate   DATE,
  CheckInTime  TIME,
  CreatedAt    TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**DATETIME vs TIMESTAMP: **use DATETIME for fixed, timezone-independent values (like a date of birth or a scheduled exam date). Use TIMESTAMP for values that should reflect "when something actually happened" (like a row's creation or last-update time), since it can auto-update and adjusts for time zone.

### Boolean Values

MySQL does not have a true, separate BOOLEAN storage type. BOOLEAN (or BOOL) is simply an alias for TINYINT(1) — a value of 0 is treated as FALSE, and any non-zero value (typically 1) is treated as TRUE.

```sql
CREATE TABLE Students (
  StudentID INT PRIMARY KEY,
  IsActive  BOOLEAN DEFAULT TRUE   -- stored internally as TINYINT(1)
);
```

*Good to know for interviews: writing BOOLEAN in MySQL is only for readability — under the hood MySQL stores and treats it exactly like TINYINT(1).*

## 6.4 Choosing Appropriate Data Types for Application Data

Picking the right data type is not just a technical formality — it directly affects storage cost, query speed, and data accuracy. A few practical guidelines:

- **Match the type to the real-world range. **Don't use INT for a column that will only ever hold 0–5 (like a rating) — TINYINT is enough.
- **Use DECIMAL for money, never FLOAT/DOUBLE. **Floating-point types can introduce tiny rounding errors that are unacceptable in financial data.
- **Prefer VARCHAR over CHAR for variable-length text **such as names and addresses; reserve CHAR for genuinely fixed-length codes.
- **Use TEXT only when content can genuinely be long. **For short fields, VARCHAR is faster to index and search.
- **Use DATE/DATETIME/TIMESTAMP instead of storing dates as text. **This allows correct sorting, date arithmetic, and validation that a plain string column cannot give you.
- **Use BOOLEAN (TINYINT(1)) for true/false flags **instead of storing 'Yes'/'No' as text — it's smaller and faster to compare.
- **Avoid over-sized columns "just in case". **A VARCHAR(255) for every text field wastes planning effort — size columns to realistic maximum lengths.
### Worked Example — Choosing Types for a Student Table

| Column | Chosen Type | Reason |
| --- | --- | --- |
| StudentID | INT (PRIMARY KEY) | Whole number, comfortably fits typical ID ranges |
| StudentName | VARCHAR(50) | Text length varies from student to student |
| Gender | CHAR(1) | Always exactly one character ('M'/'F'/'O') |
| DateOfBirth | DATE | Only the date is needed, no time component |
| FeesPaid | DECIMAL(10,2) | Money — must be exact, never approximate |
| IsActive | BOOLEAN | Simple true/false flag |
| Bio | TEXT | Free-form text that can be long and of unknown length |

> 💡 Final Takeaway
> A data type is a contract between you and MySQL about what a column can hold. Choose numeric types by realistic range, use DECIMAL for money, VARCHAR for typical text, TEXT only for long content, proper DATE/TIME types instead of plain strings, and BOOLEAN for flags. Good choices here make your database smaller, faster, and far less error-prone.

# Chapter 7 — Modifying Database Structure

Once a table has been created, its structure is rarely final. Applications grow, and new requirements appear — a new column may be needed, an existing column's type may need to change, or an entire table may need to be renamed or emptied. The ALTER TABLE command is the DDL tool used to modify an existing table's structure without rebuilding it from scratch.

## 7.1 Adding, Modifying and Removing Columns Using ALTER TABLE

Starting table used for all examples in this chapter:

```sql
CREATE TABLE Students (
  StudentID   INT PRIMARY KEY,
  StudentName VARCHAR(50),
  Branch      VARCHAR(20)
);
```

### Adding a Column — ADD COLUMN

Adds a new column to an existing table.

```sql
ALTER TABLE Students
ADD COLUMN Email VARCHAR(100);
```

You can also control where the new column appears using AFTER or FIRST:

```sql
ALTER TABLE Students
ADD COLUMN Age INT AFTER StudentName;
```

You can add more than one column in a single statement:

```sql
ALTER TABLE Students
ADD COLUMN City VARCHAR(30),
ADD COLUMN Pincode VARCHAR(10);
```

### Modifying a Column — MODIFY COLUMN

Changes the data type or definition of an existing column, while keeping its name the same.

```sql
ALTER TABLE Students
MODIFY COLUMN Email VARCHAR(150);
```

MODIFY can also add or remove constraints such as NOT NULL:

```sql
ALTER TABLE Students
MODIFY COLUMN Branch VARCHAR(20) NOT NULL;
```

### Renaming and Changing a Column Together — CHANGE COLUMN

CHANGE lets you rename a column and redefine its type in the same statement (MODIFY cannot rename a column).

```sql
ALTER TABLE Students
CHANGE COLUMN Email StudentEmail VARCHAR(150);
```

### Removing a Column — DROP COLUMN

Permanently removes a column and all the data stored in it.

```sql
ALTER TABLE Students
DROP COLUMN Pincode;
```

*DROP COLUMN cannot be undone — the data in that column is permanently lost once the statement runs.*

### Quick Reference — ALTER TABLE Column Operations

| Goal | Syntax | Can Rename? |
| --- | --- | --- |
| Add a column | ADD COLUMN col_name datatype | — |
| Change a column's type/constraints | MODIFY COLUMN col_name new_datatype | No |
| Rename + redefine a column | CHANGE COLUMN old_name new_name datatype | Yes |
| Remove a column | DROP COLUMN col_name | — |

## 7.2 Renaming Columns and Tables

### Renaming a Table

Two equivalent ways to rename an entire table:

```sql
RENAME TABLE Students TO Learners;
```

or

```sql
ALTER TABLE Students
RENAME TO Learners;
```

### Renaming a Column

MySQL 8.0 and later supports a direct RENAME COLUMN clause:

```sql
ALTER TABLE Students
RENAME COLUMN StudentName TO FullName;
```

On older MySQL versions, use CHANGE COLUMN instead (you must repeat the data type):

```sql
ALTER TABLE Students
CHANGE COLUMN StudentName FullName VARCHAR(50);
```

*Renaming a table or column does not affect the data inside it — only its name changes. However, any queries, views, or application code that reference the old name must be updated separately.*

## 7.3 Understanding TRUNCATE and DROP

TRUNCATE, DROP, and DELETE are sometimes confused because they can all appear to "remove data" — but they operate very differently.

### TRUNCATE TABLE

Removes all rows from a table instantly, but keeps the table's structure (columns, data types, constraints) intact so it can be reused immediately.

```sql
TRUNCATE TABLE Students;
```

- Deletes all rows — cannot be used with a WHERE clause.
- Resets any AUTO_INCREMENT counter back to its starting value.
- Is a DDL operation — much faster than DELETE for clearing an entire table, and generally cannot be rolled back.
- The table itself still exists and can be used right away.
### DROP TABLE

Permanently deletes the entire table — its structure, its data, its indexes, and its constraints — from the database.

```sql
DROP TABLE Students;
```

- The table no longer exists after this command runs.
- Any indexes, constraints, and permissions tied to the table are removed as well.
- Cannot be undone (without a backup).

DROP can also remove an entire database:

```sql
DROP DATABASE sql_course;
```

### DELETE (for comparison)

Unlike TRUNCATE and DROP, DELETE is a DML command that removes rows one at a time and can be filtered with WHERE, making it reversible inside a transaction.

```sql
DELETE FROM Students WHERE Branch = 'ECE';
```

### TRUNCATE vs DROP vs DELETE — Comparison

| Feature | TRUNCATE | DROP | DELETE |
| --- | --- | --- | --- |
| Command type | DDL | DDL | DML |
| What it removes | All rows only | Entire table (structure + data) | Selected rows (or all, if no WHERE) |
| Table structure after | Still exists, empty | No longer exists | Still exists |
| Supports WHERE clause | No | No | Yes |
| Speed | Very fast | Very fast | Slower (row-by-row) |
| AUTO_INCREMENT counter | Reset to start | Removed with the table | Not reset |
| Can be rolled back | Generally no | Generally no | Yes, within a transaction |

> 💡 How to Remember It
> TRUNCATE empties the room but keeps the house standing. DROP demolishes the house completely. DELETE removes chosen items from the room, one at a time, and lets you put them back if you change your mind before saving.

## 7.4 Interview Questions — Chapter 7

**Q1. What is the difference between MODIFY and CHANGE in ALTER TABLE?**

***Ideal answer: ****MODIFY changes a column's data type or constraints but keeps its name the same. CHANGE can rename the column and redefine its type in the same statement — MODIFY alone cannot rename a column.*

**Q2. What is the difference between TRUNCATE and DELETE?**

***Ideal answer: ****TRUNCATE is a DDL command that removes all rows at once, resets AUTO_INCREMENT, and cannot use a WHERE clause. DELETE is a DML command that removes rows one at a time, can be filtered with WHERE, and can be rolled back within a transaction.*

**Q3. What is the difference between TRUNCATE and DROP?**

***Ideal answer: ****TRUNCATE empties a table but keeps its structure so it can be reused immediately. DROP removes the table entirely — its structure, data, indexes, and constraints — and the table no longer exists afterward.*

**Q4. How do you add a new column to an existing table?**

***Ideal answer: ****Using ALTER TABLE with ADD COLUMN, e.g. ALTER TABLE Students ADD COLUMN Email VARCHAR(100);*

# Chapter 8 — Keys and Constraints

Keys and constraints are the rules that keep data in a relational database accurate, unique, and properly connected. Without them, a table would allow duplicate records, missing values, and broken relationships between tables.

## 8.1 Understanding Keys and Constraints

*Definition: A constraint is a rule applied to a column (or a set of columns) that restricts the kind of data that can be stored in it, in order to maintain accuracy and reliability. A key is a column (or combination of columns) used to uniquely identify rows or to connect one table to another.*

In short: constraints protect data quality; keys identify and connect records.

### Types of Keys

| Key | Description | Example |
| --- | --- | --- |
| Candidate Key | Any column (or set of columns) that could qualify to uniquely identify a row | StudentID, Email — both could identify a student |
| Primary Key | The candidate key actually chosen to uniquely identify each row in the table | StudentID |
| Composite Key | A primary key made up of two or more columns together | (OrderID, ProductID) in an OrderItems table |
| Unique Key | A column that must hold unique values, but is not the primary key | Email, PhoneNumber |
| Foreign Key | A column in one table that refers to the primary key of another table, creating a relationship | StudentID in the Marks table, referencing Students |

### Types of Constraints — Overview

| Constraint | Purpose |
| --- | --- |
| PRIMARY KEY | Uniquely identifies each row; combines NOT NULL + UNIQUE |
| NOT NULL | Column cannot store an empty (NULL) value |
| UNIQUE | All values in the column must be different from each other |
| DEFAULT | Sets an automatic value when none is provided |
| CHECK | Restricts values based on a condition |
| AUTO_INCREMENT | Automatically generates the next number for a column |
| FOREIGN KEY | Links a column to the primary key of another table |

## 8.2 Using PRIMARY KEY, NOT NULL and UNIQUE

### PRIMARY KEY

A PRIMARY KEY uniquely identifies every row in a table. MySQL automatically enforces two rules on it: values must be unique, and values cannot be NULL. A table can have only one primary key.

```sql
CREATE TABLE Students (
  StudentID   INT PRIMARY KEY,
  StudentName VARCHAR(50)
);
```

A primary key can also be added after the table is created, or defined on multiple columns (a composite key):

```sql
ALTER TABLE Students
ADD PRIMARY KEY (StudentID);

-- composite primary key
CREATE TABLE OrderItems (
  OrderID   INT,
  ProductID INT,
  Quantity  INT,
  PRIMARY KEY (OrderID, ProductID)
);
```

### NOT NULL

Ensures a column can never be left empty — every row must supply a value for it.

```sql
CREATE TABLE Students (
  StudentID   INT PRIMARY KEY,
  StudentName VARCHAR(50) NOT NULL
);
```

Without NOT NULL, a column silently accepts NULL, which can break calculations, searches, and joins later on.

### UNIQUE

Ensures every value in a column is different from every other value in that column — but, unlike PRIMARY KEY, a UNIQUE column is allowed to store one NULL value (since NULL is not considered equal to anything, including another NULL).

```sql
CREATE TABLE Students (
  StudentID   INT PRIMARY KEY,
  StudentName VARCHAR(50) NOT NULL,
  Email       VARCHAR(100) UNIQUE
);
```

A table can have many UNIQUE columns, but only one PRIMARY KEY.

## 8.3 Using DEFAULT, CHECK and AUTO_INCREMENT

### DEFAULT

Supplies an automatic value for a column when no value is given during an INSERT.

```sql
CREATE TABLE Students (
  StudentID   INT PRIMARY KEY,
  StudentName VARCHAR(50) NOT NULL,
  Branch      VARCHAR(20) DEFAULT 'CSE',
  JoinedOn    DATE DEFAULT (CURRENT_DATE)
);
```

If a Branch is not supplied on insert, MySQL automatically stores 'CSE'.

### CHECK

Restricts the values allowed in a column based on a logical condition. (Supported from MySQL 8.0.16 onward.)

```sql
CREATE TABLE Students (
  StudentID INT PRIMARY KEY,
  Age       INT CHECK (Age >= 17),
  Marks     INT CHECK (Marks BETWEEN 0 AND 100)
);
```

Any INSERT or UPDATE that violates the condition is rejected by MySQL.

### AUTO_INCREMENT

Automatically generates the next whole number for a column — most commonly used with a primary key so you never have to supply an ID manually.

```sql
CREATE TABLE Students (
  StudentID   INT PRIMARY KEY AUTO_INCREMENT,
  StudentName VARCHAR(50) NOT NULL
);

INSERT INTO Students (StudentName) VALUES ('Aarav');
INSERT INTO Students (StudentName) VALUES ('Bhavna');
-- StudentID is generated automatically as 1, 2, 3 ...
```

- Only one AUTO_INCREMENT column is allowed per table.
- It must be indexed — normally as the PRIMARY KEY.
- The counter keeps increasing even if rows are deleted (it does not reuse deleted numbers), unless the table is truncated.
## 8.4 Comparing PRIMARY KEY and UNIQUE Constraints

PRIMARY KEY and UNIQUE are often confused because both prevent duplicate values — but they are not interchangeable.

| Feature | PRIMARY KEY | UNIQUE |
| --- | --- | --- |
| Allows NULL values | No | Yes — one NULL is allowed |
| Number allowed per table | Only one | Multiple |
| Main purpose | Uniquely identifies each row | Prevents duplicate values in a column |
| Automatically indexed | Yes (clustered index in InnoDB) | Yes (unique index) |
| Can be referenced by a FOREIGN KEY | Yes | Yes |
| Typical use | StudentID, OrderID | Email, PhoneNumber, UserName |

*Rule of thumb: use PRIMARY KEY for the one column (or column combination) that identifies each row of the table itself. Use UNIQUE for any other column that must not repeat, such as an email address or a username, where the value is still a real-world identifier but not the table's main key.*

### Putting It All Together — A Complete Example

```sql
CREATE TABLE Students (
  StudentID   INT PRIMARY KEY AUTO_INCREMENT,
  StudentName VARCHAR(50) NOT NULL,
  Email       VARCHAR(100) UNIQUE,
  Branch      VARCHAR(20) DEFAULT 'CSE',
  Age         INT CHECK (Age >= 17),
  JoinedOn    DATE DEFAULT (CURRENT_DATE)
);
```

| Column | Constraint(s) | What It Guarantees |
| --- | --- | --- |
| StudentID | PRIMARY KEY, AUTO_INCREMENT | Unique, non-null, auto-generated ID for every student |
| StudentName | NOT NULL | Every student must have a name on record |
| Email | UNIQUE | No two students can share the same email |
| Branch | DEFAULT 'CSE' | Branch is filled in automatically if not provided |
| Age | CHECK (Age >= 17) | Rejects any age below 17 |
| JoinedOn | DEFAULT (CURRENT_DATE) | Automatically records today's date if not provided |

> 💡 Final Takeaway
> Keys identify records and connect tables — PRIMARY KEY for a table's own identity, FOREIGN KEY for relationships, UNIQUE for other must-not-repeat values. Constraints protect data quality — NOT NULL stops missing values, CHECK stops invalid values, DEFAULT fills in sensible values automatically, and AUTO_INCREMENT removes the need to generate IDs manually. Used together, they make a database trustworthy by design, not just by convention.

## 8.5 Interview Questions — Chapter 8

**Q1. What is the difference between a primary key and a unique key?**

***Ideal answer: ****A primary key uniquely identifies each row, cannot contain NULL, and a table can have only one. A unique key also enforces uniqueness but allows one NULL value, and a table can have several unique keys.*

**Q2. Can a table have more than one primary key?**

***Ideal answer: ****No — a table can have only one primary key, though that primary key can be composite (made of more than one column).*

**Q3. What is the difference between NOT NULL and UNIQUE?**

***Ideal answer: ****NOT NULL only ensures a column cannot be empty; it does not prevent duplicate values. UNIQUE ensures no two rows share the same value in that column, but (unlike NOT NULL) it still allows one NULL.*

**Q4. What does AUTO_INCREMENT do, and where is it usually used?**

***Ideal answer: ****AUTO_INCREMENT automatically generates the next sequential number for a column, most commonly the primary key, so IDs never need to be entered manually. Only one AUTO_INCREMENT column is allowed per table, and it must be indexed.*

**Q5. What is a foreign key?**

***Ideal answer: ****A foreign key is a column in one table that refers to the primary key of another table, creating a relationship between the two tables and preventing values that don't exist in the referenced table.*

# Chapter 9 — DML: Managing Data (INSERT, UPDATE, DELETE)

DDL builds the structure that holds data — DML is what puts data into that structure, changes it, and removes it. This chapter covers the three core DML commands: INSERT, UPDATE, and DELETE, using one running example table so you can see exactly how each command affects real records.

## 9.1 Inserting a Single Record Using INSERT

### What Happens When a Student Registers?

Imagine a student fills out this registration form:

| Field | Entered Value |
| --- | --- |
| Name | Asha Patil |
| Branch | CSE |
| CGPA | 8.45 |
| Email | asha@gmail.com |
| Joining date | 2026-09-07 |

The application collects these values, but they are not stored permanently until a new record is added to the database. SQL uses the INSERT command to add that record.

### What Does INSERT Do?

- INSERT adds a new row to an existing table.
- It changes the data inside the table but does not change the table's structure.
- Before inserting a record, the database and table must already exist.
### Create the Practice Table

Run this setup first:

```sql
CREATE DATABASE IF NOT EXISTS training_db;
USE training_db;

CREATE TABLE students (
  student_id   INT PRIMARY KEY,
  student_name VARCHAR(60) NOT NULL,
  branch       VARCHAR(30) NOT NULL,
  cgpa         DECIMAL(4,2),
  email        VARCHAR(100) UNIQUE,
  joining_date DATE NOT NULL
);
```

Inspect the table:

```sql
DESCRIBE students;
```

The structure tells you:

- Which columns exist
- Their exact order
- Which data types they accept
- Which values are mandatory
- Which values must remain unique
### Basic INSERT Syntax

```sql
INSERT INTO table_name
VALUES (value_1, value_2, value_3);
```

To insert Asha's record:

```sql
INSERT INTO students
VALUES (
  101,
  'Asha Patil',
  'CSE',
  8.45,
  'asha@gmail.com',
  '2026-09-07'
);
```

### How the Values Are Mapped

When no column list is written, MySQL matches values using the table's column order:

| Position | Table Column | Inserted Value |
| --- | --- | --- |
| 1 | student_id | 101 |
| 2 | student_name | 'Asha Patil' |
| 3 | branch | 'CSE' |
| 4 | cgpa | 8.45 |
| 5 | email | 'asha@gmail.com' |
| 6 | joining_date | '2026-09-07' |

The first value goes into the first column, the second value goes into the second column, and so on.

### Verify the Inserted Record

```sql
SELECT * FROM students;
```

Expected result:

| student_id | student_name | branch | cgpa | email | joining_date |
| --- | --- | --- | --- | --- | --- |
| 101 | Asha Patil | CSE | 8.45 | asha@gmail.com | 2026-09-07 |

*SELECT is used here only to verify the inserted record — it is covered in detail in the DQL module.*

### Why Text Values Use Quotes

Character values must be written inside single quotes:

```
'Asha Patil'
'CSE'
'asha@gmail.com'
```

Without quotes, MySQL may interpret the text as a column or database object name.

### Why Numeric Values Do Not Need Quotes

Whole numbers and decimal values are normally written without quotes:

```
101
8.45
```

This clearly represents them as numeric values.

### How Dates Are Written

MySQL dates are normally written in YYYY-MM-DD format and enclosed in single quotes:

```
'2026-09-07'
```

- 2026 is the year.
- 09 is the month.
- 07 is the day.
### Insert Another Student

```sql
INSERT INTO students
VALUES (
  102,
  'Ravi Kumar',
  'ECE',
  7.90,
  'ravi@gmail.com',
  '2026-09-07'
);
```

Verify both records:

```sql
SELECT * FROM students;
```

| student_id | student_name | branch | cgpa | email | joining_date |
| --- | --- | --- | --- | --- | --- |
| 101 | Asha Patil | CSE | 8.45 | asha@gmail.com | 2026-09-07 |
| 102 | Ravi Kumar | ECE | 7.90 | ravi@gmail.com | 2026-09-07 |

Each successful INSERT adds one new row.

### Rules an INSERT Must Follow

**1. The number of values must match. **The table contains six columns, so a full-row insertion requires six values. This is incomplete and will fail:

```sql
INSERT INTO students
VALUES (
  103,
  'Meera Shah',
  'ISE'
);
```

MySQL cannot determine values for the remaining columns using this form. To insert only selected columns, name them explicitly with a column list:

```sql
INSERT INTO students (student_id, student_name, branch)
VALUES (103, 'Meera Shah', 'ISE');
```

*Any column left out this way must allow NULL, or have a DEFAULT value — otherwise the insert is rejected.*

**2. The value order must match the column order. **This statement contains six values, but the order is wrong:

```sql
INSERT INTO students
VALUES (
  'Zoya Khan',
  104,
  'CSE',
  8.10,
  'zoya@gmail.com',
  '2026-09-07'
);
```

'Zoya Khan' is being sent to student_id, and 104 is being sent to student_name. The database rejects the statement because the values do not match the intended column types.

**3. Constraints are checked during every INSERT. **The table does not accept every syntactically valid statement.

Duplicate primary key:

```sql
INSERT INTO students
VALUES (
  101,
  'Meera Shah',
  'ISE',
  8.10,
  'meera@gmail.com',
  '2026-09-07'
);
```

This is rejected because student_id 101 already exists.

Missing mandatory value:

```sql
INSERT INTO students
VALUES (
  103,
  NULL,
  'ISE',
  9.10,
  'meera@gmail.com',
  '2026-09-07'
);
```

This is rejected because student_name is NOT NULL.

Duplicate unique value:

```sql
INSERT INTO students
VALUES (
  103,
  'Meera Shah',
  'ISE',
  9.10,
  'asha@gmail.com',
  '2026-09-07'
);
```

This is rejected because email must remain unique. The table's constraints protect the stored data during every insertion.

### One Statement Inserts One Complete Record

In this pattern, each INSERT statement adds one record:

```sql
INSERT INTO students
VALUES (
  103,
  'Meera Shah',
  'ISE',
  9.10,
  'meera@gmail.com',
  '2026-09-08'
);
```

This approach is useful when:

- A registration form submits one student.
- A user creates one account.
- A customer places one order.
- An administrator adds one employee.
### Inserting Multiple Records in One Statement

MySQL also allows several rows to be added in a single INSERT by listing multiple value sets, separated by commas — useful for bulk data entry such as importing a class list:

```sql
INSERT INTO students (student_id, student_name, branch, cgpa, email, joining_date)
VALUES
  (104, 'Zoya Khan', 'CSE', 8.10, 'zoya@gmail.com', '2026-09-07'),
  (105, 'Kabir Rao', 'ECE', 7.55, 'kabir@gmail.com', '2026-09-07');
```

*A multi-row INSERT is still one statement — if any single row violates a constraint, MySQL rejects the whole statement by default and no rows are inserted.*

### Recommended Step-by-Step Process

1. Select the database — USE training_db;
1. Inspect the table — DESCRIBE students;
1. Match every value — check the column order, data types, and constraints.
1. Execute the INSERT.
1. Verify the result — SELECT * FROM students;

```sql
USE training_db;
DESCRIBE students;

INSERT INTO students
VALUES (
  106,
  'Zoya Khan',
  'CSE',
  8.10,
  'zoyak@gmail.com',
  '2026-09-08'
);

SELECT * FROM students;
```

*Never assume that a data-change statement produced the intended result — always verify it.*

### Common INSERT Errors

| Error | Cause |
| --- | --- |
| Wrong number of values | The number of supplied values does not match the number expected by the table. |
| Wrong value order | A value is sent to the wrong column because the table order was not checked. |
| Missing quotes around text | A character value (such as Asha) is written without single quotes. |
| Incorrect date format | A date is written in a format other than the expected YYYY-MM-DD. |
| Duplicate key or email | The new record violates a primary-key or unique constraint. |
| Missing mandatory data | NULL is supplied for a NOT NULL column. |

### Interview Questions — INSERT

**Q1. What does INSERT do?**

***Ideal answer: ****INSERT adds one or more new records to an existing table.*

**Q2. Does INSERT change the table structure?**

***Ideal answer: ****No. It changes the records stored in the table. Structural changes use DDL commands such as ALTER TABLE.*

**Q3. How are values matched when no column list is provided?**

***Ideal answer: ****They are matched according to the table's column order — the first value fills the first column, and so on.*

**Q4. Why are text and date values enclosed in single quotes?**

***Ideal answer: ****They are literal character and date values. Quotes distinguish them from SQL object names and keywords.*

**Q5. Why can a syntactically correct INSERT still fail?**

***Ideal answer: ****The inserted values may violate a data type, primary key, unique, mandatory-value (NOT NULL), or CHECK constraint rule.*

> 💡 Final Takeaway — INSERT
> INSERT INTO table_name VALUES (...) adds one complete record using the table's column order. Before running it, inspect the table and ensure every value matches the correct column, data type, and constraint.

## 9.2 Updating Records Using UPDATE

Once records exist in a table, their values often need to change — a student's CGPA improves, an email changes, a branch gets corrected. UPDATE modifies the values inside existing rows without changing how many rows the table has or the table's structure.

### Basic UPDATE Syntax

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

- SET specifies which column(s) to change and their new value(s).
- WHERE specifies which row(s) should be changed.
- Any column not mentioned in SET keeps its existing value.
### Example — Correcting a Single Value

Asha's CGPA was entered incorrectly and needs to be corrected:

```sql
UPDATE students
SET cgpa = 8.75
WHERE student_id = 101;
```

Verify the change:

```sql
SELECT * FROM students WHERE student_id = 101;
```

### Updating Multiple Columns at Once

Separate each column-value pair with a comma:

```sql
UPDATE students
SET branch = 'ISE', cgpa = 8.90
WHERE student_id = 103;
```

### Updating Using a Calculation

A new value can be calculated from the column's current value:

```sql
UPDATE students
SET cgpa = cgpa + 0.10
WHERE student_id = 102;
```

This raises Ravi's existing CGPA by 0.10 rather than replacing it with a fixed number.

### Why the WHERE Clause Is Critical

*If WHERE is omitted, MySQL updates every row in the table — not just one.*

This statement changes the branch of every single student, which is almost never what's intended:

```sql
UPDATE students
SET branch = 'CSE';
```

Always confirm the affected rows with a SELECT using the same condition before running the UPDATE:

```sql
SELECT * FROM students WHERE student_id = 103;
```

### Constraints Are Checked During UPDATE Too

An UPDATE can be rejected for the same reasons an INSERT can:

| Situation | What Happens |
| --- | --- |
| Setting a UNIQUE column to a value that already exists elsewhere | Rejected — duplicate value |
| Setting a NOT NULL column to NULL | Rejected — missing mandatory value |
| Setting a value that violates a CHECK constraint | Rejected — invalid value |
| Setting the PRIMARY KEY to a value that already exists | Rejected — duplicate key |

Example — this fails because the email already belongs to another student:

```sql
UPDATE students
SET email = 'ravi@gmail.com'
WHERE student_id = 101;
```

### Common UPDATE Errors

| Error | Cause |
| --- | --- |
| Missing WHERE clause | Updates every row in the table instead of the intended one. |
| Wrong condition in WHERE | Updates the wrong row(s) because the filter doesn't match the intended record. |
| Duplicate unique value | The new value already exists in another row of a UNIQUE column. |
| NULL for a NOT NULL column | The update tries to clear a mandatory column. |
| Data type mismatch | The new value's type doesn't match the column's data type. |

### Interview Questions — UPDATE

**Q1. What does the UPDATE command do?**

***Ideal answer: ****UPDATE modifies the values of existing records in a table. It changes data, not the table's structure or row count.*

**Q2. What happens if you run UPDATE without a WHERE clause?**

***Ideal answer: ****Every row in the table gets updated with the new value(s) — not just one record — which is a common and dangerous mistake.*

**Q3. Can UPDATE change more than one column at a time?**

***Ideal answer: ****Yes. Multiple column–value pairs can be listed in SET, separated by commas, in a single UPDATE statement.*

**Q4. Can an UPDATE statement fail even if it is syntactically correct?**

***Ideal answer: ****Yes — it can violate a UNIQUE, NOT NULL, CHECK, or PRIMARY KEY constraint, just like an INSERT can.*

> 💡 Final Takeaway — UPDATE
> UPDATE table_name SET column = new_value WHERE condition changes existing data without adding or removing rows. Always pair it with a precise WHERE clause — and verify the target rows with SELECT before and after — since a missing or loose WHERE updates far more rows than intended.

## 9.3 Deleting Records Using DELETE

DELETE removes one or more existing rows from a table. Like UPDATE, it changes only the data inside the table — the table's structure, columns, and constraints remain exactly as they were.

### Basic DELETE Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

### Example — Deleting One Student

Meera Shah has withdrawn her admission and needs to be removed:

```sql
DELETE FROM students
WHERE student_id = 103;
```

Verify the deletion:

```sql
SELECT * FROM students;
```

### Deleting Multiple Rows With One Condition

A single WHERE condition can match — and delete — more than one row:

```sql
DELETE FROM students
WHERE branch = 'ECE';
```

This removes every student whose branch is ECE, however many rows that turns out to be.

### Why the WHERE Clause Is Critical

*If WHERE is omitted, DELETE removes every row from the table — while the table itself still exists, exactly like TRUNCATE TABLE, but slower.*

```sql
DELETE FROM students;   -- removes ALL rows
```

Always test the condition with a SELECT first to confirm exactly which rows will be affected:

```sql
SELECT * FROM students WHERE branch = 'ECE';
```

### DELETE and Referential Integrity

If another table has a FOREIGN KEY pointing to a row in this table, MySQL may reject the DELETE to protect that relationship — for example, if a Marks table stores records linked to a student_id, deleting that student first can be blocked unless the related marks rows are removed or updated first.

```sql
-- Example: this may be rejected if Marks rows still reference student_id 101
DELETE FROM students WHERE student_id = 101;
```

This protection exists so that a table like Marks never ends up pointing to a student that no longer exists.

### DELETE vs TRUNCATE — Quick Recap

| Feature | DELETE | TRUNCATE |
| --- | --- | --- |
| Command type | DML | DDL |
| Supports WHERE | Yes | No — removes all rows |
| Can be rolled back | Yes, within a transaction | Generally no |
| Speed on full table | Slower (row-by-row) | Very fast |
| Resets AUTO_INCREMENT | No | Yes |

### Common DELETE Errors

| Error | Cause |
| --- | --- |
| Missing WHERE clause | Deletes every row in the table instead of the intended one. |
| Wrong condition in WHERE | Deletes the wrong row(s) because the filter doesn't isolate the intended record. |
| Foreign key restriction | The row is still referenced by another table and cannot be deleted until that reference is removed. |

### Interview Questions — DELETE

**Q1. What does the DELETE command do?**

***Ideal answer: ****DELETE removes one or more existing rows from a table, based on a WHERE condition, without changing the table's structure.*

**Q2. What happens if DELETE is run without a WHERE clause?**

***Ideal answer: ****Every row in the table is removed, while the table itself continues to exist — similar in effect to TRUNCATE, but DELETE is slower and can be rolled back within a transaction.*

**Q3. What is the difference between DELETE and TRUNCATE?**

***Ideal answer: ****DELETE is a DML command that removes rows one at a time, supports WHERE, and can be rolled back. TRUNCATE is a DDL command that removes all rows at once, cannot use WHERE, resets AUTO_INCREMENT, and generally cannot be rolled back.*

**Q4. Can a DELETE statement fail even without any typing mistakes?**

***Ideal answer: ****Yes — if another table has a foreign key referencing the row being deleted, MySQL can reject the DELETE to preserve referential integrity.*

## 9.4 INSERT vs UPDATE vs DELETE — Summary

| Command | Purpose | Rows Affected | Structure Changed? |
| --- | --- | --- | --- |
| INSERT | Adds new record(s) | Increases row count | No |
| UPDATE | Modifies existing record(s) | Row count unchanged | No |
| DELETE | Removes existing record(s) | Decreases row count | No |

> 💡 Chapter Takeaway
> INSERT, UPDATE, and DELETE are the three DML commands that manage the data living inside a table's structure. INSERT adds records, UPDATE changes them, and DELETE removes them — none of the three touches the table's columns, data types, or constraints. WHERE is the safeguard for UPDATE and DELETE: without it, the command applies to every row in the table. Every constraint defined with DDL (NOT NULL, UNIQUE, PRIMARY KEY, FOREIGN KEY, CHECK) is enforced automatically during all three operations, keeping the stored data reliable at every step.
