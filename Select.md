# Select

The SELECT statement is used to select data from a database. To get more sepcific data use a combination of: 

- [DISTINCT](Distinct.md) - Return only distinct (different) values 
- [WHERE](Where) - Used to filter records
- [ORDER BY](Sort.md) - Sort the result-set
- [HAVING](Having.md) - Allows use of [aggregate functions](Functions.md) for filtering

## Syntax

```
SELECT column1, column2, ...
FROM table_name;
```

## Select all columns

If you want to return all columns, without specifying every column name, you can use the `SELECT *` syntax.
