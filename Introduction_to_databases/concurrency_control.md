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



## Transaktioner

- Serie af operationer udføres samlet

- Tilstand

  - `Active`
  - `Partially commited` - alle statements er kørt
  - `Failed`
  - `Aborted` - Roll back
  - `Commited`- success

  ![transaktioner_tilstand](diagrams/transaktioner_tilstand.bmp)


## Schedule
- Order of operations
- Can have many transactions in it, each comprising of a number of instructions/tasks
- Is deemed to be correct if they are `serialized`, otherwise, they may contain errors that can lead to duplication or overlap.

![typeofschedules](diagrams/typesofschedules.bmp)


### Serial Schedule

- Transactions are ordered one after the other

### Non-serial schedule

- Supports concurrency

## Serializability

- Concept that helps us to check which non-serial schedules are serializable, i.e. leaves the database in consistent state
- `Non-serial schedule` needs to be checked for `Serializability`
- Identifies data transactions as occurring serially, `independent of one another`, even tough they may have occurred concurrently

### Conflict Serializability

-  A `schedule` is called `conflict serializable` if we can convert it into a `serial schedule` after swapping its non-conflicting operations
- To check whether a non-serial schedule is `conflict serializable` or not

#### Example of NOT conflict Serializability

Lets consider this schedule:

```
T1         T2
-----     ------
R(A)
R(B)
          R(A)
          R(B)
          W(B)
W(A)
```

To convert this schedule into a serial schedule we must have to swap the `R(A)` operation of transaction `T2` with the `W(A)` operation of transaction `T1`. <u>However we cannot swap these two operations because they are conflicting operations</u>.
#### Example of conflict serializable
```
T1         T2
-----     ------
R(A)
          R(A)
          R(B)
          W(B)
R(B)
W(A)
```

Lets **swap non-conflicting operations**:

After swapping `R(A)` of `T1` and `R(A)` of `T2` we get:

```
T1         T2
-----     ------
          R(A)
R(A)
          R(B)
          W(B)
R(B)
W(A)
```

After swapping `R(A)` of `T1` and `R(B)` of `T2` we get:

```
T1         T2
-----     ------
          R(A)
          R(B)
R(A) 
          W(B)
R(B)
W(A)
```

After swapping `R(A)` of `T1` and `W(B)` of `T2` we get:

```
T1         T2
-----     ------
          R(A)
          R(B)
          W(B)
R(A)         
R(B)
W(A)
```

We finally got a `serial schedule` after swapping all the non-conflicting operations so we can say that the given schedule is **Conflict Serializable**.
### View Serializability
- a process to find out that a given schedule is view serializable or not

#### View equivalent

If they satisfy all the following conditions:

1. **Initial Read**

2. **Final Write**

3. **Update Read**


## Concurrency control 

Concurrency control is the procedure in DBMS for managing simultaneous operations without conflicting with each another
https://www.guru99.com/dbms-concurrency-control.html





## Glossary 

### Serial

- means one event at a time

### Parallel/ concurrently/ simultaneously 

- meaning more than one event happening at a time.

### Conflicting operation

- Operations by `different transactions` on the `same data item`, and at least one of these instructions is `write` operation

## Questions :

- Hvorhenne løser man det med booking system, som du har snakket mange gange? 

> The classic method to do this is to use a transactional database (so there's no clashes) and to do a *tentative allocation* of the seat to you that expires after some length of time (e.g., 10 minutes for kiosks) that gives you enough time to pay. If the (customer-visible) transaction falls through or times out, the seat allocation can be released back into the pool. (All state changes are processed via the transactional database, and one customer-visible transaction might require many database-level transactions.)



<span style="background-color:#FAB433">**some blue text**</span>


