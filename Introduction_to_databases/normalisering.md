## Funktional afhængighed
- Hver værdi for en attribut er associeret med præcis én værdi for en anden attribut
  - Dvs. der findes kun én værdi for en given attribute
#### Eks. af funktional afhængighed:

- `STUD_NO ---> STUD_name`
  - For en given STUD_NO, eksisterer der kun én STUD_name værdi
- STUN_name funktionalt afhænger af STUD_NO
  
- `bilmærke ---> land`
  - For en given bilmærke, eksisterer der kun ét land
  - land funktional afhænger af bilmærke

## Normalisering

### Hvorfor?

- Løser problemer med **redundans** og **insert, update og delete anomalier**
- Normalisering er et værktøj til at minimere redundans



### 1NF

- **Ingen éns rækker** (dubletter) 
  - primærnøgle
- **Atomic kolonner** (single valued attribute) 
  - ikke composite. eks. fornavn + efternavn
  - cpr-nummer heller ikke atomic
- **Ingen gentagne grupper** 
  - ikke multi value eks. liste af telefonnumre
- **Kun én slags data i hver kolonne** 
  - komme fra den samme domæne
  - format skal være éns
  - must be of the same kind or type:
    - **For example:** If you have a column `dob` to save date of births of a set of people, then you cannot or you must not save 'names' of some of them in that column along with 'date of birth' of others in that column. It should hold only 'date of birth' for all the records/rows.
- **Hver kolonne har en unik navn**  

### 2NF
- **1NF + Ingen partielle afhængigheder**
- En ikke-primær attribute må ikke være afhængig af en del af en kandidatnøglen

```
Manufacturer	Model			Model Full Name		Manufacturer Country
-------------------------------------------------------------------------
Forte			X-Prime			Forte X-Prime		Italy
Forte			Ultraclean		Forte Ultraclean	Italy
Hoch			Toothmaster		Hoch Toothmaster	Germany
```

- `{Manufacturer, Model}` - kandidatnøglen
- Partielle afhængighed her at, `Manufactuter ---> Manufacturer Country` . Dvs. uden `Model` 
#### Løsning til at opnå 2NF

- Ikke-primær attribute med partiel afhængighed for egen tabel, hvor nøglen bliver den del af kanditatnøglen som den er afhængig af

```
Manufacturer		Manufacturer Country
-----------------------------------------
Forte				Italy
Hoch				Germany
```




### 3NF

- **2NF + Ingen transitive afhængigheder**
- Ingen ikke-primær attribute afhænger af andre ikke-primær attributer

```
Tournament		Year	Winner		Winner Date of Birth
---------------------------------------------------------
Indiana Invit.	1998	Tommy		21 July 1975
Cleveland Open	1999	Johnny		28 September 1968
Des Moines		199		Tommy		21 July 1975
```

- `{Tournament, Year} ---> Winner`
- `Winner ---> WinnerDate of Birth`, såfremt Winner er **ikke**-primær, så er det ikke på 3NF

#### Løsning til at opnå 3NF
- Ikke-primær attribut med transitiv afhængighed får egen tabel, hvor nøglen bliver den attribut, som den er transitivt afhængig af
```
Winner		Date of Birth
------------------------------
Tommy		21 July 1975
Johnny		28 September 1968
```
### BCNF 3½ (Boyce Codd)

- **3NF + for hver afhængighed `A-->B` , A skal være kandidatnøglen**. Dvs. A kan ikke være ikke-primær attribute, hvis B er primær attribute. 
- Bruddet på BCNF kunne opstå, hvis primær attribute afhænger af ikke primær attribute

```
student_id	subject		professor
---------------------------------
101			Java		P.Java
101			C++			P.Cpp
102			Java		P.Java2
104			Java		P.Java
```

- Vi skal antage, at en professor **kun** underviser ét subject, men et subject må have flere proffessors

- Det giver, at `professor--->subject`, professor er ikke-primær, mens subject er en del af kandidatnøglen. Så det brydder BCNF.

#### Løsning til opnå BCNF
```
p_id		professor		subject
-----------------------------------
1			P.Java			Java
2			P.Java2			Java
3			P.Cpp			C++
```
- Problemmet er løst, at der kan være flere inputs i en oprindelig tabel med student_id og subject og professor flere gang, fordi hvis subject navn skal ændres kan da opstå update anomalier

### 4NF 
- **BCNF + igen uafhængige multi-value afhængigheder**
- Der må ikke være flere kolonner med flere værdier, der ikke ar afhængige

```
s_id	course		hobby
--------------------------
1		Science		Cricket
1 		Math		Hockey
2		C++			Cricket
2		PHP			Hockey
```

- to attribute med flere værdier `course` og `hobby`
- Multivalued dependancies:
  - `s_id -->--> course`
  - `s_id -->--> hobby`
#### Løsning på til opnå 4NF
- Lave `s_course` og `s_hobby` tabeller


## Denomalisering

- Nogen gange vælge man ikke at normalisere data, fordi **JOIN er for dyrt**
- **Pro**: Performance forbedring
- **Con**: Constrains, redundans og data anomalier er applikationens problem
- **Alternativ løsning til denomalisering**: Materialized View 
- **The rule of thumb**: If `performance` is unsatisfactory and a table has `low update rate` and a very `high query rate`, `denormalization` may be a possible option. 



## Glossary

#### Non-prime attribute

- An attribute that is not part of **any** candidate key is known as non-prime attribute.

#### Relationships between relations

