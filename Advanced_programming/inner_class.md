## Inner class
- En medlem af den omsluttende klasse på lige fod med andre felter (attributer, metoder)
- Exception klasser der kun benyttes ifm. en interface type kan med fordel defineres som inner klasser til interfacet

### Why
- Grouping related code together
- Increasing code encapsulation
- Making the code more readable and maintainable
- 
### static inner class

- har kun adgang til statiske medlemmer i den omsluttende klasse

### non-static

- har adgang til alle felter i den omsluttende klasse
- er bundet til objekter af den omsluttende klasse og har en speciel `this` reference

```java
public class A{
    int a;
    int b;
    B bref;
    A() {
        a = 5;
        b = 6;
        bref = new B();
    }
   	class B{
        int b;
        B() {
            b = 9; // this.b or A.B.this.b
            A.this.b = 10;
            a = 7; // A.this.a
        }
    }
    public String toString(){
        return "A.a: " + a + "A.b: " + b + "B.b: " + bref.b;
    }
    public static void main(String[] args){
        System.out.println(new A());
    }
}
```

- En fuldt kvalificeret reference til instans felter af inner objektet er på formen 
  - `<Outerclass>.<Innerclass>.this.<field>` 
- Kvalificering kan udelades hvis der ikke er navnesammenfald mellem felter i inner objektet og det omsluttende objekt

### Instantiering af Inner klasser

```java
class A{
    ...
    A(){...}
    class B{
        B(){...}
    }
}
public class TestInner{
    public static void main(String[] args){
        A.B bref = new A().new B();
    }
}
```

### Lokal inner klasse

- defineres i en metode
- kan være navgivne eller anonyme
- navngivne klasser kan have konstruktører på lige fod med andre klasser

```java

public class Client1 {
    public Client1() {}

    public void register(String s){
        // local inner class
        class LogToScreen implements ILog{
            @Override
            public void log(String s) {
                System.out.println(s);
            }
        }
        new LogToScreen().log(s);
    }

    public static void main(String[] args){
        Client1 client1 = new Client1();
        client1.register("Hi");
    }

}

interface ILog{
    void log(String s);
}

```

### Anonym lokal inner klasse

- make code more concise

- enable you to declare and instantiate a class at the same time

- like local classes except that they do not have a name

- use them if you need to use a local class only once

- en anonym inner klasse kan ikke selv have en konstruktør, i stedet kan der benyttes en initialiserings blok

- `new class-name([argument-list]){class-body}`
  - baseret på nedarvning af en eksisterende klasse
  
  - argumentlisten overføres til superklassen konstruktør
  
  - class body indeholder data og metoder (overskrevene eller nye)
  - ```java
  SomeClass x = new SomeClass(){
        ...
        @Override // methods in SomeClass
    }
    ```
  
- `new interface-name() {class-body}`
  - vedrører implementering af et interfacet
  - ```java
    Runnable r = new Runnable(){
        public void run() {...}
    }
    ```

