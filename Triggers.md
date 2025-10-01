# Triggers

A trigger is a SQL procedure that runs automatically when an event occurs in the database. You can use triggers to check values before insert/update, create backups, or maintain data integrity.

## Types of Triggers

For each table, you can create 6 types of triggers:

- AFTER INSERT → Runs after a row is inserted.
- AFTER UPDATE → Runs after a row is updated.
- AFTER DELETE → Runs after a row is deleted.
- BEFORE INSERT → Runs before a row is inserted.
- BEFORE UPDATE → Runs before a row is updated.
- BEFORE DELETE → Runs before a row is deleted.

## Syntax

```
CREATE [OR REPLACE] TRIGGER trigger_name
{ BEFORE | AFTER | INSTEAD OF }
{ INSERT | UPDATE [OF column_list] | DELETE }
ON table_name
[ FOR EACH ROW ]
DECLARE
   -- optional variable declarations
BEGIN
   -- trigger logic here
   -- :NEW.column_name  (new values)
   -- :OLD.column_name  (old values)
EXCEPTION
   -- optional exception handling
END;
/
```

## Examples

Prevent inserting employees younger than 25. This trigger runs before inserting into employee. If the age is less than 25, the insert will fail with an error message.

```
CREATE OR REPLACE TRIGGER check_age
BEFORE INSERT ON employee
FOR EACH ROW
BEGIN
   IF :NEW.age < 25 THEN
      RAISE_APPLICATION_ERROR(-20001, 'ERROR: AGE MUST BE AT LEAST 25 YEARS!');
   END IF;
END;
/
```
