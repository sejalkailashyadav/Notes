
# DBMS Interview Questions 
Database Management Systems (DBMS) play a pivotal role in software applications that rely on structured storage of data. Understanding core concepts of DBMS is essential for software developers, database administrators, and data architects. 
## Questions & Answers
### 1. **What is DBMS?**
   - **Answer**: A Database Management System (DBMS) is software that controls the storage, retrieval, and updating of data in a database.
   - **Example**: Oracle, MySQL, and PostgreSQL are popular RDBMS systems.

### 2. **Distinguish between a database and a DBMS.**
   - **Answer**: A database is a structured collection of data, whereas a DBMS is the software that manages and interacts with the database.
   - **Example**: Consider a library. The collection of books is similar to a database, while the system used to manage the check-in/check-out and arrangement of books is like a DBMS.

### 3. **What is normalization? Why is it important?**
   - **Answer**: Normalization is the process of organizing data in a database to reduce redundancy and prevent data anomalies. It ensures data integrity and optimizes storage.
   - **Example**: Without normalization, a database that stores an address for each transaction could have multiple different addresses for a single customer, leading to confusion and redundancy.

### 4. **Describe the different normal forms in normalization.**
   - **Answer**: There are several normal forms, including 1NF, 2NF, 3NF, BCNF, 4NF, etc. Each form has a set of specific rules or conditions that the database schema should satisfy.
   - **Example**: 
     - **1NF**: Each table has atomic (indivisible) columns.
     - **2NF**: No non-prime attribute is dependent on the proper subset of any candidate key.
     - **3NF**: Every non-prime attribute is functionally dependent on the primary key.

### 5. **What are the ACID properties in a database?**
   - **Answer**: ACID stands for Atomicity, Consistency, Isolation, and Durability. These properties ensure reliable processing of transactions within a database.
   - **Example**: In a banking system, if you are transferring money from one account to another, the operation needs to either fully complete (money is deducted from one account and added to another) or fully fail. Partial completion could lead to data inconsistencies.

### 6. **What is SQL?**
   - **Answer**: SQL (Structured Query Language) is a domain-specific language used for managing and querying data in a relational database.
   - **Example**: 
     ```sql
     SELECT first_name, last_name FROM users WHERE age > 21;
     ```

### 7. **Explain the difference between DDL and DML.**
   - **Answer**: DDL (Data Definition Language) deals with database schema and structure modifications (e.g., `CREATE`, `ALTER`, `DROP`). DML (Data Manipulation Language) deals with data manipulation and includes commands like `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.
   - **Example**:
     - DDL: 
       ```sql
       CREATE TABLE employees (ID int, Name varchar(255));
       ```
     - DML:
       ```sql
       INSERT INTO employees (ID, Name) VALUES (1, 'John Doe');
       ```

### 8. **What is a primary key?**
   - **Answer**: A primary key is a unique identifier for a record in a table. It ensures each record can be uniquely distinguished.
   - **Example**: In a `users` table, `user_id` could be a primary key, ensuring each user has a unique identifier.

### 9. **Distinguish between primary key and foreign key.**
   - **Answer**: A primary key uniquely identifies a record within a table, while a foreign key in one table is the primary key of another table, establishing a link between them.
   - **Example**: In a relational database with `authors` and `books` tables, the `author_id` could be the primary key in the `authors` table and a foreign key in the `books` table.

### 10. **What is a deadlock? How can it be avoided?**
   - **Answer**: A deadlock is a situation in which two or more transactions are unable to proceed because each is waiting for the other to release a resource. Deadlocks can be prevented through techniques like timeout, deadlock detection, or ordering the resources.
   - **Example**: Transaction A holds Resource 1 and waits for Resource 2, which is held by Transaction B. Transaction B waits for Resource 1, resulting in a cyclic wait condition or deadlock.

### 11. **What is indexing and why is it used?**
   - **Answer**: Indexing is a technique used to speed up retrieval operations on a database. It works similarly to an index in a book, allowing the database system to find the required data without scanning every row in a database table.
   - **Example**: A `user_email` index on the `users` table ensures faster lookups when searching by email.

### 12. **What are views in a database?**
   - **Answer**: A view is a virtual table based on the result-set of an SQL statement. It contains rows and columns, similar to a real table, but does not store data physically.
   - **Example**: A view that lists all users who have registered in the past month can be created using an SQL statement filtering on the registration date.

### 13. **Describe the difference between inner join, left join, and right join in SQL.**
   - **Answer**: An inner join returns rows when there is a match in both tables. A left join returns all rows from the left table and matching rows from the right table. A right join returns all rows from the right table and matching rows from the left table.
   - **Example**:
     ```sql
     SELECT orders.order_id, customers.customer_name
     FROM orders
     INNER JOIN customers
     ON orders.customer_id = customers.customer_id;
     ```

---
# DDL || DML || DQL || TCL || DCL
| ID | Name  | Role      | Salary |
|----|-------|-----------|--------|
| 1  | John  | Manager   | 60000  |
| 2  | Jane  | Engineer  | 50000  |
| 3  | Jake  | Engineer  | 50000  |

Now, let's delve into the different types of SQL commands:

1. **DDL (Data Definition Language)**:
    - `CREATE`: Creates a new table.
        ```sql
        CREATE TABLE Employees (
            ID INT PRIMARY KEY,
            Name VARCHAR(50),
            Role VARCHAR(50),
            Salary INT
        );
        ```
    - `ALTER`: Modifies the table structure.
        ```sql
        ALTER TABLE Employees ADD COLUMN Department VARCHAR(50);
        ```
    - `DROP`: Deletes the table.
        ```sql
        DROP TABLE Employees;
        ```

2. **DML (Data Manipulation Language)**:
    - `SELECT`: Retrieves data from a table.
        ```sql
        SELECT * FROM Employees WHERE Role = 'Engineer';
        ```
    - `INSERT`: Adds new data into the table.
        ```sql
        INSERT INTO Employees (ID, Name, Role, Salary) VALUES (4, 'Mike', 'Intern', 30000);
        ```
    - `UPDATE`: Modifies existing data in the table.
        ```sql
        UPDATE Employees SET Salary = 55000 WHERE Name = 'Jane';
        ```
    - `DELETE`: Removes data from the table.
        ```sql
        DELETE FROM Employees WHERE Name = 'Jake';
        ```

3. **DCL (Data Control Language)**:
    - `GRANT`: Provides specific privileges to a user.
        ```sql
        GRANT SELECT, INSERT ON Employees TO some_user;
        ```
    - `REVOKE`: Removes specific privileges from a user.
        ```sql
        REVOKE INSERT ON Employees FROM some_user;
        ```

4. **TCL (Transaction Control Language)**:
    - `BEGIN TRANSACTION`: Begins a new transaction.
        ```sql
        BEGIN TRANSACTION;
        ```
    - `COMMIT`: Commits the current transaction.
        ```sql
        COMMIT;
        ```
    - `ROLLBACK`: Rolls back the current transaction to the beginning or to a savepoint.
        ```sql
        ROLLBACK;
        ```
    - `SAVEPOINT`: Creates a savepoint within a transaction to which you can later roll back.
        ```sql
        SAVEPOINT Savepoint1;
        ```
        example :
1. **COMMIT**:
    - What it does: It permanently saves any transactional updates into the database. After committing, you cannot undo the changes.
    
    - Example:
        ```sql
        BEGIN TRANSACTION; -- or just BEGIN;
        UPDATE Employees SET Salary = Salary + 5000 WHERE Role = 'Engineer';
        COMMIT;
        ```

2. **ROLLBACK**:
    - What it does: It undoes any changes made during the current transaction and reverts to the previous state before the transaction began.
    
    - Example:
        ```sql
        BEGIN TRANSACTION;
        DELETE FROM Employees WHERE Role = 'Intern';
        -- Oops, I changed my mind!
        ROLLBACK;
        ```

3. **SAVEPOINT**:
    - What it does: It creates a point within a transaction to which you can later roll back, instead of rolling back the entire transaction. This allows you to have nested levels of transactions.
    
    - Example:
        ```sql
        BEGIN TRANSACTION;
        UPDATE Employees SET Salary = 55000 WHERE Name = 'Jane';

        SAVEPOINT SavepointA;

        INSERT INTO Employees (Name, Role, Salary) VALUES ('Mike', 'Intern', 30000);

        -- Oh no, I shouldn't have added Mike as an Intern.
        ROLLBACK TO SavepointA; -- This will only undo the INSERT operation, not the UPDATE operation.

        COMMIT; -- This will save the changes from the UPDATE operation but not the INSERT.
        ```

5. **DQL (Data Query Language)**:
    - Primarily consists of the `SELECT` command to query and retrieve data. It's often considered a part of DML, but some sources separate it.
        ```sql
        SELECT Name, Role FROM Employees WHERE Salary > 50000;
        ```

The above examples provide an overview of the various SQL command types and how they operate on data and database structures.

# ACID Properties

The ACID properties are a set of properties that ensure reliable processing of transactions in a database management system (DBMS). The acronym "ACID" stands for Atomicity, Consistency, Isolation, and Durability.

1. **Atomicity**:
    - **Definition**: Atomicity ensures that a transaction is treated as a single unit, which means either all of its operations are executed or none of them are.
    - **Example**: Let's say you're making an online transfer from one bank account to another. The operation consists of deducting the amount from one account and adding it to another. If, for some reason, the amount is deducted from one account but not added to the receiving account (e.g., due to a system crash or failure), the whole transaction will be rolled back, ensuring that the amount is not lost.

2. **Consistency**:
    - **Definition**: Consistency ensures that the database remains in a consistent state before and after the transaction. This means that any transaction will bring the database from one valid state to another.
    - **Example**: Suppose there's a rule that the minimum balance in a bank account must be $100. If a transaction attempts to reduce the balance below $100, the transaction will be aborted to ensure the consistency rule is not violated.

3. **Isolation**:
    - **Definition**: Isolation ensures that concurrent execution of transactions results in a system state that would be obtained if transactions were executed serially (one after the other). This means that the operations of one transaction are isolated from the operations of other transactions.
    - **Example**: Imagine two people trying to book the last seat on a flight at the same time. Even if their booking operations happen concurrently, the isolation property will ensure that only one person successfully books the seat while the other receives an error or a notification that the seat has already been booked.

4. **Durability**:
    - **Definition**: Durability ensures that once a transaction has been committed, it remains committed even in the case of a system failure. This is typically achieved by storing the transaction logs or by ensuring data is flushed to permanent storage.
    - **Example**: After confirming the receipt of a payment in an online store, the transaction data is stored in permanent storage. If there's a system crash shortly after the payment confirmation, the data related to that transaction won't be lost, thanks to durability. When the system restarts, the transaction will still be in a committed state.

# Normalization

Normalization is a process in relational database design that organizes tables to minimize data redundancy and dependency by dividing larger tables into smaller ones and defining relationships between them. The main goals of normalization are:

1. Eliminating redundant data.
2. Ensuring data is stored logically.
3. Reducing the potential for anomalies during data operations (insertion, update, deletion).

**Real-time Example of Normalization**:

Imagine a university database with a table called `Students`:

| StudentID | FullName | Subjects                           | ContactNumber |
|-----------|----------|------------------------------------|---------------|
| 1         | John Doe | Math, Science, History             | 1234567890    |
| 2         | Jane Doe | Science, History                   | 0987654321    |
| 3         | Sam Smith| Math, History, Physical Education  | 1122334455    |

Issues with the table:

1. The Subjects column has multiple values, making it challenging to query specific subjects or modify one subject for a student.
2. If we need to change the name of a subject, we have to do it in multiple places.
3. Deleting a student row might inadvertently delete information about which subjects are offered.

To normalize, we'd break this table down:

1. **Student Table**:

| StudentID | FullName   | ContactNumber |
|-----------|------------|---------------|
| 1         | John Doe   | 1234567890    |
| 2         | Jane Doe   | 0987654321    |
| 3         | Sam Smith  | 1122334455    |

2. **Subjects Table**:

| SubjectID | SubjectName |
|-----------|-------------|
| 1         | Math        |
| 2         | Science     |
| 3         | History     |
| 4         | Physical Education |

3. **StudentSubjects Table**:

| StudentID | SubjectID |
|-----------|-----------|
| 1         | 1         |
| 1         | 2         |
| 1         | 3         |
| 2         | 2         |
| 2         | 3         |
| 3         | 1         |
| 3         | 3         |
| 3         | 4         |

This normalized design eliminates redundancy and reduces the potential for anomalies.

**Types of Normal Forms**:

1. **First Normal Form (1NF)**: Each table has a primary key, and each column contains atomic, indivisible values.
2. **Second Normal Form (2NF)**: All non-key attributes are fully functionally dependent on the primary key. This basically means no partial dependencies of columns on the primary key.
3. **Third Normal Form (3NF)**: All the attributes in a table are functionally dependent only on the primary key.
4. **Boyce-Codd Normal Form (BCNF)**: A more stringent version of the 3NF. For any non-trivial functional dependency X -> Y, X should be a super key.
5. **Fourth Normal Form (4NF)**: Concerned with multi-valued facts. There shouldn't be any dependencies amongst unrelated facts.
6. **Fifth Normal Form (5NF)**: Concerned with join dependencies.
7. **Sixth Normal Form (6NF)**: Concerned with temporal databases and how data is valid over certain periods of time.


# Keys
### 1. **Primary Key**:

- **Definition**: A column or set of columns that uniquely identifies a record within a table.
  
- **Use**: Ensures that each row in the table is unique.

- **Example**:
  ```
  CREATE TABLE Students (
      StudentID INT PRIMARY KEY,
      FirstName VARCHAR(255),
      LastName VARCHAR(255)
  );
  ```
  Here, `StudentID` is a primary key, meaning each student must have a unique ID.

### 2. **Foreign Key**:

- **Definition**: A column or set of columns in one table that refers to the primary key in another table.
  
- **Use**: Ensures referential integrity in the relationship between two tables.

- **Example**:
  ```
  CREATE TABLE Enrollments (
      EnrollmentID INT PRIMARY KEY,
      StudentID INT FOREIGN KEY REFERENCES Students(StudentID),
      CourseName VARCHAR(255)
  );
  ```
  Here, `StudentID` in the `Enrollments` table is a foreign key that references `StudentID` in the `Students` table.

### 3. **Unique Key**:

- **Definition**: A column or set of columns where all values must be unique, similar to the primary key, but a table can have multiple unique keys.
  
- **Use**: Ensures uniqueness of values in columns where it's applied.

- **Example**:
  ```
  CREATE TABLE Users (
      UserID INT PRIMARY KEY,
      Email VARCHAR(255) UNIQUE,
      Password VARCHAR(255)
  );
  ```
  Here, the `Email` column is a unique key, ensuring no two users have the same email address.

### 4. **Composite Key**:

- **Definition**: A type of key that consists of two or more columns to ensure uniqueness within the database.
  
- **Use**: When no single column is sufficient to uniquely identify records.

- **Example**:
  ```
  CREATE TABLE Enrollments (
      StudentID INT,
      CourseID INT,
      EnrollmentDate DATE,
      PRIMARY KEY (StudentID, CourseID)
  );
  ```
  Here, the combination of `StudentID` and `CourseID` acts as a composite key.

### 5. **Candidate Key**:

- **Definition**: A column or set of columns that can be chosen as a primary key. There can be multiple candidate keys, but only one can be the primary key.
  
- **Use**: To identify potential primary keys.

- **Example**: In a table with columns `Email`, `MobileNumber`, and `UserID`, all three columns can be candidate keys if they can uniquely identify a record.

### 6. **Secondary (or Alternate) Key**:

- **Definition**: Any candidate key which is not chosen as the primary key.
  
- **Use**: Useful for retrieval and access purposes.

- **Example**: If in a table `UserID` is the primary key, then `Email` and `MobileNumber` (both unique) would be secondary or alternate keys.

### 7. **Super Key**:

- **Definition**: A set of one or more columns that can be used to identify records uniquely. A super key may contain additional columns that are not strictly required for unique identification.
  
- **Use**: To understand potential combinations for unique identification.

- **Example**: In a table with columns `UserID` and `Email`, `{UserID}`, `{Email}`, and `{UserID, Email}` are all super keys, but only the first two are candidate keys.

# `DROP` vs  `DELETE` vs `TRUNCATE`

### 1. `DELETE`:

- **Definition**: `DELETE` is used to remove rows from a table based on a condition. If no condition is specified, all rows will be deleted.
  
- **Characteristics**:
  - It's a logged operation, meaning every row deletion is recorded in the logs. This can make the operation slower, especially for large data.
  - It doesn't free the space associated with the table but makes it available for future inserts.
  - You can use a `WHERE` clause to specify criteria for deletion.
  - It triggers DELETE triggers in the database.

- **Example**:
  ```sql
  DELETE FROM students WHERE student_id = 5;
  ```

### 2. `TRUNCATE`:

- **Definition**: `TRUNCATE` quickly removes all rows from a table, resetting the space occupied by the table to its minimum.
  
- **Characteristics**:
  - Typically, it's a minimally logged operation, making it faster than DELETE.
  - It frees the space back to the system, effectively resetting the table to be like a new one.
  - You cannot use a `WHERE` clause. It will remove all rows.
  - Doesn't generally activate triggers as it doesn't operate on individual rows.

- **Example**:
  ```sql
  TRUNCATE TABLE students;
  ```

### 3. `DROP`:

- **Definition**: The `DROP` command removes an entire table or database from the database system.
  
- **Characteristics**:
  - All space associated with the object (table, database, etc.) is released back to the system.
  - The structure/schema of the object is also deleted, meaning you lose both the data and the design.
  - It's not a logged operation in terms of individual rows (since the whole structure is removed).
  - There's no going back after a DROP without a backup.

- **Example**:
  ```sql
  DROP TABLE students;
  ```

### Main Differences:

- **Scope**: `DELETE` operates on rows, `TRUNCATE` operates on the entire table (but retains the structure), and `DROP` removes the entire table or database structure and data.
- **Speed**: `TRUNCATE` is usually faster than `DELETE` because it's less logged. `DROP` is fast because it removes the entire object.
- **Space**: After `TRUNCATE` and `DROP`, space is freed to the system, while `DELETE` just makes it available for future rows in the same table.
- **Flexibility**: Only `DELETE` allows for conditional removal based on the data in the rows.

# Join 

### 1. **INNER JOIN (or JOIN)**:

- **Definition**: Returns records that have matching values in both tables.
  
- **Example**:
  ```sql
  SELECT employees.name, orders.order_id
  FROM employees
  INNER JOIN orders ON employees.employee_id = orders.employee_id;
  ```
  This returns all employees and their orders, but only for employees who have made at least one order.

### 2. **LEFT JOIN (or LEFT OUTER JOIN)**:

- **Definition**: Returns all records from the left table, and the matched records from the right table. If there's no match, the result is NULL on the right side.
  
- **Example**:
  ```sql
  SELECT students.name, courses.course_name
  FROM students
  LEFT JOIN enrollments ON students.student_id = enrollments.student_id
  LEFT JOIN courses ON enrollments.course_id = courses.course_id;
  ```
  This fetches all students and the courses they are enrolled in, but it will also include students not enrolled in any course (with NULL for course names).

### 3. **RIGHT JOIN (or RIGHT OUTER JOIN)**:

- **Definition**: Returns all records from the right table, and the matched records from the left table. If there's no match, the result is NULL on the left side.
  
- **Example**:
  ```sql
  SELECT students.name, books.book_title
  FROM students
  RIGHT JOIN book_ownership ON students.student_id = book_ownership.student_id
  RIGHT JOIN books ON book_ownership.book_id = books.book_id;
  ```
  This fetches all books and their respective owners. If a book has no owner, it'll still be listed (with NULL for the student's name).

### 4. **FULL JOIN (or FULL OUTER JOIN)**:

- **Definition**: Returns all records when there's a match in one of the left or right tables. Combines the effects of both LEFT and RIGHT joins.
  
- **Example**:
  ```sql
  SELECT customers.name, orders.order_id
  FROM customers
  FULL JOIN orders ON customers.customer_id = orders.customer_id;
  ```
  This fetches all customers and their orders, but it also includes customers with no orders and orders that have no linked customer.

### 5. **CROSS JOIN**:

- **Definition**: Returns the Cartesian product of the two tables. It pairs every row from the first table with every row from the second table.
  
- **Example**:
  ```sql
  SELECT colors.color_name, sizes.size_label
  FROM colors
  CROSS JOIN sizes;
  ```
  If you have a `colors` table with colors (Red, Blue) and a `sizes` table with sizes (Small, Medium), this would return all combinations: Red-Small, Red-Medium, Blue-Small, Blue-Medium.

### 6. **SELF JOIN**:

- **Definition**: A join of a table with itself. Useful when the data related to each other is in the same table.
  
- **Example**:
  ```sql
  SELECT A.employee_name, B.employee_name as 'Manager'
  FROM employees A, employees B
  WHERE A.manager_id = B.employee_id;
  ```
  This fetches every employee alongside their respective managers from an `employees` table, where managers are also employees in the same table.


# Understanding Redundancy:

1. **Definition**: Redundancy in DBMS is when data is repeated in the database unnecessarily, leading to a waste of storage and potential inconsistencies.

2. **Problems caused by Redundancy**:
   - **Update Anomaly**: Difficulty in updating data. For instance, if the same data is stored in multiple locations, updating it in one place but not the others can lead to inconsistencies.
   - **Insert Anomaly**: There might be scenarios where certain data cannot be inserted without the presence of other data.
   - **Delete Anomaly**: Removing a record might unintentionally remove valuable data if the data is stored redundantly.

### Example of Redundancy:

Consider a simple database for a school system. Let's take a table `Classes`:

| StudentName | Subject       | TeacherName |
|-------------|---------------|-------------|
| Alice       | Mathematics   | Mr. Smith   |
| Bob         | Mathematics   | Mr. Smith   |
| Charlie     | English       | Mrs. Doe    |
| Alice       | English       | Mrs. Doe    |

From the table, you can observe redundancy:

1. The teacher's name for each subject is repeated for every student taking that subject. If there's a change in the teacher for a subject, you'd have to update multiple rows.
  
2. If you wanted to delete a student's record, you would also be deleting the teacher associated with them, which isn't ideal.

3. If you wanted to add a new subject, you'd need a student to associate with it right away, which might not always be the case.

### Solutions:

1. **Normalization**: This is the process of organizing data to minimize redundancy. In the above example, normalization might involve creating separate tables for `Students`, `Subjects`, and `Teachers`, and then using foreign keys to establish relationships.

2. **Regular Audits**: Periodically checking the database for redundancy can help in keeping it clean and efficient.





