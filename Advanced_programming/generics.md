## Generics

- Tillader at skrive parameteriserede metoder, klasser og interfaces. Mest brugt i collections, nævnt `generics-collections`

### Problem without generic

- ```java
  List users = new ArrayList();
  users.add("User");
  users.add(new Date(1));
  
  String user = (String) users.get(0);
  System.out.println(user);
  String user2 = (String) users.get(1); // will result in java.lang.ClassCastException: java.util.Date cannot be cast to java.lang.String
  ```

- This kind of problem would produce unsafe code with potential bugs as the type of the objects added to the collection cannot be verified by the compiler and compile time.

### With generic

```java
List<String> listNames = new ArrayList<String>();
listNames.add("Tom");
listNames.add("Mary");
listNames.add("Peter");
```

- `listNames` is parameterized with the String type 
- From now on, if you mistakenly add a non-String object into this collection, the compiler will issue an error. 
- Makes code more **safe and readable**
- Elimination of **casts**
- **Enable writing generic algorithms:** with generics, we can generalize our code for reusability, as you see in the code of the List interface and sort() method above.

### Nedarvning
```java
// Extending a particular type
class IntBox extends Box<Integer>{...}
// Extending a parameterized type
class SpecialBox<E> extends Box<E> {...}

Box<String> sb = new SpecialBox<String>("Hi");
```

### Bundne parameterisere typer

```java
public class MathBox<E extends Number> extends Box<Number>
```

- Vi ønsker `E` skal være en `Number` eller en subklasse af `Number`

### Upper bounded wildcards

```java
Box<Number> numBox = new Box<Integer>(31); // Incompatible Type
Box<? extends Number> numBox = new Box<Integer>(31);
```

- Den type `numBox` vi ønsker er "en klasse af enhver type, der extender Number"

### Unbounded Wildcards

```java
Box<?> b1 = new Box<Integer>(31);
Box<?> b2 = new Box<String>("Hi");
b1 = b2;
```

- Compileren kan finde ud af præcis, hvilken type b1 er ud fra højre side af sætningen