### Part 1 : Debugging Scenario

#### 1. Student's Problem

The student is having a problem trying to figure out why their implementation of ListExamples from lab 7 is not passing both given tests:

> I'm having issues trying to pass both tests in ListExamplesTests, and whenever I run the tests file, I get the following output just by compiling and running the tests file with jUnit:
![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/e07e3d38-6d10-4f6e-8198-abab36527cbc)
> I understand that it's saying that it goes over the timeout limit for the tests, so either there's an infinite loop/time complexity issue/stack overflow error occurring, but could I have some help figuring out where this occurs? Thank you in advance.

#### 2. TA's Suggestion
> I suggest you first try using javac -g [compile info] and jdb -classpath [run info] in order to start debugging. Once you're running the debugger, try to ask it to stop at a line as such: stop at ListExamplesTests:29, and then entering run and then locals to check all the local variables. This should give you a good step in the right direction in figuring out what is causing your looping issue.


#### 3. Student's Response
> I edited my test.sh file and found the issue by doing this! None of the local variables were saved however, so seeing this led to me trying by searching for my own local variables by printing lines individually between the ListExamples.java methods for each value to track what happens, and I found that I was missing an else statement within a while loop in order to account for string1s that are greater than string2s rather than only the opposite. 
![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/76340ee8-1294-40be-8da3-0567a5b9c975)


#### 4. Overall Solution
**File & Directory Structure:**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/322268c1-508d-488f-a9a7-f9eb88a2e0c3)

**Pre-Fix Contents in test.sh:**
```
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" org.junit.runner.JUnitCore ListExamplesTests
```
**Pre-Fix Contents in ListExamples.java:**
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {
  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }

  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }
}
```
**Command Lines to Determine Bug Source:**
```
$ bash test.sh // RAN AFTER MODIFYING TEST.SH TO ACCOUNT FOR COMPILING/RUNNING JDB
> stop at TestListExamples:29
> run
> locals
```
**Fixes Made Within ListExamples.java:**
> An else statement was added to the if statement within the first while loop of the merge method in order to add the value at index2 and increment index2 when its string is lexicographically greater than the first string. Without this, the class will continue to have a non-empty list, which causes the timeout errors that we ran into in the first place. This is irrespective of the fact that the list ordering would be incorrect even if the timeout was not fixed.

---

### Part 2 : Reflection
Learning how to script in bash in general was something I had no clue how to work with. It initially seemed like something that is rudimentary and sluggish to do, but it turns out to be an incredibly useful tool for debugging complex programs, and also compiling information output from programs. It was pretty cool to learn it, and it was so engaging that I went an extra mile trying to parse, format, and output information in a clean way when we were scripting in it during week 6's lab. I feel pretty motivated to utilize it as a tool in my kit as both a student and a future developer.
