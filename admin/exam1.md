Exam 1 Review
=============

### Exam Format
- Take home
- Two hour time limit
- *Read-only* resources may be used (notes, class resources, books, Internet)
- **No communication** with others during the exam
- **No copying** any part of a solution from a resource 
- **No communication** with other students who have not completed the exam
- 10-15 questions

The exam will be a take home exam administered as a Canvas quiz.

The exam will be available beginning at 5:00pm on Monday, October 11 for a 24-hour period, until Tuesday, October 12 at 5:00pm. The exam will be **timed**. You will have a time limit of **two hours** to complete the exam once you begin. Per the following Canvas guide: "Timed quizzes begin once a student begins the exam and **do not pause** if the student navigates away from the quiz." 

*Students who have accommodations that grant them additional time will have their time limit extended. If, for example, you are entitled to 2x time on exams then you will have four hours to complete the exam. Exams must be completed before 4:30pm on October 12, and the time limit will not pause once the exam has been started.*

I will be available to answer questions via the [class Zoom link](https://usfca.zoom.us/j/84640666307) during the normal class times on Tuesday (9:55-11:40am and 2:40-4:25pm). You may wish to schedule your two-hour exam period to overlap with those times if you would like the option of asking questions. This is not, however, required.

While you are completing the exam **you may not communicate with any other person about the exam questions**. Communication includes but is not limited to speaking in person, texting, chatting, slacking, tweeting, and posting to online forums. Other persons include but are not limited to your classmates, friends/family, others you know who are developers, and people you interact with online.

You may refer to any other read-only resource; however, **you may not copy text, code, or any other portion of your answers directly from any other resource**. You may use your class notes and any other information available on the class web page. You may use the internet as a read-only resource. You may use any books or other physical resources you have available. If, however, any portion of any answer is directly copied from another resource you will earn an automatic 0 on the exam. 

You **may not share any information about the exam with a student who has not yet completed the exam**. If I discover that students have shared information with other students *both* students will get an automatic 0 on the exam and may get an automatic F in the class. 

The exam will be 10-15 questions in length.

It is strongly advised that you read all of the material posted on the class website.

A partial list of topics covered on the exam is as follows:

### Basic Java

- Syntax
- Static keyword
- Style guidelines
- Exceptions

Example question:

The following program has several problems with coding style. 
Identify at least five problems, and make sure to explain each problem you specify.

```
public class student {
	public String name;
	student(String name, boolean isGrad, double theGrade) {
		this.name = name;
		this.is_Grad = isGrad;
		this.grade = theGrade;
	}

	public boolean isPassing() {
		if(is_Grad) {
			return this.grade > 80;
		} else {
			if(this.grade > 70) {
				return true;
			} else {
				return false;
			}
		}		
	}
	public Boolean is_Grad;
	public double grade;
}
```
  
### Data Structures

- Lists
- Sets
- Maps
- Performance comparison

Example questions:

For Project 1, most students maintained a `HashMap` data structure that stored a mapping between a document ID and an object, i.e., `Review` or `QA` object, that contained the complete document data. Some students, instead, chose to use an `ArrayList` of objects and assigned the document ID as the position in the list. For instance, the first `Review` object in the list had a document ID of 0. Which approach do you think is better *and why*?

Consider an `InvertedIndex` class defined as follows. How would you modify and/or extend this class to provide the ability to search for an exact term and get a list of IDs of documents containing the term *sorted by most recently added document first*? You do not need to provide specific code. You do need to describe (1) any additional data members you would need to add; (2) any changes to existing methods; (3) any new methods you would add (including their parameters and return values); and (4) the algorithms for any new or changed methods.

```
public class InvertedIndex {
	
	// Maps word -> {documentId -> countOfAppearancesInDocument}
	private Map<String, Map<Integer, Integer>> index;
		
	// Takes as input an entire document that is a multi-word string and
	// an integer identifier for the document. Adds each individual 
	// word of the document to the index.
	public void add(String document, int documentID);

	// Takes as input a search word and returns a list of IDs of the 
	// documents where the word appears.
	// The list of document IDs is sorted by term frequency.
	// Term frequency is the number of times the term appears in the document.
	public List<Integer> exactSearch(String word);

	// Takes as input a search term and returns a list of IDs of the 
	// documents where the term appears. The term may appear as part
	// of a word.
	public List<Integer> partialSearch(String term);
	
	// Private helper method to add a new appearance of a single word in 
	// the document with ID documentId.
	private void add(String word, int documentId);


```

### Inheritance
- Super/sub class
- Casting
- Polymorphism
- Dynamic binding

Example question: 

This question refers to the following class definitions:

```
abstract class A {
	public abstract void method();
}

public class B extends A {
	public void method() {
System.out.println(“B method”);	
	}
}

public class C extends B {
	public void method() {
System.out.println(“C method”);	
	}
}
```

Will the following statement compile? For full credit explain your answer.

` A a = new A();`




Will the following statement compile? For full credit explain your answer.
				
`C c = new B();`




What is the output of the following statements?

```
A a = new C();
a.method();
```



### Code design
  * Code smells (DRY, long methods, long classes)
  * Patterns (Singleton, Builder, Factory, Observer, Decorator, Visitor)

Consider a program that has an abstract `User` class. The program has concrete `User` implementations `WebUser`, `MobileUser`, and `DebugUser`. The `WebUser` class is instantiated when a user connects to an application via a browser, the `MobileUser` class is instantiated when a user connects via a mobile device, and the `DebugUser` is used when debugging. Now, consider extending the application so that it further differentiates between a `ChromeUser`, `SafariUser`, and `IEUser`. The developer is considering whether to (1) use the Decorator pattern to have `ChromeUser` decorate `WebUser`, or to (2) have `ChromeUser` extend `WebUser`. Give one argument in favor of *each* approach.
  
### Concurrency/Threads
  * Why use threads?
  * Thread lifecycle
  * Atomicity
  * Race conditions
  * Mutual exclusion
  * `synchronized` keyword
  * Readers/Writers problem
  * Producer/Consumer problem
  * Thread pools
  * `volatile`

Example questions:

The following method decrements a number until it hits 0 and uses a lock to guarantee that no two threads will be modifying the variable at the same time. Is it possible that `num` will ever be less than 0? Why or why not?

```
	public void decrementNum() {
		if(num > 0) {
			lock.writeLock().lock();
			num--;
			lock.writeLock().unlock();
		}		
	}
```


For Project 2 you were not required to implement a `SynchronousUnorderedDispatchBroker`. Would it be possible to implement a `Broker` with this behavior? If so, explain how you would implement it. If not, explain why not.
  
### Sockets and Networking
  * Protocol stack
  * HTTP

Example question:

If a client opened a connection to an HTTP server using a Socket and then did not send a request, what would happen? See below for an example.

```
Socket s = new Socket("google.com", 80);		
int nextByte = s.getInputStream().read();
//what now?
```

Why does the following request to http:cs601-f21.github.io result in a response of `HTTP/1.1 301 Moved Permanently`?

```
GET / HTTP/1.1
Host: cs601-f21.github.io
Connection: close
```
  
### Testing
  * Unit tests
  * Integration tests
  * System tests

Explain *three* tests you did (or should have) implemented to test the functionality of partial search for Project 1.  
