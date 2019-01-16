# Test Coverage

each exercise in this readme comes with:
* a snippet of code to study
* an english description of it's behavior (inputs & outputs)
* a couple starter test cases
* an empty coverlog

for each snippet your task is to write:
* passing test cases that provide full _test coverage_ (more on this down below)
* the final coverlog readout for the snippet and your test cases 

### Index
* [learning objectives](#learning-objectives)
* [test coverage](#test-coverage)
* [testing framework](#testing-framework)
* [completed examples](./completed-examples.md)
* the exercises
    * [number 1](#1)
    * [number 2](#2)
    * [number 3](#3)
    * [number 4](#4)
    * [number 5](#5)
    * [challenge](#challenge)

---

## Learning Objectives

* representing code behavior with test cases
* tracing specific paths through code
* working in devtools console
* ...

[TOP](#test-coverage)

---

### Test Coverage

Writing passing test cases for existing code is not too hard, you can pretty much do it by trial and error. Writing good test cases is hard.  We will cover this in detail later on, but for now there is one important question to ask:
> Do my tests test all of the code?  
To help you understand your _test coverage_ each exercise snippet comes with a coverage log & a path log.  The 'coverlog' automatically tracks how many times each line of code is executed, the 'paths' log will track the lines of code each test case reaches in order.  Together these readouts have all the information (along with the source code!) to figure out what test cases are missing.



[TOP](#test-coverage)

---

## Testing "Framework"

So you can focus on writing test cases, we've provided the 'framework' below to log a helpful message for every one of your failing test cases.  This message will include the name of the failing case, the expected value and the actual value.  In this exercise if a test fails it's because the test is wrong, not because the code is broken.  Remember, you're describing what the code _does_ do, not what it _should_ do.

To complete the exercises paste this framework into the devtools console.  Then paste the snippet you want to study into the blank, and start filling in new test cases.  Hit enter after every new test case to check your work.  You can ignore everything besides the 'test\_cases' array and the console readout, that's the point of a framework.  It takes care of the routine work so you can focus on the task at hand.

After you've written all 10 cases, paste them into your fork of this README and move on to the next. 

```js
test_coverage_framework: {
  const coverlog = /* paste 'before' coverlog here*/; 
  const test_cases = /* paste in test cases */;
  const paths = [];
  for (let _case of test_cases) {
  
    let actual; const path = [_case.name]; { 
        // paste challenge snippet here
    };

    // framework magic happens down here
    paths.push(path);
    const expected = _case.expected;
    let pass;
    if (typeof expected === 'object') {
      const _actual = JSON.stringify(actual);
      const _expected = JSON.stringify(expected);
      pass = _actual === _expected;
    } else {
      pass = actual === expected;
    };
    if (!pass) {
      console.groupCollapsed(`%c ${_case.name}: \n`, 'color:red');
      console.log(`%c   actual: ${typeof actual},`, 'color:red', actual);
      console.log(`%c   expected: ${typeof expected},`, 'color:blue', expected);
      console.groupEnd();
    };
  };
  console.log('paths: ', paths);
  console.log('coverlog: ', coverlog);
};
```
[TOP](#test-coverage)

---

## Exercises

### 1

the snippet:
```js
const a = _case.args[0];
const b = _case.args[1];

if (a || b) {
   actual = a - b;         coverlog[1]++; path.push(1);
} else {
   actual = a + b;         coverlog[2]++; path.push(2);
};
if (actual === b) {
   actual = a;             coverlog[3]++; path.push(3);
};
```
coverlog:
```js
const before = {1:0, 2:0, 3:0};
const after = {1:0, 2:0, 3:0};
```
test cases:
```js
const test_cases = [

  ];
```
[TOP](#test-coverage)

---

we can use your studying to create the exercises











___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
