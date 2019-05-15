## JOINS

- Tager to tabeller og returnerer én
- Giver 
  - 

### Cartesian Product / kartesisk produkt

- Hvis man ikke specificerer, hvordan man joiner
- Joina for each row of one table to every row of another table

#### Exampel of cartesien product

<center><b>Student </b> </center>

| id       |  Name    |        Age  |
| ------------- |:-------------:| -----:|
| 1     | Tom |  18 |
| 2     | Ramesh      |   19 |
|3 | Johnny      |    20 |

<center><b>StudentCourse </b> </center>

| course_id       |  student_id    |
| ------------- |:-------------:|
| 1     | 1 |
| 2     | 2      |
|2 | 3      |

```SQL
SELECT Student.NAME, Student.AGE, StudentCourse.COURSE_ID
FROM Student
CROSS JOIN StudentCourse;
```

OR 

```SQL
SELECT Student.NAME, Student.AGE, StudentCourse.COURSE_ID 
FROM student,studentcourse;
```

<center><b>Output </b> </center>

| name       |  age    |        course_id  |
| ------------- |:-------------:| -----:|
| Tom     | 18 |  1 |
| Tom     | 18      |   2 |
| Tom     | 18      |    2 |
| Ramesh     | 19 |  1 |
| Ramesh     | 19      |   2 |
| Ramesh     | 19      |    2 |
| Johnny     | 20 |  1 |
| Johnny     | 20      |   2 |
| Johnny     | 20      |    2 |

### Inner, outer

- `Inner` and `outer` is **optional** keyword, where:
  -  `inner` is used to join with regular `JOIN ON` 
  -  `outer` is used to join with `LEFT` or `RIGHT` 

