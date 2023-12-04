# Lab Report 5
## Buggy Code Help
> I've tried creating two private helper methods called ```filter``` and ```merge``` for PA1. But when I tested this code for correctness, two of my tests keep failing.
> In terms of symptoms, it seems that two tests are failing, ```testFilter``` and ```testMerge```. For ```testMerge```, it seems that the test timed out because
> it ran past 100 milliseconds to run. For ```testFilter```, we expected ```[apple, a]``` but got ```[a, apple]``` instead. For input-inducing failures, the ```testFilter```
>  method creates a list ```["a", "b", "apple"]``` and filters the list for the character ```a``` to create a failure-inducing input. My ```merge``` tries to merge the lists
> ```["a", "b", "cranberry"]``` and the list ```["dragon"]```. My guess at the bug is that because the ```merge``` method uses a ```while``` loop to merge lists, it is possible
> that for some reason the exit condition is never changed from ```true``` to ```false```. The ```testFilter``` uses the ```filter``` method to create a filtered list.
> Because the actual list is in reversed order of the expected list, a possible bug is that the list reverses the elements of the list for some reason.

## Response from TA:
> You mentioned that the elements are appearing in reverse order of the expected filtered list for the ```filter``` method. This is a great observation! Think about how
> your ```filter``` method chooses to add elements to your list. Reflecting on this might help you find the bug. The ```merge``` method times out as you mentioned. Look
> closely at your while loops in the ```merge``` method and pay close attention to how each while loop keeps track of their respective variables and checks their conditions.
> Hopefully this is helpful!

## Fixing the Bug
> I realized that the bug in my ```filter``` method was in how I added each of the filtered elements to the filtered list. I used ```result.add(0, s)``` which inserts each new
> element at the beginning of the list instead of at the end. This consequently results in a final list that has elements in reverse order compared to their original order in
> the input list. To fix this, I changed the method to ```result.add(s)```, so it should instead add each new element to the end of the result list.

> The bug in my ```merge``` method was causing an infinite loop during the merging of the two input lists. The bug was in the second while loop which added elements from the
> second list to the final list, to be specific. In this loop, ```index1``` was being incremented instead of ```index2```. Since ```index2``` was never incremented, and the loop
> checks for the condition ```index2 < list2.size()```, this condition never checked to false, leading to an infinite loop. To fix this, I changed line 41 from ```index1++```
>  to ```index2++```, so that the correct variable will be incremented and the condition will eventually check to true. These changes and their JUnit output are reflected
> in the screenshots below.

## Setup Information:
### File and Directory Structure:
```
- JAVA
  - Lab 5
    - lib
      - `hamcrest-core-1.3.jar`
      - `junit-4.13.2.jar`
    - `ListExample.java`
    - `ListExamples.class`
    - `StringChecker.class`
    - `test.sh`
    - `TestListExamples.class`
    - `TestListExamples.java`
```
### File Contents
#### ListExample.java 
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
                result.add(s);
            }
        }
        return result;
    }

    // Takes two sorted lists of strings (so "a" appears before "b" and so on),
    // and return a new list that has all the strings in both lists in sorted order.
    static List<String> merge(List<String> list1, List<String> list2) {
        List<String> result = new ArrayList<>();
        int index1 = 0, index2 = 0;
        while(index1 < list1.size() && index2 < list2.size()) {
            if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
                result.add(list1.get(index1));
                index1++;
            } else {
                result.add(list2.get(index2));
                index2++;
            }
        }
        while(index1 < list1.size()) {
            result.add(list1.get(index1));
            index1++;
        }
        while(index2 < list2.size()) {
            result.add(list2.get(index2));
            index2++;
        }
        return result;
    }
}
```
#### TestListExample.java
```
import java.util.ArrayList;
import java.util.List;
import java.util.Arrays;
import static org.junit.Assert.*;
import org.junit.*;

public class TestListExamples {

    @Test
    public void testFilter() {
        List<String> strs = new ArrayList<>();
        strs.add("a");
        strs.add("b");
        strs.add("apple");
        List<String> filtered = ListExamples.filter(strs, s -> s.charAt(0) == 'a');
        assertEquals(filtered, Arrays.asList("a", "apple"));
    }

    @Test(timeout=100)
    public void testMerge() {
        List<String> strs1 = new ArrayList<>();
        List<String> strs2 = new ArrayList<>();
        strs1.add("a"); strs1.add("b"); strs1.add("cranberry");
        strs2.add("dragon");
        List<String> merged = ListExamples.merge(strs1, strs2);
        assertEquals(merged, Arrays.asList("a", "b", "cranberry", "dragon"));
    }
}
```
#### Test.sh
```
set -e
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" org.junit.runner.JUnitCore TestListExamples
```
> I ran the command ```bash test.sh``` to run the bash script, which compiled the code and ran the tester file. This returned all of the failed/passed tests.

### Changes to Code
> In the ```filter``` method, I changed ```result.add(0, s)``` to ```result.add(s)``` to maintain the same order of elements.

> In the ```merge``` method, I corrected the incrementation within the second while loop from ```index1++``` to ```index2++``` to prevent an infinite while loop.

## Reflection
> I think  that one of the coolest things that I've learned in the later half of this quarter is the use of Vim for code editing. Initially, it took me a while to
> get used to using Vim because the controls were just so unintuitive to me. After learning a lot of commands to navigate and edit through code, I think Vim has
> become an invaluable tool and will be especially useful in future classes like CSE30, as I've heard from friends currently in the class about the need to edit
> using Vim. 
