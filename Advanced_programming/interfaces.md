## Interface

- I et interface erklæres der en række metoder som en klasse skal implementere for at den kan siges at være af denne typen. 

- Opnår lav kobling GRASP 

- Koden referer kun til interfacet, men kender ikke den konkrete implementering

- Mere robust, idet ændringer i implementeringen ikke påvirker brugeren af interfacet.

- Interfaces udgør en kontrakt mellem brugeren og implementatoren af interface (interface defines a contract with the outside world,)

- To summary, an interface defines common behaviors of a type without providing detailed implementation. It separates the WHAT from the HOW. The WHAT is strict but the HOW varies depending on actual implementations.

- Alle metoder der erklæres i et interface er pr. definition: **abstract public**, **cannot** be `static` and `final`

- ```java
  interface Color {
    int RED = 0xff0000; // means: public static final int. Declares a constant
  }
  ```
```



### Comparable

- bør implementere dette interface hvis vi ønsker at sammenligne to objekter af klassen, herunder hvis vi ønsker at sortere objekter
- Givet to objekter o1, o2 skal compareTo metoden returnere følgende
  - o1 < o2 --> negativt tal
  - o1 = o2 --> 0
  - o1 > o2 --> positivt tal

## Polymorfisme

- mange former
- `IRef` kan referere til mange implementationer
- You see, by making the parameter of the `create(User)` method as an interface, we can pass any objects whose class implements the User interface into the method, thus facilitates the concept of **polymorphism** in OOP

​```java
public class DefaultUser implements User, Comparable {
    // implementation for User
     
    // implementation for Comparable
}
```

-  Here, the `DefaultUser` class is of two types: `User `and `Comparable`. When being used with the `UserDAO`, it is a `User`. When being used with a collection e.g. `ArrayList`, it is a `Comparable`. This is multiple inheritances with interfaces, which adds flexibility to the program.



## API(Application programming interface)

- In computer programming, an application programming interface is a set of subroutine definitions, communication protocols, and tools for building software. In general terms, it is a **set of clearly defined methods of communication** among various components.

### JDK

Java Development Kit (JDK) is comprised of three basic components, as follows:

- Java compiler
- Java Virtual Machine (JVM)
- Java Application Programming Interface (API)

The Java API, included with the JDK, describes the function of each of its components. In Java programming, many of these components are pre-created and commonly used

### References 

https://www.codejava.net/java-core/the-java-language/everything-you-need-to-know-about-interfaces-in-java