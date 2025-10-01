# ALTER TABLE Statement

The ALTER TABLE statement is used to add, delete, or modify columns in an existing table.

The ALTER TABLE statement is also used to add and drop various constraints on an existing table.

## ADD Column

To add a column in a table, use the following syntax:

```
ALTER TABLE table_name
ADD column_name datatype;
```

## DROP Column

To delete a column in a table, use the following syntax:

```
ALTER TABLE table_name
DROP COLUMN column_name;
```

## RENAME Column

To rename a column in a table, use the following syntax:

```
ALTER TABLE table_name
RENAME COLUMN old_name to new_name;
```

## ALTER/MODIFY DATATYPE

To change the data type of a column in a table, use the following syntax:

```
ALTER TABLE table_name
MODIFY column_name datatype;
```
