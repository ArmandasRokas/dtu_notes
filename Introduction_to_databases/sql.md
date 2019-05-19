### SQL
- SQL  er deklaritiv sprog
- Har dog imperative elementer (fuctions, triggers)
### DDL -  data definition language
- Data struktur
- Constraints, access, keys

### DML - data manipulation language
- Data sprog
- Data operationer
- Algebra, mængdelære, prædikat logik

### Functions
- Avanceret select
- Skal returnere værdi/tabel
- Indbyggede funktioner
  - ABS(), COS()
- *A function can be called **from inside a statement** just like any other function and can return a scalar value.*

### Stored procedures

- Mere avanceret end funktions
- Serie af SQL statements og kode
- Har try-catch
- Transactions
- Kan kalde functions
- *A procedure is invoked using a **CALL statement** and can only pass back values using output variables.*

### Triggers

- SQL der kan køres automatisk ved modifikation af databasen
  - INSERT, UPDATE, DELETe
- Hvad skal den bruges til?
  - Logge historiske data. Versionering
- Pas på med triggers - kan fyres af på uheldige tidspunkter(mens man rydder op eller loader backups ind)
### Recursion
- Hvorfor?
	- Facebook - venners venner
	- Grafer
- 	Frygteligt kompiceret - kan oftest løses med iteration



