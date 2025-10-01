# Foreign Key

The **FOREIGN KEY** constraint is used to prevent actions that would destroy links between tables.
A **FOREIGN KEY** is a field (or collection of fields) in one table, that refers to the [PRIMARY KEY](PrimaryKey.md) in another table.
The table with the foreign key is called the child table, and the table with the primary key is called the referenced or parent table.

## FOREIGN KEY on CREATE TABLE

The following SQL creates a FOREIGN KEY on the "PersonID" column when the "Orders" table is created:

```
CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int REFERENCES Persons(PersonID),
    PRIMARY KEY (OrderID)
);
```

## FOREIGN KEY on ALTER TABLE

To create a FOREIGN KEY constraint on the "PersonID" column when the "Orders" table is already created, use the following SQL:

```
ALTER TABLE Orders
ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
```
