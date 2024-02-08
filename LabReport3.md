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
A failure-inducing input for a buggy program. 
