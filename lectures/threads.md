Concurrency and Threads
=======================


## [Introduction to Java Threads](https://www.ibm.com/developerworks/java/tutorials/j-threads/j-threads.html) 

Author: Brian Goetz

> ### What are threads?
> Threads are sometimes referred to as lightweight processes. Like processes, threads are independent, concurrent paths of execution through a program, and each thread has its own stack, its own program counter, and its own local variables. However, threads within a process are less insulated from each other than separate processes are. They share memory, file handles, and other per-process state.


> ### Why use threads?
> Some of the reasons for using threads are that they can help to:

> - Make the UI more responsive
> - Take advantage of multiprocessor systems
> - Simplify modeling
> - Perform asynchronous or background processing

## Implementation

There are a couple of ways to use threads in your code. One approach is by creating a class that implements the `Runnable` interface and another class that creates a `Thread` to execute the `run` method. An example follows:

```java
public class InfinitePrinter implements Runnable {
	
	@Override	
	public void run() {		
		//main job executed in this thread
		//this will execute when Thread's start method is invoked
		int count = 0;
		while(count < Integer.MAX_VALUE) {
			System.out.println(count++);			
		}
	}

}
```

```java
public class ThreadTest {

	public static void main(String[] args) {

		Thread t1 = new Thread(new InfinitePrinter());
		t1.start();
		
		Thread t2 = new Thread(new InfinitePrinter());
		t2.start();

	}
	
}
``` 

## Thread Life Cycle

[Baeldung - Life Cycle of a Thread in Java](https://www.baeldung.com/java-thread-lifecycle)

![](https://www.baeldung.com/wp-content/uploads/2018/02/Life_cycle_of_a_Thread_in_Java.jpg)

## Definitions

### Critical Section
In the example above, the two instances of `InfinitePrinter` operate completely independently. They do not share any data, thus we need not worry about the order in which they are executed.

Generally, however, multiple threads will operate on *shared* data or otherwise access a shared resource. A **critical section** is the portion of the program where a thread accesses a shared resource. Typically only one thread may access the critical section at a time.

### Atomic Operations
To understand why critical sections are necessary it is necessary to understand the concept of **atomicity**.  An **atomic operation** is an operation that appears as a single step to other threads. Even if the operation is multiple steps, other threads will not see the intermediate steps and may not interrupt the operation.

Consider the following example:

```java

public class Adder {

	int value = 0;
	
	public static void main(String[] args) {
		
		Adder a = new Adder();
		
		Thread t1 = new Thread() {
			public void run() {
				for(int i = 0; i < 30000; i++) {
					a.value++;
				}
				System.out.println("thread 1 complete");
			}
		};
		
		Thread t2 = new Thread() {
			public void run() {
				for(int i = 0; i < 30000; i++) {
					a.value++;
				}
				System.out.println("thread 2 complete");
			}
		};
		
		t1.start();
		t2.start();
		
		try {
			t1.join();
			t2.join();
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		System.out.println(a.value); 
		
	}
	
}

```

The operation `a.value++` is *not* atomic!

Similarly, consider the following implementation of the `Singleton` pattern:

```java

public static Singleton getInstance() {
	if(instance == null) {
		instance = new Singleton();
	}
	return instance;
}
```

The `getInstance` method is not atomic, therefore two threads could see `instance` as null and each decide to create a new instance of the object, violating the pattern.

### Race Condition

The `Singleton` example above defines a **race condition**. The behavior of the program could be incorrect if the scheduling of the threads is not as expected. Essentially, a race condition occurs if the programmer expects code to be executed in a particular order but the threads are scheduled such that the expected order is not preserved.

### Mutual Exclusion

**Mutual exclusion** is used to prevent race conditions by ensuring that only one thread may access the critical section at a time. 

In Java, one way to ensure mutual exclusion is through the use of [`synchronized`](https://docs.oracle.com/javase/tutorial/essential/concurrency/syncmeth.html). This keyword may be applied to a method or a code block ([Baeldung examples](https://www.baeldung.com/java-synchronized)).

## Classical Synchronization Problems

There are several classical synchronization problems you may have learned about in Operating Systems class. Like with design patterns, understanding these problems and their solutions can help you more quickly and easily solve new problems with similar properties.

### Readers/Writers Problem

In this problem, a shared piece of data may be read from or written two by multiple threads. If there is a writer then no other thread may be reading or writing concurrently. Multiple readers, however, *may* concurrently read the data.

A typical approach to solving this problem is by using a read/write lock. If the write lock is held then no other thread may hold a read or write lock. If the read lock is held then another thread may hold a read lock but no other thread may hold a write lock.

#### Thread-safe Data Structures and Utilities

The `java.util.concurrent` package has several useful utilities: 

- [Overview of Concurrent](https://www.baeldung.com/java-util-concurrent)
- [API Summary](https://docs.oracle.com/en/java/javase/16/docs/api/java.base/java/util/concurrent/package-summary.html)

Java, for example, offers a `ConcurrentHashMap`. This is a *thread safe* data structure that guarantees that calls to any of the methods are thread safe. 

:warning: Swapping out a non-thread safe data structure for a thread safe one will not necessarily solve all of your problems! Consider two threads that execute the following sequence of operations. 

```java
if(!map.containsKey(key)) {
	map.put(key, value);
}
```

This is a *compound operation*. This multi-step sequence is not atomic and not thread safe even if performed on a `ConcurrentHashMap`. 

### Producer/Consumer Problem

The producer/consumer problem is similar to, but a slightly more restricted version of the readers/writers problem.

A producer and consumer share a bounded buffer. If the buffer is full when the producer tries to add an item it will block until there is space. If a consumer tries to take an item and the buffer is empty then it must block until an item has been added.

## Additional Concepts

### Thread Pools

Creating new `Thread` objects generates significant overhead. Thread pools create a pool of threads that can be reused to execute incoming jobs.

### `volatile`

There are a *very small number* of cases where the keyword `volatile` may be used in place of synchronization in Java.

From [https://www.baeldung.com/java-volatile](https://www.baeldung.com/java-volatile)

> In Java, each thread has a separate memory space known as working memory; this holds the values of different variables used for performing operations. After performing an operation, thread copies the updated value of the variable to the main memory, and from there other threads can read the latest value.

> Simply put, the volatile keyword marks a variable to always go to main memory, for both reads and writes, in the case of multiple threads accessing it.

<!--Take a careful look at the [patterns for using `volatile` correctly](https://www.ibm.com/developerworks/java/library/j-jtp06197/)
-->
Also, [this tutorial](http://tutorials.jenkov.com/java-concurrency/volatile.html) has some good diagrams explaining the concept.

### Synchronous vs. Asynchronous/ Blocking vs. Non-blocking

It is very important to understand the concepts of synchronous vs. asynchronous and blocking vs. non-blocking.

Suppose a thread calls a method `m` and that method will write some data to a file.

If the method is synchronous then the method will not return to the caller until the data has been written. If the method is asynchronous then the method will return to the caller immediately and the data will be written to the file at some point later.

If a call to a method blocks that means it does not return until something happens. The `Scanner` method `nextLine` blocks until the user enters a line of text at the keyboard. 

A non-blocking method may execute a task asynchronously so that it may return without blocking the caller.


### busy-wait

If a thread needs to block until another has completed some action it is generally better practice to use `wait` and `notify` rather than a busy-wait loop that consumes CPU cycles as below:

```java
package concurrency;

public class BusyWaiter {

	volatile boolean finished = false;

	public static void main(String[] args) {

		BusyWaiter bw = new BusyWaiter();

		Thread t1 = new Thread() {
			public void run() {
				//replace this while loop with a call to wait()
				while(!bw.finished) {} // <- not a good solution!
				System.out.println("finished!");
			}
		};

		Thread t2 = new Thread() {
			public void run() {
				System.out.println("doing some stuff that takes awhile...");
				for(int i = 0; i < Integer.MAX_VALUE; i++) {
					//doing some stuff
				}
				//replace this boolean update with a call to notify
				bw.finished = true;
			}
		};

		t1.start();
		t2.start();

		try {
			t1.join();
			t2.join();
		} catch(InterruptedException ie) {

		}

	}	

}
```