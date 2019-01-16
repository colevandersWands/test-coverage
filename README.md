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
* [code behavior](#code-behavior)
* [test coverage](#test-coverage)
* [testing framework](#testing-framework)
* [completed examples](./completed-examples.md)
* the exercises
    * [number 1](#1)
    * [number 2](#2)
    * [number 3](#3)
    * [number 4](#4)
    * [number 5](#5)
    * [number 6](#6)
    * [challenge](#challenge)

---

## Learning Objectives

* representing code behavior with test cases
* tracing specific paths through code
* working in devtools console
* ...

[TOP](#test-coverage)

---

## Code Behavior

A snippet's behavior is what has changed in your program _after_ the snippet has run, implementation is the lines of code that make this change happen.  In the last exercises on tracing, logging & asserting you were exposed to this difference.  The 'expected' variable described the snippet's _behavior_, while the logs and asserts helped to understand the snippet's _implementation_. This exercise will take you deeper into understanding behavior.

Practically speaking you can think of behavior as inputs and outputs.   What values did variables have before a snippet, and what values do they have after the snippet?  To use vocabulary, what are the __arguments__ and what is the __expected__ output:
```js
const test_cases = [
    {name:'meaningful name', args:['the inputs', 'for this snippet'], expected: 'what it should output'},
    {name:'another test case', args:['different', 'inputs'], expected: 'the expected output'},
    ...
  ];
```

[TOP](#test-coverage)

---

### Test Coverage

Writing passing test cases for existing code is not too hard, you can pretty much do it by trial and error. Writing good test cases is hard.  We will cover this in detail later on, but for now there is one important question to ask:
> Do my tests test all of the code?
To help you with _code coverage_ each exercise snippet comes with a coverage log.  It will automatically keep track of how many times each line of code is executed.  You will use this readout to make sure your test cases are complete.

This will be done using an object called 'coverlog'.  Each exercise comes with an 


[TOP](#test-coverage)

---

## Testing "Framework"

So you can focus on writing test cases, we've provided the 'framework' below to log a helpful message for every one of your failing test cases.  This message will include the name of the failing case, the expected value and the actual value.  In this exercise if a test fails it's because the test is wrong, not because the code is broken.  Remember, you're describing what the code _does_ do, not what it _should_ do.

To complete the exercises paste this framework into the devtools console.  Then paste the snippet you want to study into the blank, and start filling in new test cases.  Hit enter after every new test case to check your work.  You can ignore everything besides the 'test\_cases' array and the console readout, that's the point of a framework.  It takes care of the routine work so you can focus on the task at hand.

After you've written all 10 cases, paste them into your fork of this README and move on to the next. 

```js
{
  const test_cases = /* paste in test cases */;
  const paths = [];
  const coverlog = /* paste coverlog here*/; 
  for (let _case of test_cases) {
  
    let actual; const path = [_case.name]; { 
        // paste challenge snippet here
    };   paths.push(path);

    // framework magic happens down here
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

### Exercises















