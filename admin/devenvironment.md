Development Environment
=======================

In this course we will use the following technologies for developing, testing, building, and submitting programs.

- [IntelliJ](#intellij)
- [Github](#github)
- [Maven](#maven)

Most students have their own laptop computer and find it helpful to bring it to class. If you do not have a laptop then you may use the laboratory computers on campus.

Most professors, and a majority of students, use Macs. Macs, Windows, and Linux computers are all fine. If you are thinking of a new computer and have the budget, a Mac is recommended. If not, any relatively modern laptop will serve you fine for this course. Much of the software is easier to work with on unix-based machines, however.

## IntelliJ
IntelliJ is an Integrated Development Environment (IDE) that provides a friendly interface for building large Java programs. If you wish you may use a different IDE, for example Eclipse or NetBeans, or a text editor like Sublime Text along with the command line. The instructor and TAs will only provide support for IntelliJ, however.

Make sure you are using the most recent version of IntelliJ (2021.1.2) and that it is configured to use Java 16.

1. Download [IntelliJ here](https://www.jetbrains.com/idea/). Select the free Community version.
2. Download [Java 16 here](https://www.oracle.com/java/technologies/javase-downloads.html)
3. Make sure that IntelliJ is configured to use Java 16.


## Github
[Github](https://github.com/) is a web-based version control system. All notes and resources will be posted on github. In addition, all assignments will be distributed and submitted using github. 

Create a github user account if you do not already have one and sign up for the [Student Developer Pack](https://education.github.com/pack). This will be very useful throughout your CS career.

There are several ways to download code from and commit code to github.

1. [Command line](https://www.atlassian.com/git/tutorials/install-git) - If you are a Linux user, or if you want to prepare yourself for future CS classes you should use the command line.
2. [IntelliJ Integration](https://www.jetbrains.com/help/idea/using-git-integration.html) - IntelliJ has an integrated client that makes it easy to access git repositories. 
3. [Github Desktop](https://desktop.github.com/) - If you are a Mac or Windows users you may find it helpful to use the standalone client tool. 

The instructor will generally use some combination of 1 and 2. 

The instructor will use [Github Classroom](https://classroom.github.com/) to manage assignments. For each assignment, you will be provided with a link that you will click to create a new repository. When it is created, that repository will be seeded with skeleton code and test cases. You will download the repository and maintain and submit your code by committing to the repository.

For most assignments, you will follow the following procedure:

1. **Create Repo** - Use the link provided to create your initial repository.
2. **Clone** - Create an initial copy of the repository on your local computer.
3. **Edit/Test** - Edit and test your code. **Do not** modify the test files or any other configuration code provided.
3. **Add** - Add any files that have been modified. **Do not forget this step!**
4. **Commit** - Save the changes you just added.
5. **Push** - Upload the changes to the github servers.
6. **Take a break** - Sleep, shower, eat.
7. **Pull** - Before your start working again, make sure to download any changes. The instructor or TA may have made comments or edits to your code, or you may be working on multiple machines. It is always a good idea to make sure your local copy is consistent with what is on the github server before beginning work again.
8. **Repeat** - Start again at step 3.

It is *strongly* advised that you spend some time reading/watching git resources online. A good place to start is this set of [git guides from Atlassian](https://www.atlassian.com/git/tutorials).

Commit your changes to Github *early and often*. You should *not* use Github as only a submission tool. Every time you get a new method or feature working *commit your changes to Github*! 

## Maven

[Maven](https://maven.apache.org/) is a project management tool we will use for this class. It provides a useful way to describe how to build software and manage its dependencies. You will notice that your projects will contain a file `pom.xml`. This file specifies how to compile the project and any other packages on which the project depends. *Do not modify this file!* In most cases, the instructor will provide this file for you, and this file will be used by the instructor and TAs to grade your solution. 

## Getting Started

The instructions below demonstrate how to get started using IntelliJ, the IntelliJ git integration, and github to complete and submit a practice assignment.

### Create your repo

The instructor will provide you with a link to a README file that outlines the requirements of the assignment. The README will include a link that will allow you to create your own repository for the assignment at the bottom of the page under the heading **Submission Requirements**. 

1. Click the link.
2. Select `Accept this assignment`.
3. It can take a minute or two for the import to complete.

### Clone the repo

1. Visit the web page of your repository, which will look something like: `https://github.com/CS601-F21/practice-<username>`
2. Select `Code` and copy the https URL.
3. Open IntelliJ, specifying the workspace where you want to put the new project.
4. Select `File` > `New` > `Project from Version Control...`.
5. If you have not already, enter your Github credentials.
6. Paste the URI of your repository into the URL field and select `Clone`.

At this point, you should now have a copy of your repository on your local computer.

<!--### Convert to Maven Project

You will now need to tell Eclipse that this is not a "general" project, but a Maven project. Because of the way the github repos are set up (to allow students to use IDEs other than Eclipse) you cannot just import as a Maven project directly.

1. Right-click on the name of the project (e.g., `practice-easy-<username>`) in the Package Explorer.
2. Select `Configure` > `Convert to Maven Project`.

At this point, if you expand the project in your Package Explorer you should see something like the following:

![maven](images/maven.png)

-->
### Edit your code

You may now edit your code.

:warning: Make sure that you do not modify anything in the `src/test/java` directory. 

You are expected to create your own test cases in addition to those provided. You can use JUnit and/or develop your own Driver classes to help you during development.

There are several ways to run the unit tests.

Option 1: To run an individual set of tests right-click on the JUnit test class (e.g., `SayHelloTest.java`) and select `Run '<TEST CLASS>Test`.

Option 2: To run all tests right-click on the project and select `Run All Tests`.

Of course, you can also run from the command line, using either Java or Maven.

### Commit your changes

:warning: Commit your changes early and often! I cannot stress this enough. You should commit your changes anytime you make any change to your code.

1. Select the `Git` menu > `Commit`.
2. In the `Commit Message` box enter a message that clearly describes the change to your code.
3. Select `Commit and Push`.
4. Select `Push` from the dialog box.

:warning: It is very important that you select `Commit and Push`. If you just select `Commit` then your changes will not appear on github.

**Double check** your solution was pushed to github. Visit the repository URL and verify that the code that is checked in is the code you intended to push. *Do not skip this step!* 


<!--## Travis

[Travis CI](https://travis-ci.com/) is a continuous integration tool. For every assignment, once your repository is created the instructor will configure Travis CI to automatically build and run the project test cases every time you commit your code to github. After your repository has been enabled, you may check the status of your latest commit by using your github credentials to log in to [https://travis-ci.com/profile/](https://travis-ci.com/profile/).

If the test cases aren't passing, you know you have more work to do! 

:warning: You should not rely on Travis CI to test your code for you. You should create your own local test cases and also run the provided test cases on your local machine before committing.

The `.travis.yml` file in each of your assignment repositories contains the configuration information necessary to trigger the automated build and test of your program when committed to github. *Do not modify this file!*-->

