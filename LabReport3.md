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
