# Lab 3 Bugs and Commands
## Part 1: Bugs
### Code:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
Here I chose the method "reversed" where it's supposed to reverse an array given any length of an array. For example, an array of {1,2,3} is supposed to return {3,2,1}.
### Faliure Inducing Input:
```
@Test
  public void testReversed() {
    int[] input1 = {1,2,3};
    assertArrayEquals(new int[]{3,2,1}, ArrayExamples.reversed(input1));
  }
```
Here, the failure inducing input is really any value other than an input array of all zeroes, but I chose {1,2,3} as my failure inducing input.
### Input that does not induce a failure:
```
@Test
  public void testReversed() {
    int[] input1 = {0,0,0};
    assertArrayEquals(new int[]{0,0,0}, ArrayExamples.reversed(input1));
  }
```
The code is broken so that only an empty array would work, so this input of {0,0,0} actually runs successfully and does not induce a failure.
### Symptom
![Symptom](images/symptoms-lab3.png)
Here is what happens when I try to run the test. There is one failure and one pass, where the failure is when I input the {1,2,3} array.
### Before and After
Before:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

After:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

