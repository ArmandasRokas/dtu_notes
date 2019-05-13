- DDL - data definition language
- DML - data manipulation language



## Integrity constraints

- Integrity constraints are usually declared as part of the `create table`  command used to create relations. 

- The allowed integrity constraints include:

  - `NOT NULL`

  - `UNIQUE`

  - `CHECK`  
  	- ```SQL
      CHECK(semester in ('Fall', 'Winter', 'Spring', 'Summer'))
      ```

