# Where

The WHERE clause is used to filter records. It is used to extract only those records that fulfill a specified condition. To check if a row exists in a sub query use [EXISTS](Exists.md)

## Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

Or with multiple conditions:

```
SELECT column1, column2, ...
FROM table_name
WHERE condition (AND || OR) condition;
```


