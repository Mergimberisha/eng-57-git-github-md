# Joins in SQL

An inner join selects records that have matching values in both tables.

A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

## Inner JOIN

```SQL
SELECT column-names
  FROM table-name1 INNER JOIN table-name2
    ON column-name1 = column-name2
 WHERE condition
```

## Left JOIN

A left JOIN selects records from the left most table with matching right table records.

```SQL
SELECT column-names
  FROM table-name1 LEFT JOIN table-name2
    ON column-name1 = column-name2
 WHERE condition
 ```

## Right JOIN

 A right join performs a JOIN with the right most table and then matching any left most table records.

 ```SQL
SELECT column-names
  FROM table-name1 RIGHT JOIN table-name2
    ON column-name1 = column-name2
 WHERE condition
 ```

## Full JOIN

A Full JOIN returns all matching records from both tables whether the other table matches or not.

A full JOIN can potentially return very large data sets.

    ```SQL
SELECT column-names
  FROM table-name1 FULL JOIN table-name2
    ON column-name1 = column-name2
 WHERE condition
 ```
