## ACID 

### Atomicity

- *Dataproblem*: En af operationerne i en transaktion fejler

- Systemet garanterer `alt eller intet` - Enten hele transaktionen eller ingenting

### Consistency

- Systemet garanterer at `constrains` er overholdt efter transaktionen

### Isolation

- *Dataproblem*: Operationer fra forskellige transaktioner påvirker hinanden

- Systemet garanterer at transaktioner ikke påvirker hinanden
- Kan løses ved at alle transaktioner afvikles serielt (men giver dårligt performance)

### Durability

- *Dataproblem*: En transaktion bliver markeret som gennemført, men fejler.

- Systemet garanterer at data er persisteret, når man får svar



## I don't know something with scheduling?

### Serial Schedule



### Serializability

Identifies data transactions as occurring serially, independent of one  another, even tough they may have occurred concurrently

### Schedule

List of transactions is deemed to be correct if they are serialized, otherwise, they may contain errors that can lead to duplication or overlap.

### Serial vs parallel

- **Serial** means one event at a time. 
- **Parallel** meaning more than one event happening at a time.



## Questions :

- Hvorhenne løser man det med booking system, som du har snakket mange gange? 

> The classic method to do this is to use a transactional database (so there's no clashes) and to do a *tentative allocation* of the seat to you that expires after some length of time (e.g., 10 minutes for kiosks) that gives you enough time to pay. If the (customer-visible) transaction falls through or times out, the seat allocation can be released back into the pool. (All state changes are processed via the transactional database, and one customer-visible transaction might require many database-level transactions.)



<span style="background-color:#FFB433">**some blue text**</span>


