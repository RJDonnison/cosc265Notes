# Aggregate Functions

An aggregate function is a function that performs a calculation on a set of values, and returns a single value.

Aggregate functions are often used with the [GROUP BY](Group.md) clause of the [SELECT](Select.md) statement. The [GROUP BY](Group.md) clause splits the result-set into groups of values and the aggregate function can be used to return a single value for each group. To perform filtering with aggregate functions use [HAVING](Having.md).

The most commonly used SQL aggregate functions are:

- [MIN()](MinMax.md) - returns the smallest value within the selected column
- [MAX()](MinMax.md) - returns the largest value within the selected column
- [COUNT()](Count.md) - returns the number of rows in a set
- [SUM()](Sum.md) - returns the total sum of a numerical column
- [AVG()](Avg.md) - returns the average value of a numerical column

Aggregate functions ignore null values (except for COUNT(*)).

## Operators

- [ANY()](Any.md)
- [ALL()](All.md)
