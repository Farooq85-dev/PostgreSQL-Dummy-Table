# PostgreSQL-Dummy-Table
This repository is practical implementation of what i learned in CRUD operation. Happy Coding!


## PostgreSQL CRUD Operations: `USERDATA`Table

This document outlines how to create a basic USERDATA table in PostgreSQL, perform data insertions, updates, and deletions, and explains how default constraints work.

### Table Creation

We begin by creating a table named `USERDATA` with the following fields:

1) ID: An auto-incrementing unique identifier for each user (Primary Key).
2) USERNAME: A unique, non-null string to store the user's name. 
3) CREATED_AT: The date when the record was created (defaulted to the current date).
4) UPDATED_AT: The date when the record was last updated (defaulted to the current date).

### SQL Query to Create the Table
 
 ```
 CREATE TABLE USERDATA (
    ID SERIAL PRIMARY KEY,             -- Auto-incrementing primary key
    USERNAME VARCHAR(100) UNIQUE NOT NULL, -- Username, must be unique and not null
    CREATED_AT DATE DEFAULT CURRENT_DATE,  -- Default value set to the current date
    UPDATED_AT DATE DEFAULT CURRENT_DATE   -- Default value set to the current date
);
 ```
 ### Explanation of Constraints


- SERIAL: Automatically generates a unique integer for the ID field, which increments with each new record.
- PRIMARY KEY: Ensures that each ID is unique and serves as the identifier for each row.
- UNIQUE: Ensures that no two users have the same USERNAME.
- NOT NULL: Prevents the USERNAME field from being empty.
- DEFAULT CURRENT_DATE: Automatically sets the date fields (CREATED_AT and UPDATED_AT) to the current date when a new record is inserted.

### Inserting Data into the Table

To insert new users into the USERDATA table, we can use the INSERT INTO command. For example, here we insert three users.

### SQL Query to Insert Records

```
INSERT INTO USERDATA (USERNAME) 
VALUES 
    ('MUHAMMAD FAROOQ'), 
    ('MUHAMMAD ASAD'), 
    ('MUHAMMAD FAIZAN');
```

After inserting the records, we can retrieve all the data from the USERDATA table with the SELECT statement.

![table-img](./images/Screenshot%20from%202024-10-07%2021-11-05.png)

As you can see, the ID field auto-increments for each new user, and both the CREATED_AT and UPDATED_AT fields are automatically set to the current date (2024-10-07).

### Updating a Record

To update a user’s data, use the UPDATE statement. For example, to change the USERNAME of the user with ID = 1:

### SQL Query to Update Record

```
UPDATE USERDATA SET USERNAME = 'MUHAMMAD FAHAD' WHERE ID = 1;
```

### Result
This will update the username for the user with ID = 1 to 'MUHAMMAD FAHAD'.

### Deleting a Record

To delete a record, use the DELETE statement. For example, to delete the user with ID = 3:

#### SQL Query to Delete Record

```
DELETE FROM USERDATA WHERE ID = 3
```

### Result

This will delete the row with ID = 3 from the USERDATA table.

```
-- Create the table
CREATE TABLE USERDATA (
    ID SERIAL PRIMARY KEY,
    USERNAME VARCHAR(100) UNIQUE NOT NULL,
    CREATED_AT DATE DEFAULT CURRENT_DATE,
    UPDATED_AT DATE DEFAULT CURRENT_DATE
);

-- Insert records into the table
INSERT INTO USERDATA (USERNAME) 
VALUES 
    ('MUHAMMAD FAROOQ'), 
    ('MUHAMMAD ASAD'), 
    ('MUHAMMAD FAIZAN');

-- Select all records from the table
SELECT * FROM USERDATA;

-- Update a record
UPDATE USERDATA SET USERNAME = 'MUHAMMAD FAHAD' WHERE ID = 1;

-- Delete a record
DELETE FROM USERDATA WHERE ID = 3;

-- Select all records again to verify changes
SELECT * FROM USERDATA;
```

### Conclusion

In this guide, we walked through how to:

- Create a PostgreSQL table with default constraints.
- Insert, update, and delete records.
Understand the meaning of constraints like SERIAL, PRIMARY KEY, UNIQUE, and DEFAULT.
This table structure provides a solid foundation for managing user data in a PostgreSQL database.