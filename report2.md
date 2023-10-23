### Part 1

Screenshot 1:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/d893bf05-d8b3-40e5-a932-1014947b7e4a)

- The above screenshot calls the leading method handleRequest, and it uses methods such as getPath, equals, and contains inside of it to evaluate where the page is and what was entered in the query. The method split is also used to retrieve the desired message from the query.
- The argument used in handleRequest is the URI object for the url itself, which will allow us to access and use the path. getPath is called from the url argument itself, equals uses various expected inputs for the path to consider, contains detects if a certain part of the query is used, and split takes the query string and equals sign to access the input side of the query.
- None of the values change in the output in a significantly unexpected way besides the expected increase of a new message to the originally empty string of messages, as does an integer meant for measuring the number of messages input; and none of the inputs are directly modified either, simply because the methods used either just evaluate the given strings or creates a new one.

Screenshot 2:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/208031d6-7bcb-48b5-af4e-39354f4fad45)

- The above screenshot recalls the leading method handleRequest and all of its method calls inside of it again (getPath, equals, contains, split).
- handleRequest's argument is again the URI url, and the same path is used in getPath and equals to evaluate that the user is trying to add-message, but a different input for the query is used for contains and split, because a different kind of message is desired.
- One of the values do change in the output, as spaces aren't considered properly in a url to be output without some different workaround (%20 and + in the url changed nothing), likely because certain special characters in general need to be avoided to consider readability. Besides this, none of the inputs resulted in an unexpected output, or got modified singlehandedly besides the total message string returned, and the usual increment of the number of messages by 1. 

---
### Part 2

Screenshot 1:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/4e4207d5-367f-4d4b-8121-7d3e916bf37e)

Screenshot 2:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/236057ed-517a-463a-b9ee-4fc1ffe0e041)

Screenshot 3:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/81cf586c-8c1c-4275-a51e-aadd573967b8)

---
### Part 3

One thing I definitely didn't know previously that I learned in week 2/3 was about remote connecting with the ssh command in Linux shells. I also didn't know that you could use it to import and connect a private and public key between a local machine and the remote machine, allowing you to login in securely without having to use a password.
