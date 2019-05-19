## Valget af database typen

- Vælg type efter use case
- Skema vs. ikke skema
  - strukturerede vs ustrukturedede
- Flad vs træ struktur
- Consistency vs Performance
  - Transactions?

- Query type
  - Graf
  - Relationships
- Polyglot persistence

## Types

### Key-value

- Simpleste db-type
- Grundlæggende funktionalitet som et HashMap
- Intet skema, ustrukturede data
- **Pros**:
  - Simple at bruge
  - Høj performance
- **Cons**:
  - Svært at håndtere komplekse data, eks. ingen joins
- **Use**: 
  - Cache(Session, web-page), Køer
- **Eksampel**:
  - Redis

### Wide Column

- Dynamsik og meget stort antal kolonner
- 2D Key-Value store (Gigantisk Excel ark)
- Intet skema
- **Pros**:
  - Distrubution, availabilty, scalability (lineært)
  - SQL-lignede sprog (Cassandra)
- **Cons**:
  - Ingen ACID, sekundære indeces, igen JOINs
- **Use**: 
  - Logging, IOT,  Twitter, Real-time analyse
  - Høj skrive aktivitet, få updates
- **Eksampel**:
  - Redis

### Documents Oriented

- Træ-struktur (JSON), næstede objekter gemmes i samme Collection. Identisk med objekter i OOP
- Intet skema

- **Pros**:
  - Godt til komplekse objekter
  - Høj availabilty, performance
  - Har får transaction fornylig
- **Cons**:
  - Ingen Joins
- **Use**: 
  - Produktkatalog, Log data, Content Management
  - Ustrukturerede data, store datamængde

#### Eksample: MongoDB

- Hurtigt udvikling
- Ingen normalisering, constrains
- Weak entities er nestede
- Lookups svarer til Left join
- Redundans
- **Navngivning**
  - Database - database
  - Table - collection
  - Row - document

### Graph

- Data er grafer
- **Pros**:
  - Performance på queries på relationships
  - Aggregation (samle data i flere niveauer)
- **Cons**:
  - Besværlig distribution, forskeliggartet sprog
- **Use**: 
  - Netværk, analyse, AI og machine learning, fraud detection, supply chain
  - Facebook, LinkedIn
- **Eksampel**:
  - Neo4J
- **Ikke populær** fordi
  - Besværlig syntax
  - GraphQL sproget kan give andre databaser nogle af de samme egenskaber (GraphQL er **ikke** en database) 
### Elastic search

- **Pros**:
  - God til at indeksere store mængder af inhomeogene data, dvs. alt bliver indekseret
  - Kan fiske data fra andre typer af databaser

- **Use cases**:
  - Søgninger i meget store datamængder
  - Wikipedia, Stack overflow, Github

### Polyglot Persistence

- Blanding af flere databaser i samme system
- Eks.:
  - SQL til relationelle data
  - Mongo til produktkataloget
  - Elastic til at søge i log filer 

## Relational vs non-relational databases
![relationalvsnon](https://content-static.upwork.com/blog/uploads/sites/3/2015/06/02170023/relational-vs-nonrelational-databases.png)

*Non-relational har en blog post med sine comments, tags, categories osv.*

*Relational alle blog post er samlet et sted og comments den anden sted og man joiner dem*

### Relational

- The relationship between tables and field types is called a **schema**. In a relational database, the schema **must be clearly defined** before any information can be added.
- Minimizes data redundancy and prevents tables from becoming out-of-sync

### Non-relational

- Enter non-relational databases, which offer much greater **flexibility** than their traditional counterparts. Think of non-relational databases more like file folders, assembling related information of all types.