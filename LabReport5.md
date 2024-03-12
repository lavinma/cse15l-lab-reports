# Lab Report 5 - Putting It All Together (Week 9)

## Part 1 - Debugging Scenario
### Original post from student depicting symptom and their intepretation of the bug/failure-inducing input:
![Image](OrigPost.jpeg)
![Image](CompilingBash.jpeg)
"I am having issues with my implementation of the `reversed()` method. I am having issues when I run my `ArrayTests.java` file. My method `reversed()` is supposed to return a new array with the elements of the input array in reverse order. My test case (shown above) told me that the first element in my return array differs from my expected array. Originally I thought I returned the array with the elements in the original order, but my test case shows that the element at the first index is 0, which isn't even an element ever in my input array. I can see that the failure-inducing input is my test case named `testReversed2()`, but I am still unsure of what the bug may be. Also, the command line I ran that triggered this bug was `bash test.sh`. `test.sh` was the bash scipt I created that compiled and ran ArrayTests.java for me. (I attached a screenshot of the script file)"

### TA response:
"Have you tried fully printing out the returned array you get from calling `reversed()`? Perhaps that could help you with debugging and fixing your method implementation."

### Student response:
![Image](Post2.jpeg)
![Image](FixedStudentCode(LabReport5).png)
"I tried your suggestion and I have a good idea of what my bug is now! Thanks!! Since the output I am getting from the method call is an array with 0 as each of its four elements, I can see now that the bug is I am returning an array that is never initialized to anything (I attached a screenshot of how I implemented your suggestion). 
I took another look at my method implementation and noticed a few different bugs.
<br/>First, I am setting my input array to the reversed order of elements in the new array I initialized (the elements in the new array are all 0). Second, I am returning my input array instead of the new array I initialized. I will fix my bug in the code by setting each element in `newArray` to elements in `arr` (the input array) in reverse order and then return `newArray` at the end of my code. (I also attached a screenshot of my updated fixed code!)" 

<br/>
<br/>Directory structure is:
<br/>-> .vscode
<br/>------> settings.json
<br/>-> lib
<br/>------> junit-platform-console-standalone-1.10.2.jar
<br/>-> libs
<br/>------> hamcrest-2.2.jar
<br/>------> junit-4.13.2.jar
<br/>-> starter
<br/>------> ArrayExamples.java
<br/>------> ArrayTests.java
<br/>------> test.sh

<br/>Contents of each file before fixing the bug:
<br/>`ArrayExamples.java`: 
```
public class ArrayExamples{
  // Returns a *new* array with all the elements of the input
  // array in reversed order
  static int[] reversed (int [] arr){
    int[] newArray = new int[arr.length];
    for (int i = 0; i < arr.length; i += 1){
      arr[i] = newArray[arr.length- ¡ - 1];
    }
    return arr;
  }
}
```
`ArrayTests.java`:
```
import org.junit.Test;
import static org.junit.Assert.*;
public class ArrayTests{
  @Test
  public void testReversed1() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }

  @Test
  public void testReversed2() {
    int [] input = {6, 7, 8, 9};
    int [] output = ArrayExamples.reversed (input);
    assertArrayEquals (new int[] {9, 8, 7, 6}, output);
  }
}
```
`test.sh`:
```
javac *.java
javac -cp ../libs/junit-4.13.2.jar:../libs/hamcrest-2.2.jar:. ArrayTests.java
java -cp ../libs/junit-4.13.2.jar:../libs/hamcrest-2.2.jar:. org.junit.runner.JUnitCore ArrayTests
```
<br/>The command line that triggered the bug was: `bash test.sh`
<br/>This line triggered the bug because it executed the bash file that compiled and ran the `ArrayTests.java`. And, in that file was where the `reversed()` method was called and the bug was triggered.

<br/>What to edit to fix the bug:
<br/>The bug can be fixed by calling `newArray[i] = arr[arr.length - i - 1];` instead of `arr[i] = newArray[arr.length- ¡ - 1];`. The new line would successfully initialize each element in the `newArray` to the element in the input array in reverse order. Additionally, the student would need to return this `newArray` at the end of the method instead of returning the input array. So this line could be fixed by calling `return newArray;` as opposed to the current `return arr;`.

## Part 2 - Reflection
I learned a lot of new advice from one of my lab group mates. She was a junior and during one lab we talked about classes together and it was really cool hearing her experiences and her plans for the future. Because she was a few years ahead of me, she had new perspectives and advice I was able to use when picking new classes. 
<br/>Learning how to use `vim` was also another thing I really enjoyed and found engaging during lab. That might have been one of my favorite things we did during lab because I thought all the commands we used within `vim` were useful. While, it was a hassle to memorize and get used to the commands and how to edit text, once I got the hang of it, I enjoyed using the tool. I had no idea of such a tool before, so learning about this was fun because I will be able to actually use it in the future.
