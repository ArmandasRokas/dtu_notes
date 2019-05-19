## Keys

- Integrity
- Unique
- Improves functionality (speed)

### Super key

- **Any number** of columns that creates unique row. 

Only for designing purposes. Is it possible to define unique row?

### Candidate key

- **The least number** of columns that creates unique row?
- How many Candidate keys are there?
  - CD_1: user_id 
  - CD_2: user_name
  - CD_3: email

### Primary key

- Pick one candidate key
- They should always be
  - Unique
  - Never changing
  - Not null
- Categories of primary keys
  - `Surrogate` - made up keys - e.g. id
  - `Natural` - e.g. username, email
- Composite primary key - is made of more than one attribute.  Usually when it is natural key. 

- Compound primary key -combination of foreign keys is unique

### Foreign key

- references PK, that connects tables. Keeps database consistent

- Can be **NULL**

- **Constrains** `ON DELETE` or `ON UPDATE`

  - `Restrict`
  - `Cascade`
  - `SET NULL`

  
