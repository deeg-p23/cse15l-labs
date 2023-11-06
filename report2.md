### Part 1

The following is the entire code of StringServer.java, changed to fit the demands of this part's question:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler 
{
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String returnedMessages = "";
    int totalMessages = 0;

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return "404";
        } else if (url.getPath().equals("/add-message")) {
            if (url.getQuery().contains("s="))
            {
                String[] QuerySplit = url.getQuery().split("=");

                returnedMessages += (totalMessages+1) + ". " + QuerySplit[1] + "\n";

                totalMessages++;

                return returnedMessages;
            }
            else
            {
                return "Query needs s=";
            }
        }
        else
        {
            return "blank";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

Screenshot 1:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/d893bf05-d8b3-40e5-a932-1014947b7e4a)

- The above screenshot calls the leading method handleRequest, and it uses methods such as getPath, equals, and contains inside of it to evaluate where the page is and what was entered in the query. The method split is also used to retrieve the desired message from the query.
- The argument used in handleRequest is the URI object for the url itself, which will allow us to access and use the path. getPath is called from the url argument itself, equals uses various expected inputs for the path to consider, contains detects if a certain part of the query is used, and split takes the query string and equals sign to access the input side of the query. The fields in the Handler class contain returnedMessages, a string that will have the entire output to be read in the lead path, and totalMessages, an integer numbering the quantity of messages written, used for numbering in returnedMessages. The fields are occupied with totalMessages = 0 and returnedMessages = "" prior to the request being handled.
- For the two fields of the Handler class, returnedMessages and totalMessages, both change after this request is made to the server. totalMessages increases by 1, as 1 new message is added through the path. Then, returnedMessages, which is "", is concatenated with "1. Hello\n" (the 1 comes from returnedMessages). This shows a trend in which totalMessages will increment when the path add-message is used with query s=, and returnedMessages will always concatenate itself with the message typed in the query request.

Screenshot 2:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/208031d6-7bcb-48b5-af4e-39354f4fad45)

- The above screenshot recalls the leading method handleRequest and all of its method calls inside of it again (getPath, equals, contains, split).
- handleRequest's argument is again the URI url, and the same path is used in getPath and equals to evaluate that the user is trying to add-message, but a different input for the query is used for contains and split, because a different kind of message is desired. The fields in the Handler class contain returnedMessages, a string that will have the entire output to be read in the lead path, and totalMessages, an integer numbering the quantity of messages written, used for numbering in returnedMessages. The fields are occupied with totalMessages = 1 and returnedMessages = "1. Hello\n" prior to the request being handled.
- One of the values do change in the output, as spaces aren't considered properly in a url to be output without some different workaround (%20 and + in the url changed nothing), likely because certain special characters in general need to be avoided to consider readability. Besides this, none of the inputs resulted in an unexpected output, or got modified singlehandedly besides the total message string returned, and the usual increment of the number of messages by 1. 

---
### Part 2

Screenshot 1:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/ccd4a550-181c-4c3e-a133-0e3c1e153cce)

Screenshot 2:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/236057ed-517a-463a-b9ee-4fc1ffe0e041)

Screenshot 3:

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/81cf586c-8c1c-4275-a51e-aadd573967b8)

---
### Part 3

One thing I definitely didn't know previously that I learned in week 2/3 was about remote connecting with the ssh command in Linux shells. I also didn't know that you could use it to import and connect a private and public key between a local machine and the remote machine, allowing you to login in securely without having to use a password.
