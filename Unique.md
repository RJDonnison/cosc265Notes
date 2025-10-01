# UNIQUE Constraint
The UNIQUE constraint ensures that all values in a column are different. Both the UNIQUE and [PRIMARY KEY](PrimaryKey.md) constraints provide a guarantee for uniqueness for a column or set of columns. A [PRIMARY KEY](PrimaryKey.md) constraint automatically has a UNIQUE constraint. However, you can have many UNIQUE constraints per table, but only one [PRIMARY KEY](PrimaryKey.md) constraint per table.

## UNIQUE Constraint on CREATE TABLE

```
CREATE TABLE Persons (
    ID int NOT NULL UNIQUE,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```

## UNIQUE Constraint on ALTER TABLE

```
ALTER TABLE Persons
ADD UNIQUE (ID);
```
