# Date

DATE is formated YYYY-MM-DD.

## Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE date_column = 'YYYY-MM-DD';
```

## Current Date

Use `sysdate` to get the current database date. 
The `GETDATE()` function returns the current database system date and time, in a 'YYYY-MM-DD hh:mm:ss.mmm' format.

## Add Months

To add a number of months to a date value use the `ADD_MONTHS(date, integer)` function.

