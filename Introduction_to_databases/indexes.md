

### Query optimering

- Indexering er en måde at øge hastiheden på opslag/queries
	- Fra linær til log-tid
	- Potentielt fra timer til sekunder 
- Search key - attribute der slås op efter
- Index består af key og pointers
- Indeksering
	- Ordnede indices
	- Hash

### Index architecture
#### Primært index / clustering index
- Indexet, der afgør den fysiske lagring af data
- Primary key er automatisk indekseret i MySql
- Værdier gemmes i rækkefølge
  - 1,2,3,4 (numerisk)
  - a, abe (leksikografisk)
- Orginizes actual data  (can be only one in table)
#### Sekundært index / non-clustering
- Ekstra index til at søge på andre kolonner
- Foreign keys bliver også indexet automatisk 
- list with pointer to data
- The physical order of the rows is not the same as the index order.
- The indexed columns are typically non-primary key columns used in JOIN, WHERE, and ORDER BY clauses. A field which is a candidate key and has a unique value in every record

### Oredered indexing is of two types
#### Dense 
- en entry i index for hver søgeværdi
![denseindex](https://www.tutorialspoint.com/dbms/images/dense_index.png)

#### Sparse
- kun på primær index eller i multilevel index
- kun nogle værdier har index-værdi (eks. for hver block på hdd)
  - duer ikke til sekundære indices
![sparseindex](https://www.tutorialspoint.com/dbms/images/sparse_index.png)
### Multilevel index 
- Sparse index på indexet
- Bruges når index bliver for stort til hukommelsen
![multilevelindex](https://www.tutorialspoint.com/dbms/images/multi_level_index.png)


### String indeksering
- Performer godt med wildcards til sidst
- Performer ikke med wildcards til start
- Alternativt FULLTEXT index
### Multi-key index / multiple columns
- Flere nøgler i same index
- Vigtigt at vælge rigt rækkefølge til index
- Most left can be used alone
### Covering indexes
- Ekstra kolonner medtages for performance gain

## Index implementation
### Hashing
- Hash funktion og nøgler jævnt fordelt i buckets
- Potentielt O(1) opslag
- I praktsis sjæland bedre end B-tree
- HashMap er alletiders til applikationer
- MySql understøtte ikke
### B-Trees
- Standart index i SQL databaser
- Kombination af
  - Balanceret søgetræ
  - Hægtet list (linked-list)
- Fordele
  - Understøtter både opslag på værdi og intervaller
- Ulemper
  - Overhead ved 'mutation'
  - Pladsforbrug
### R-Tree
- B-tree til fler-dimensionelle data(spatielle data)
- opdeler til rektangler

## Should be used

- Columns used with WHERE
- Columns used to Join tables

## Disadvantage

- Take time to update  (no add indexes on columns, which do not need them)
- Minimalt overhead(costs) på mutations
  - Create, Update, Delete
- Minimalt pladsforbrug

## EXPLAIN

- Execution plan
- DB motoren gør ikke altid hvad man forventer