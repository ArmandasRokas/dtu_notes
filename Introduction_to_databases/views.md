### Views

- VIEWS are virtual tables. By virtual, we mean, the tables **do not store any data** of their own but **display data stored in other tables**

```sql
CREATE VIEW students AS SELECT * from student;
DROP VIEW students;

// Hvis man indsætter noget i student, så man får også det i students.
```

- Views kan også bruge andre views

### Materialized views

- Fysisk tabel, der spejler andre tabeller
- Skal vedligholdes 
- Kan forbedre performance
- Eksisterer **ikke** explicit i MySql
  - Skal laves manuelt i MySQL med CREATE table og triggers

### WITH

- used for defining a **temporary tabels** such that the output of this temporary tabel is available and is used by the query that is associated with the WITH clause
```sql
WITH temporary_Table(averageValue_Column) as
    (SELECT avg(Salary)
    from Employee), 
        SELECT EmployeeID,Name, Salary 
        FROM Employee, temporary_Table 
        WHERE Employee.Salary > temporaryTable.averageValue;
```
