## Lab Report 4
### Step 1 (4/9)
Entered into the terminal: 
```
$ ssh cs15lfa23nx@ieng6.ucsd.edu
```
Used this command in order to log in remotely.
Then I entered in my password (didn't setup the private key on this device).

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/6fda7827-60d9-4171-8ba2-c9dde5b66463)

### Step 2 (5/9)

Entered into the terminal:
```
$ git clone https://github.com/deeg-p23/cse15l-lab7
```
Used this command in order to clone the forked repository made on my GitHub profile.

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/143a8577-3921-4226-a67b-fa70e639ce4a)

### Step 3 (6/9)

Entered into the terminal:
```
$ cd cse15l-lab7
```
Used this command in order to enter the cloned repository directory.
Then I ran the test.sh file to view the compilation error that occurs:
```
$ bash test.sh
```

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/13b00aea-0c54-4c4f-9c7c-a93a4abd1954)

### Step 4 (7/9)

Entered into the terminal:
```
$ vim ListExamples.java
```
Used this command in order to enter the file ListExamples.java into the vim editor.

I then pressed the following keys in order so as to edit the file and properly change the final loop's index1 into an index2 and save the edits:
I entered ```:44``` in order to search for the final occurrence of index1 at line 44.
Then, entered ```e``` the end of the word. Then, pressed ```<x>``` to delete it, then ```<i>``` to enter insertion mode, and pressed ```<2>``` to enter 2.
Finally, pressed ```<esc>``` one last time, then ```:wq``` to save and exit the edits.

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/74183a39-b3a5-45c7-93bc-6ed8ba2602c2)

### Step 5 (8/9)

Entered into the terminal:
```
$ bash test.sh
```
Used this command in order to run the given test.sh bash file for compiling and running the tests.

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/78387666-5ed0-4c2b-b5cf-7eb1219c95a0)

### Step 6 (9/9)

Entered into the terminal:
```
$ git commit ListExamples.java
```
Used this command in order to commit the most recent changes applied to the java file.
This entered me into a vim editor for entering a commit message.
I pressed the following keys in this exact order:
Enterd in ```:14``` in order to go down to the last entered line, which is line 14. Then, pressed ```<l>``` to go right by one, ```<i>``` for insert, and ```<enter>``` to insert a new line. Then, I entered the following message, "Replaced index1 with index2 in the last for loop in the file." (without quotes).
Finally, I entered ```<esc>``` and typed ```:wq``` and entered to save my edits and message. 

Then, I entered into the terminal:
```
$ git push
```
I used this command to confirm the changes made.

