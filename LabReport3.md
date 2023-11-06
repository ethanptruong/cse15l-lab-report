# Bugs
## This is a failure inducing input.
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  
  @Test 
  public void testReverseInPlace_Failure() {
    int[] input1 = { 1, 2, 3, 4 };
    ArrayExamples.reverseInPlace(input1);
    // The expected result should be a reversed array
    assertArrayEquals("Array should be reversed in place", 
                      new int[]{ 4, 3, 2, 1 }, 
                      input1);
  }
}
```
## This test does not cause failure.
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test
  public void testReverseInPlace() {
    int[] input = { 3 };
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(new int[]{ 3 }, input);
  }
}
```

## This is the symptom of a test that does not induce failure
![Image](https://i.imgur.com/a/cqxeBji.png)
## This is the symptom of a test that does induce failure
![Image](https://i.imgur.com/a/sJKNE8M.png)
## This is the code with the bug
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
    }
}
```
## This is the code after the bug is fixed
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
        int temp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = temp;
    }
}
```
> Originally, the array would try to switch each element with its opposite index. However, when you reach
> halfway point, the elements you want to switch have already been overwritten with the first one, so you
> can't switch it back. I fixed the bug by storing the front elements in a temp variable. The method then
> switches the elements from the back to the front, and then the front to the back using the temp variable.
> This loop will only run for half the length of the list to switch the elements in the whole list.

## Example 1
```
ethan@DESKTOP-5AT37T5 MINGW64 /e/CS/Lab/UCSD/CSE15L/docsearch (main)
$ find ./technical -type d
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```
> I used [this](https://man7.org/linux/man-pages/man1/find.1.html) link to find ALL of the ```find```
> command options for this lab report. 

> I used the ```find``` command and a ```-type``` option to search for a file of a certain type. The
> ```-type d``` listed all of the directories within the ```./technical``` directory. It is useful
> if you want to do something that only considers directories.
```
ethan@DESKTOP-5AT37T5 MINGW64 /e/CS/Lab/UCSD/CSE15L/docsearch (main)
$ find ./technical -type f
./technical/biomed/1471-2334-2-26.txt
./technical/biomed/1471-2334-2-27.txt
./technical/biomed/1471-2334-2-29.txt
./technical/biomed/1471-2334-2-5.txt
```
> I used the ```-type f``` option to instead list all of the files in the ```./technical``` directory.
> I didn't add all of the output due to the sheer size, but the outputs given seem to encapsulate the
> overall gist of the command. This is useful if you want to do something to only files like editing

## Example 2
```
$ find ./technical -type f -empty

```
> I used the ```-type f -empty``` options to list all files in the ```./technical``` directory.
> This returns all empty files within the directory. This could be useful if you wanted to clean up
> files that are no longer in use or find empty files to write input in. Nothing was returned because
> none of the files were empty

```
ethan@DESKTOP-5AT37T5 MINGW64 /e/CS/Lab/UCSD/CSE15L/docsearch (main)
$ find ./technical -type d -empty

```
> I used the ```-type d -empty``` options to list all directories in the ```./technical``` directory.
> This returns all empty directories within the directory. This could be helpful if you wanted to clean
> up the ```./technical``` directory structure or clean up the directory as before. Nothing was returned
> because none of the directories are empty.

## Example 3
```
ethan@DESKTOP-5AT37T5 MINGW64 /e/CS/Lab/UCSD/CSE15L/docsearch (main)
$ find ./technical -type f -size -2k
./technical/plos/pmed.0020191.txt
./technical/plos/pmed.0020226.txt
```
> I used the ```-type f -size -2k``` options to list all files in the ```./technical``` directory using the
> ```-size``` option. This returns all files in the ```./technical``` directory that has a size of less
> than 2 kilobytes (only the two above do). This could be useful if you want to look for small,
> unimportant files.

```
ethan@DESKTOP-5AT37T5 MINGW64 /e/CS/Lab/UCSD/CSE15L/docsearch (main)
$ find ./technical -type d -size +1k

```
> I used the ```-type d -size +2k``` options to list all directories in the ```./technical``` directory using the
> ```-size``` option. The size option should cause the find command to return directories of size greater than 2
> kilobytes. However, no directories are returned, causing me to believe that this option only works with file types.
> This would probably not be useful since it tells you nothing about the sizes of the directories.

## Example 4
```
ethan@DESKTOP-5AT37T5 MINGW64 /e/CS/Lab/UCSD/CSE15L/docsearch (main)
$ find ./technical -type f -mtime 365

```
> I used the ```-type f -mtime 365``` options to list all files in the ```./technical``` directory using the
> ```-mtime``` option. This should cause all files who have been modified within the past year to be returned.
> The fact that no files were returned suggests that none of these files have been modified in the past year. This
> command could be useful if you want to look for recently edited files.
```
ethan@DESKTOP-5AT37T5 MINGW64 /e/CS/Lab/UCSD/CSE15L/docsearch (main)
$ find ./technical -type d -mtime 700

```
> I used the ```-type d -mtime 700``` options to list all directories in the ```./technical``` directory
> using the ```-mtime``` option. This should cause all the directories that have been modified in the last
> 700 days to be returned. The fact that no directories were returned suggests that none of the directories
> were edited in the past 700 days. This command could be useful if you want to find recently edited directories
