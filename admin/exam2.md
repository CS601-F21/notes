Exam 2 Review
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

The exam will be available beginning at 5:00pm on Monday, November 29 for a 24-hour period, until Tuesday, November 30 at 5:00pm. The exam will be **timed**. You will have a time limit of **two hours** to complete the exam once you begin. Per the following Canvas guide: "Timed quizzes begin once a student begins the exam and **do not pause** if the student navigates away from the quiz." 

*Students who have accommodations that grant them additional time will have their time limit extended. If, for example, you are entitled to 2x time on exams then you will have four hours to complete the exam. Exams must be completed before 5:00pm on November 30, and the time limit will not pause once the exam has been started.*

I will be available to answer questions via the [class Zoom link](https://usfca.zoom.us/j/84640666307) during the normal class times on Tuesday (9:55-11:40am and 2:40-4:25pm). You may wish to schedule your two-hour exam period to overlap with those times if you would like the option of asking questions. This is not, however, required.

While you are completing the exam **you may not communicate with any other person about the exam questions**. Communication includes but is not limited to speaking in person, texting, chatting, slacking, tweeting, and posting to online forums. Other persons include but are not limited to your classmates, friends/family, others you know who are developers, and people you interact with online.

You may refer to any other read-only resource; however, **you may not copy text, code, or any other portion of your answers directly from any other resource**. You may use your class notes and any other information available on the class web page. You may use the internet as a read-only resource. You may use any books or other physical resources you have available. If, however, any portion of any answer is directly copied from another resource you will earn an automatic 0 on the exam. 

You **may not share any information about the exam with a student who has not yet completed the exam**. If I discover that students have shared information with other students *both* students will get an automatic 0 on the exam and may get an automatic F in the class. 

The exam will be 10-15 questions in length.

It is strongly advised that you read all of the material posted on the class website.

A partial list of topics covered on the exam is as follows:

### Pre-Midterm Content

The exam will focus on topics covered since the midterm exam; however, there may be questions related to content covered in the first half of the semester. The topics covered on the midterm exam were as follows:

  * Basic Java
  * Data Structures
  * Inheritance
  * Code design
  * Concurrency/Threads
  * Sockets and Networking
  
Topics such as Concurrency and Sockets have been applied in projects since the midterm; thus, it is recommend that you be prepared to answer questions about those topics, in particular questions related to your assignments.

### Testing
  * Unit tests
  * Integration tests
  * System tests

Example question:

Explain one system test you would use to test a web-based email application. Make sure to include a description of the functionality being tested *and* how you would implement the test. Full credit will be awarded to answers that are as specific as possible.

### HTTP
  * HTTP Protocol
  * HTTP Methods
  * Common Headers
  * Status codes
  * Body format

Example questions:

Consider the following output from a curl request. The server is not behaving correctly. Describe how the server response is incorrect.

```
curl -v localhost:8080/reviewsearch
*   Trying ::1...
* TCP_NODELAY set
* Connected to localhost (::1) port 8080 (#0)
> GET /reviewsearch HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.64.1
> Accept: */*
> 
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml"><head><title>TEST</title></head><body><form action="/reviewsearch" method="POST">
  Query:<br/>
  <input type="text" name="query"/>
  <input type="submit" value="Submit"/>
* Closing connection 0
</form> </body></html>
```

Assume your Project 3 search application solution is running on mcvm050 at port 8080. How should the program respond to the following request?

```
GET /reviewsearch?query=computer
```

### REST
  * Web APIs
  * Why REST?
  * Characteristics of a RESTful API

Example question:
 
The TikTok Share Video API (https://developers.tiktok.com/doc/web-video-kit-with-web) defines the following:
 
```
POST https://open-api.tiktok.com/share/video/upload/
```

Give one argument for why this API endpoint is **not** RESTful.

### OAuth and User Authentication
  * Flow for signing in with a third-party service
  * URL parameters required and their functions

Example question:

In order for your application to allow a user to "Sign in with Slack" you must redirect them to Slack to provide their credentials. After an end user has authenticated with Slack (or any other service) the client must be sent back to your application. How does that happen? Be specific about the mechanics of this process.  

### Monolithic Web Architecture
  * Characteristics of a monolithic architecture
  * Advantages and disadvantages of a monolithic architecture
  * Design of a monolithic application (e.g., Project 4) including APIs, flow from one page to another, data storage

Example questions:

Describe at least *three* characteristics of a monolithic architecture.

Describe the design of a monolithic architecture to implement a bit.ly-like URL shortening application. Make sure to describe the APIs/URL endpoints supported, how the control logic will be decomposed, and how data will be stored. 

What is a "distributed monolith"?


### Microservices
  * Characteristics of a microservice architecture
  * Advantages and disadvantages of a microservice architecture

Example questions:

Describe a disadvantage of using synchronous communication between services in a microservice architecture.

Describe an alternative to using synchronous requests between services in a microservice architecture.

What is the relationship between microservices and REST?

How might the publish/subscribe model be used in the implementation of a microservice architecture?

Consider the design a microservices architecture to implement a web email system like GMail. Describe at least two possible services you would implement. For each service, describe the data the service would store and the API that the service would expose.

Would it be appropriate to decompose the bit.ly-style architecture described above into a microservice architecture. If so, describe how. If not, justify your answer.

### SQL/Relational Databases
  * Why use a relational database?
  * Constructing SQL INSERT and SELECT statements
  * Design of a database schema

Consider a database schema that keeps track of students and, for each student, a list of all email addresses they have provided to a university. 

The students table looks as follows:

```
+-------+--------------+
| Field | Type         |
+-------+--------------+
| name  | varchar(100) |
| id    | int(11)      |
+-------+--------------+
```

The emails table looks as follows:

```			
+-------+--------------+
| Field | Type         |
+-------+--------------+
| id    | int(11)      |
| email | varchar(100) |
+-------+--------------+
```

Should email be a primary key? Why or why not?

Should any of the four fields described be designated as a foreign key? Explain your answer.

Consider the values in the tables below. What would be the result of the following query:

``` 
SELECT name, email FROM students LEFT OUTER JOIN emails ON students.id=emails.id;
```

```
+--------+----+
| name   | id |
+--------+----+
| Jane   |  1 |
| Bob    |  2 |
| Alex   |  3 |
| Sandra |  4 |
+--------+----+
+------+-------------------+
| id   | email             |
+------+-------------------+
|    1 | jane@usfca.edu    |
|    1 | janey@gmail.com   |
|    5 | vincent@yahoo.com |
|    2 | bobby@hotmail.com |
+------+-------------------+
```

Write a query to retrieve all email addresses for a student with a given name.

