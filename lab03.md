# Lab Report 3 - Bugs and Commands

Nov. 5, 2023

In this lab report, we will take a closer look at one of the bugs from Week 4's lab and examine its behavior under certain circumstances and its fixes. Additionally, I will also research additional options for the `less` command. 

---

## 1️⃣ Bugs

<!--Choose the bug from week 4-->
**The Buggy File and Method:** `ArrayExamples.java`, specifically the `averageWithoutLowest()` method.

Since there are many ways to interpret the behavior from `averageWithoutLowest()`, I should specifically define my standards so that we have a clearer understanding of what exactly constitutes a failed or successful test. After all, we can't decide what behavior is wrong if we haven't decided what's right.

For the purpose of the following tests, we will say that `averageWithoutLowest()` 
is succesful if the following conditions are met:
- When the array has 2 or more elements: The method will calculate the average of the values without the smallest number. <ins>However, if the smallest number appears more than once, only one instance of it will be removed.</ins>
- When the array has 0 or 1 elements: The method will return 0.

<br>

---
### The Inputs
<!--Failure inducing input (JUnit test and code block)-->
**Failure Inducing Inputs:**
- `{4,4,5,8}`
- `{7,7,7}`

```java
JUNIT TESTS
———————————

@Test
public void test_fail_dup() {
    double[] input = {4, 4, 5, 8};
    double expected = (double)17/3;
    assertEquals(expected, ArrayExamples.averageWithoutLowest(input), 0.0001);
}

@Test
public void test_fail_same() {
    double[] input = {7,7,7};
    double expected = (double)(7 + 7)/2;
    assertEquals(expected, ArrayExamples.averageWithoutLowest(input), 0.0001);
}
```

<br>

<!--Non-failure input (JUnit and code block)-->
**Non-Failure inducing inputs:**
- `{9}`
- `{ }`
- `{1.1,2,3,4}`

```java
JUNIT TESTS
———————————

@Test
public void test_nonfail_single() {
  double[] input = {9};
  double expected = 0;
  assertEquals(expected, ArrayExamples.averageWithoutLowest(input), 0.0001);
}

@Test
public void test_nonfail_empty() {
  double[] input = { };
  double expected = 0;
  assertEquals(expected, ArrayExamples.averageWithoutLowest(input), 0.0001);
}

@Test
public void test_nonfail3_unique() {
  double[] input = {1.1,2,3,4};
  double expected = (double)(2 + 3 + 4)/3;
  assertEquals(expected, ArrayExamples.averageWithoutLowest(input), 0.001);
}
```

---
### The Outputs

<!--output of both tests-->
The tests that failed were `test_fail_dup()` and `test_fail_same()`.

<br>

<div align="center">
  <img src="img/lab03_junit_output.png" size="500px"/>
</div>

---
### Fixing the Code
<!--The bug before/after fix, explain why the fix works-->

Looking at the tests that failed, a recurring pattern is that `averageWithoutLowest()` has trouble handling inputs where the lowest number appears more than once.

Specifically, in the test `test_fail_dup()` (input: `{4,4,5,8}`), what we expected was `5.667` as the result of `(4+5+8)/3`. But what the computer did was calculate `(5+8)/3` which resulted in the erroneous value of `4.333`.

In the case of `test_fail_same()` (input: `{7,7,7}`), we expect a returned value of `7` from the calculation `(7 + 7)/2`. However, what happened was that the method saw that `7` was the smallest value and therefore kept each instance of a `7` out of the calculations altogether. Thus, the wrong result returned was `0`.

Also, `averageWithoutLowest()` succeeded in the case where all numbers were unique such as in `test_nonfail3_unique()` (input: `{1.1,2,3,4}`). So it must be the repeating low numbers that are causing problems.

<br>

**Before Fixes:**
```java
static double averageWithoutLowest(double[] arr) {
  // 0 or 1 elements; works as expected
  if(arr.length < 2) { return 0.0; }

  // 2 or more elements; currently buggy
  double lowest = arr[0];
  for(double num: arr) {
    // Compares through array and finds lowest number
    if(num < lowest) { lowest = num; }
  }

  double sum = 0;
  for(double num: arr) {
    // I suspect the problem is here
    if(num != lowest) { sum += num; }
  }
  // and also here
  return sum / (arr.length - 1);
}
```

<br>

**After Fixes:**
```java
static double averageWithoutLowest(double[] arr) {
  // 0 or 1 elements; works as expected
  if(arr.length < 2) { return 0.0; }

  // 2 or more elements; fixed
  double lowest = arr[0];
  for(double num: arr) {
    // Compares through array and finds lowest number
    if(num < lowest) { lowest = num; }
  }

  // Fix: just add everything together
  // and get rid of the lowest number once at the end
  // when returning
  double sum = 0;
  for(double num: arr) {
    sum += num;
  }
  return (sum - lowest) / (arr.length - 1);
}
```

<br>

The reason why this fix works is because I removed the part of the code that checked if the current number in `arr` was equal to the lowest number. 

`if(num != lowest) { sum += num; }` is a problem because if you have multiple instances of the lowest number, it doesn't just remove one of them from the sum, it removes ALL of them. Which, as we said earlier was not the desired outcome.

So, in order to remove the lowest number just once, I replaced the numerator in the return statement to be `(sum - lowest)`. Thus preserving all of the other lowest numbers if they happend to show up more than once.


Now, all the tests pass!
<div align="center">
  <img src="img/lab03_junit_passes.png" size="450px"/>
</div>

## 2️⃣ Researching Commands

<!--Researching `less`-->
In this section, I will examine more uses or options for the `less` command. 

One interesting thing I noticed about `less` is that we can add options even as we view the file. We don't have to add all the options all at once in the command line. 

<!-- 4 options or alternate uses 2 ex. each, cite source for each-->

---

### --mouse: scroll with the mouse
For the `--mouse` option, it allows us to view the file and scroll through the lines as if we were scrolling through a page. This can be useful if we don't like using the spacebar or the arrow keys.

Since it is a bit impossible to demonstrate the output of this command option in a code block, I hope that a video I've recorded can replace it.

<br>

**Input**
```shell
COMMAND
———————

katri@dark-chocolate MINGW64 ~/OneDrive/Documents/GitHub/lab5/docsearch (main)
$ less --mouse technical/government/Alcohol_Problems/Session2-PDF.txt
```

<br>

**Output**

A video of me scrolling through the file reader with the mouse. Visually, it is almost like moving through the viewer with the arrow keys.
