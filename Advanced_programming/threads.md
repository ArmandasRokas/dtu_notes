##  Threads

### Intro

- So every application runs as a single process, and each process can have multiple threads. Every process has a heap, and every thread has a thread stack
- **concurrency** - doing more than one thing at a time. Which means that progress can be made on more than one task. One task does not have to complete before another starts

### Hvorfor?

- Kan håndtere mange programmer(processes, bl.a. mus og tekstatur ) samtidigt selv om vi kun har ÉN processor til rådighed
- Some task takes a long time to perform. The main thread wont be able to do anything else while it is waiting for the data

### Two way implement

- Extending the Thread class

```java
public class ThreadExample1 extends Thread {
 
    public void run() {
        System.out.println("My name is: " + getName());
    }
 
    public static void main(String[] args) {
        ThreadExample1 t1 = new ThreadExample1();
        t1.start();
 
        System.out.println("My name is: " + Thread.currentThread().getName());
    }
 
}
```



- Implementing the Runnable interface (fordel når en klasse i forvejen er nedarvet fra en anden klasse)

```java
public class ThreadExample2 implements Runnable {
 
    public void run() {
        System.out.println("My name is: " + Thread.currentThread().getName());
    }
    public static void main(String[] args) {
        Runnable task = new ThreadExample2();
        Thread t2 = new Thread(task);
        t2.start();
        System.out.println("My name is: " + Thread.currentThread().getName());
    }
 
}
```

### Main thread

- Når et java program starter, startes en main thread automatisk
- Fra denne thread kan andre threads dannes(spawnes)
- Main threaden er altid den sidste thread, når denne stopper termineres programmet

### Yield

- en thread kan opgive CPUen ved kald af metoden yield(frivillig tidsdeling)

### Joining threads

- En tråd kan vente på, at en anden tråd bliver færdig

### Synkronisering

- Synchronized objekt - kun en thread ad gangen kan være i dette område

### wait/notify

- En thread kan frigive monitoren midlertidigt ved at kalde `wait`, herved tillades en anden thread adgang til monitoren

- En thread kan aktivere en thread der venter i monitoren ved at kalde notify

- En thread kan aktivere alle ventende threads i monitoren ved at kalde notifyAll


### Thread Variables

- **heap** - the applications memory that all threads share
- **thread stack** - memory that only that thread can access. In other words thread one cannot access threads 2 stack
- **Local variables** are stored in the **thread stack**, that means that each thread has its own copy of a local variable
-  In constrast, the memory required to store an object instance value is allocated on the heap. In the other words when multiple threads are working with the same object they in fact share the same object or share that object so they dont have the own copy and so when one thread changes the value of one of the objects instance variables the other threads will see the new value from that point forward. That means they share instance variables
- When a method is **synchronized**, only one thread can execute that at a time, so when the thread is executing the method all other methods that want to call the method or any other synchronized method in that class will suspend until the thread running the method exits it then another thread can run a synchronized method then another etc. to be clear **if a class has three synchronized methods then only one of these methods can ever run at a time and only on one thread** 
- **synchronized** - we want this whole method to run before another thread gets access to 
- Not to use local variables to synchronize full stop