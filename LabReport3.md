# Lab Report 3 - Bugs and Commands (Week 5)

## Part 1 - Bugs
I will address this buggy method:
```
// Changes the input array to be in reversed order
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
A failure-inducing input for the `reverseInPlace()` method:
```
@Test
public void testReverseInPlace2() {
  int[] input = {1, 2, 3};
  ArrayExamples.reverseInPlace(input);
  assertArrayEquals(new int[] {3, 2, 1}, input);
}
```
An input that does not induce a failure for the `reverseInPlace()` method:
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```
The symptom (the output of running the tests above):
![Image](symptomVisible.jpeg)
![Image](symptomNotVis.jpeg)
<br/>The failure-inducing test can be seen above (first image) and the input that does not induce a visible failure is one of the 3 tests that passed (second image) out of a total of 4 tests.
<br/>Before the code was changed to fix the bug:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
After the code was changed to fix the bug:
```
static void reverseInPlace(int[] arr) {
  int[] arrCopy = new int[arr.length];
  for (int i = 0; i < arr.length; i++) {
    arrCopy[i] = arr[i];
  }
  for (int i = 0; i < arr.length; i+=1) {
    arr[i] = arrCopy[arr.length - i - 1];
  }
}
```
Previously, only the first half of the array was being successfully reversed and the second half of the array remained the same. This was because the for loop didn't take into account the array being updated (reversed) while the for loop ran. This code change fixes the issue of the array not being reversed properly because when the original array is being reversed now, it doesn't modify itself as it refers to its copy for the correct elements.

## Part 2 - Researching Commands
I will find 4 new ways to use the `find` command
1. `find /path/to/search -type <file_type>` command:
```
lavin@Lavins-MacBook-Air docsearch % find . -type d
.
./lib
./.git
./.git/objects
./.git/objects/pack
./.git/objects/info
./.git/info
./.git/logs
./.git/logs/refs
./.git/logs/refs/heads
./.git/logs/refs/remotes
./.git/logs/refs/remotes/origin
./.git/hooks
./.git/refs
./.git/refs/heads
./.git/refs/tags
./.git/refs/remotes
./.git/refs/remotes/origin
./technical
./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
./technical/government/Media
./technical/plos
./technical/biomed
./technical/911report
```
```
lavin@Lavins-MacBook-Air docsearch % find . -type s
lavin@Lavins-MacBook-Air docsearch % 
```
This command is useful because  it searches through the given path for files of a given type. This allows for a new way to specifically search for files of different types including character special, directories, simple files, and more. I can also see if there isn't files of a specific type (shown in the second example where no files paths are printed).
<br/>I found this command through the `man find` command line in the terminal. 
<br/>2. `find /path/to/search -empty` command:
```
lavin@Lavins-MacBook-Air docsearch % find . -empty               
./.git/objects/info
./.git/refs/tags
./grep-results.txt
```
```
lavin@Lavins-MacBook-Air docsearch % find technical  -empty
lavin@Lavins-MacBook-Air docsearch %
```
This command is useful because I can find in a short amount of time the files that are empty. The command shows me the exact paths to all empty files in the given path I want to search. And, when there are no empty files, nothing is printed (as shown in the second example). 
<br/>I found this command through the `man find` command line in the terminal.
<br/>3. `find /path/to/directory -depth +num -print` command:
```
lavin@Lavins-MacBook-Air docsearch %   find technical/911report -depth +0 -print 
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-1.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/preface.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
```
```
lavin@Lavins-MacBook-Air docsearch %   find technical/911report -depth -1 -print
technical/911report
```
This command is useful because it searches through the given directory but only prints all the files and directories to the specified depth. The `-depth +num` part is how deep into the given directory files and directories are searched for. This allows for a new way of finding and printing files/directories and can be useful in scenarios where you don't need to search fully into subdirectories.
<br/>I found this command through the `man find` command line in the terminal. 
<br/>4. `find /path/to/directory \! -name "whatFileDoesNotEndIn" -print` command:
 ```
lavin@Lavins-MacBook-Air docsearch % find technical/911report \! -name "*.c" -print 
technical/911report
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-1.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/preface.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
```
```
lavin@Lavins-MacBook-Air docsearch % find technical/government/Alcohol_Problems \! -name "*.c" -print   
technical/government/Alcohol_Problems
technical/government/Alcohol_Problems/Session2-PDF.txt
technical/government/Alcohol_Problems/Session3-PDF.txt
technical/government/Alcohol_Problems/DraftRecom-PDF.txt
technical/government/Alcohol_Problems/Session4-PDF.txt
```
This command is useful because it prints out a list of all the files in the given path that does not end in what given in quotes. It's a nice new way to use the `find` command because you are able to now able to search for files that aren't something instead of being limited to only searching for files that contain a specific string.
<br/>I found this command through the `man find` command line in the terminal. 
