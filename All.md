# ALL Operator

The ALL operator:

- returns a boolean value as a result
- returns TRUE if ALL of the subquery values meet the condition
- is used with [SELECT](/Select.md), [WHERE](/Where.md) and [HAVING](/Having.md) statements
ALL means that the condition will be true only if the operation is true for all values in the range.

## Syntax

```
SELECT column_name(s)
FROM table_name
WHERE column_name operator ALL
  (SELECT column_name
  FROM table_name
  WHERE condition);
```
