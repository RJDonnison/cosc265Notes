# Update

The UPDATE statement is used to modify the existing records in a table.

## Syntax

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

**Note:** Be careful when updating records in a table! Notice the [WHERE](Where.md) clause in the UPDATE statement. The [WHERE](Where.md) clause specifies which record(s) that should be updated. If you omit the [WHERE](Where.md) clause, all records in the table will be updated!
