## JDBC

- Java API til databsseadgang
- Kræver en driver til databasen
  - computer program that implements a protocol for a database connection
- Connections 
  - Dyre at oprette
  - Husk at lukke
  - Brug en connectionPool
- Prepared statements
- (boolean) execute(), (ResultSet) executeQuery(), (int) executeUpdate()
- autocommit(false)
  - transaction