Tip and Tricks
==============

### Using the Internet

The Internet, including sites like Stack Overflow, are extremely helpful resources, but they should be **used with caution**. In this program, your goal is to learn to program, not to copy/paste solutions from the Internet. If you cannot complete your lab and project assignments without relying on Google then it is unlikely you will be able to pass the exams in this course, and will end up earning an F in the class.

You should be able to reproduce, without use of the Internet, any code you submit as your own work. If you are called for code review you may get an F on the assignment or in the class if you cannot demonstrate that you are able to reproduce your solution. 

:warning: **No code should ever be copied directly from the Internet** without explicit permission from the instructor. This means you may not select text, copy it, and paste it into your development environment. This also means you may *not* retype exact code from a web page into your development environment. 

So, how *should* you use the Internet? In general, 

1. Google a topic you are confused about. This may result in pages that contain code that is similar to what you need to implement.
2. Look carefully at that solution to *understand* how it works.
3. Close the page you were looking at and reproduce the solution from your own understanding in your development environment. Make sure you understand everything you have implemented and can explain it to the instructor if required.
4. **Cite your source** by adding a comment with the URL where you found the code you used to help you understand the concept. This might look something like this:

```
/**
 * A method to generate a lower-case username containing
 * a user's first initial and full last name
 *
 */
public String getUsername(String first, String last) {
		char firstInitial = first.charAt(0);
		String name = firstInitial + last;
		//https://www.tutorialspoint.com/java/java_string_tolowercase.htm
		//Used online resource to understand how to use String toLowerCase
		//method
		return name.toLowerCase();
	
}
```

### When You're Stuck

Everyone gets stuck, a lot, when learning to program. This is frustrating but part of the process. Learning to program is a bit like learning to play a musical instrument. You must **practice**, a lot, in order to get it right. As you practice, you are likely to mess up, a lot. *Everyone* experiences this. 

The first and most crucial piece of advice I can give you is to **start early**! You must leave yourself enough time to iterate on your solutions. Even if you think an assignment should only take you 10 hours, starting it exactly 10 hours before the deadline is a very bad idea. It is not always possible to make consistent progress on a program. Sometimes you get stuck and need to step away from the problem or seek help before you can solve the issue and move on. **You must leave yourself enough time** to do this.

If you experience a problem you should first spend **at least one hour** trying to solve the problem yourself. If you immediately seek help you are unlikely to develop the independent problem solving skills necessary to be successful in this class, program, and field! If you have been stuck for one hour, you should use the resources available to you. 

1. **Slack** - You are encouraged to use Slack liberally. Ask questions, and answer questions asked by your classmates! You should be careful, however, about posting too much detail about a solution. In general, you should not post code in the public Slack channels. You may direct message the instructor or TAs if you have questions specific to your code. General discussion of code is OK, for example "I ended up using a regular for loop since I need to access the index and couldn't do that with the for-each loop."
2. **TA/Tutoring Center** - You are encouraged to see the TAs during office hours, and to visit the tutoring center. 
3. **Professor Office Hours** - The professor *expects* to see you during office hours. 
4. **Class Notes and Code Samples** - Make sure you have carefully reviewed all of the class resources provided on the website. You'll find lots of hints for your assignments there!




