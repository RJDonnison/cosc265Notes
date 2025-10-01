# Primary Key

The **PRIMARY KEY** constraint is used to uniquely identify each record in a table.
Primary keys must contain unique values, and cannot contain NULL values. 
Each table can have only ONE primary key. The primary key can be a single column or a combination of columns.

## PRIMARY KEY on CREATE TABLE

The following SQL creates a **PRIMARY KEY** on the "ID" column when the "Persons" table is created:

```
CREATE TABLE Persons (
    ID int NOT NULL PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```

To define a **PRIMARY KEY** constraint on multiple columns, use the following SQL syntax:

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT PK_Person PRIMARY KEY (ID,LastName)
);
```

## PRIMARY KEY on ALTER TABLE

To create a **PRIMARY KEY** constraint on the "ID" column when the table is already created, use the following SQL:

```
ALTER TABLE Persons
ADD CONSTRAINT PK_Person PRIMARY KEY (ID,LastName);
```
```
