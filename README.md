# Test Cases

A code's behavior is what has changed _after_ it the code runs, implementation is the lines of code that make this change happen.  In the last exercises on tracing, logging & asserting you saw this difference.  The 'expected' variable described the snippet's _behavior_, while the logs and asserts helped to understand the snippet's _implementation_. This exercise will take you deeper into understanding and documenting code behavior.

Practically speaking you can think of this in terms of inputs and outputs.   What values did variables have at the top of a snippet, and what values do they have after the snippet?  To use vocabulary, what are the __arguments__ and what is the __expected__ output:
```js
const test_cases = [
    {name:'meaningful name', args:['the inputs', 'for this snippet'], expected: 'what it should output'},
    {name:'another test case', args:['different', 'inputs'], expected: 'the expected output'},
    ...
  ];
```

each exercise on this readme comes with:
* a snippet of code to study
* an english description of it's behavior (inputs & outputs)

Your task is to write ~10 passing test cases for each snippet, all together they should have complete _code coverage_ (more on that further down).  


---


## Testing "Framework"

So you can focus on writing test cases, we've provided the 'framework' below to log a helpful message for every one of your failing test cases.  This message will include the name of the failing case, the expected value and the actual value.  In this exercise if a test fails it's because the test is wrong, not because the code is broken.  Remember, you're describing what the code _does_ do, not what it _should_ do.

To complete the exercises paste this framework into the devtools console.  Then paste the snippet you want to study into the blank, and start filling in new test cases.  Hit enter after every new test case to check your work.  You can ignore everything besides the 'test\_cases' array and the console readout, that's the point of a framework.  It takes care of the routine work so you can focus on the task at hand.

After you've written all 10 cases, paste them into your fork of this README and move on to the next. 

```js
{
  const test_cases = [
      {name: '', args: [], expected: null},
      {name: '', args: [], expected: null},
    ];
  let coverage;
  for (let _case of test_cases) {
  
    { // paste exercise snippet here
    
    };

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
  console.log('coverage: ', coverage);
};
```

---

### Tips for writing tests

Writing passing test cases is not too hard, you can do it by trial and error using the framework above. Writing good test cases is hard.  We will cover this in detail later on, but for now we will focus on one question only:
> Do my tests test all of the code?
To help you with _code coverage_ each exercise snippet comes with a coverage log.  It will automatically keep track of how many times each line of code is executed.  You can use this readout to make sure your test cases are complete.

---

### Exercises

__1.__  
the snippet:
```js
coverage = {1:0,2:0,3:0};

let a = _case.args[0];                        
let b = _case.args[1];                        
let temp = _case.args[2];              

temp = b;               coverage[1]++;
b = a;                  coverage[2]++;
a = temp;               coverage[3]++;        

const actual = temp;
```
your test cases:
```js
```
the  coverage log:
```js
// have this section?
```
your notes:

---













