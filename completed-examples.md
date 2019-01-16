# Completed Examples

* [no control flow](#no-control-flow)
* [conditionals](#conditionals)
* [unreachable conditions](#unreachable-conditions)
* [paths help understand behavior](#conditional-inside-loop-inside-conditional)
* efficient vs. inefficient coverage
    * [simple example](#efficient-coverage-simple-behavior)
    * [complex example](#efficient-coverage-complex-behavior)

---

### no control flow

the snippet:
```js
let a = _case.args[0];                        
let b = _case.args[1];                        
let temp = _case.args[2];              

temp = b;               coverlog[1]++; path.push(1);
b = a;                  coverlog[2]++; path.push(2);
a = temp;               coverlog[3]++; path.push(3);       

actual = temp;
```
coverlog:
```js
const before = {1:0, 2:0, 3:0};
const after = {1:2, 2:2, 3:2};
```
test cases:
```js
const test_cases = [
      {name:'1, 2, 3', args:[1,2,3], expected: 2},
      {name:'3, 2, 1', args:[3,2,1], expected: 2},
    ];
```
your notes:

[TOP](#completed-examples)

---


### conditionals

the snippet:
```js
let a = _case.args[0];                        
let b = _case.args[1];   
let c = _case.args[2];   

if (a && b) {
  actual = 1;                   coverlog[1]++;  path.push(1);
} else if(a && !b) {
  actual = 2;                   coverlog[2]++;  path.push(2);
} else if(!a && b) {
  actual = 3;                   coverlog[3]++;  path.push(3);
} else if(!a && !b) {
  actual = 4;                   coverlog[4]++;  path.push(4);    
};
if (a || c) {
  actual = actual + '' + 5;     coverlog[5]++;  path.push(5);
};
if (b || c) {
  actual = actual + '' + 6;     coverlog[6]++;  path.push(6);
};
```
coverlog:
```js
const before = {1:0, 2:0, 3:0, 4:0, 5:0, 6:0};
const after = {1:2, 2:2, 3:2, 4:2, 5:6, 6:6};
```
test cases:
```js
const test_cases = [
      {name:'tr, tr, tr', args:[true,true,true], expected:'156'},
      {name:'tr, fa, tr', args:[true,false,true], expected:'256'},
      {name:'fa, tr, tr', args:[false,true,true], expected:'356'},
      {name:'fa, fa, tr', args:[false,false,true], expected:'456'},
      {name:'tr, tr, fa', args:[true,true,false], expected:'156'},
      {name:'tr, ra, fa', args:[true,false,false], expected:'25'},
      {name:'fa, tr, fa', args:[false,true,false], expected:'36'},
      {name:'fa, fa, fa', args:[false,false,false], expected:4},
   ];
```
your notes:

[TOP](#completed-examples)

---


### unreachable conditions

sometimes there are lines of code that can never happen, no matter what.  this is most likely with conditionals but can also happen with loops.  
keep an eye out for this and try to remove any lines of code that will never happen to keep things clear and simple to read.

the snippet:
```js
let a = _case.args[0];    

actual = 0;										coverlog[1]++; path.push(1);
if (a) {
	if (a) {
		actual += 1;							coverlog[2]++; path.push(2);
	} else {
		actual = 'impossible!';   coverlog[3]++; path.push(3);
	};
else {
	if (a) {
		actual = 'impossible!;    coverlog[4]++; path.push(4);
	} else {
		actual += 4;							coverlog[5]++; path.push(5);
	};
};
```
coverlog:
```js
const before = {1:0, 2:0, 3:0, 4:0, 5:0};
const after = {1:2, 2:1, 3:0, 4:0, 5:1};
```
test cases:
```js
const test_cases = [
      {name:'tr', args:[true], expected: 1},
      {name:'fa', args:[false], expected: 4},
   ];
```
your notes:

[TOP](#completed-examples)

---



### conditional inside loop inside conditional

inspecting the path logs for this snippet is a very effective way to build an understanding of it's behavior.  

the snippet:
```js
let a = _case.args[0];                        
let b = _case.args[1];   
let c = _case.args[2];   

if ( (a < b) || (b < c) ) {
  while (a !== b && b !== c) {
    if ( (b - a) > (c - b) ) {
      a++;                        coverlog[1]++; path.push(1);
    } else {
      c--;                        coverlog[2]++; path.push(2);
    };
  };
  actual = [a,b,c];               coverlog[3]++; path.push(3);
} else {
  actual = 'infinite loop';       coverlog[4]++; path.push(4);
};
```
coverlog:
```js
const before = {1:0, 2:0, 3:0, 4:0};
const after = {1:14, 2:10, 3:6, 4:1};
```
test cases:
```js
const test_cases = [
      {name:'1, 2, 3', args:[1,2,3], expected:[1,2,2]},
      {name:'1, 2, 4', args:[1,2,4], expected:[1,2,2]},
      {name:'1, 3, 4', args:[1,3,4], expected:[2,3,3]},
      {name:'1, 4, 4', args:[1,4,4], expected:[1,4,4]},     
      {name:'1, 8, 4', args:[1,8,4], expected:[8,8,4]},   
      {name:'10, 8, 4', args:[10,8,4], expected:'infinite loop'},
      {name:'1, 8, 14', args:[1,8,14], expected:[7,8,8]},   
   ];
```
your notes:

[TOP](#completed-examples)

---


### efficient coverage (simple behavior)

Any good set of test cases will hit every line of testable code, but some test cases get the job done more evenly & efficiently than others.  The efficient cases below cover every line as equally as possible with only 3 cases. The inefficient cases still cover all lines of code but hit some far more than others, and have way more tests than necessary.

Complete & efficient code coverage aren't the only important things to consider when writing tests, but they are some of the easiest concepts in testing to grasp.  Later in this course we will cover other important, but trickier, questions to ask about test quality.


the snippet:
```js
let a = _case.args[0];                        
let b = _case.args[1];    

if (a && b) {
	actual = 1;						coverlog[1]++; path.push(1);
} else {
	actual = 2;						coverlog[2]++; path.push(2);
};
```
coverlog:
```js
const before = {1:0, 2:0};
const efficient = {1:1, 2:1};
const inefficient = {1:1, 2:3};
```
efficient code coverage:
```js
const test_cases = [
      {name:'tr, tr', args:[true,true], expected:1},
      {name:'tr, fa', args:[true,false], expected:2},
   ];
```
inefficient code coverage:
```js
const test_cases = [
      {name:'tr, tr', args:[true,true], expected:1},
      {name:'tr, fa', args:[true,false], expected:2},
      {name:'fa, tr', args:[false,true], expected:2},
      {name:'fa, fa', args:[false,false], expected:2},   
   ];
```
your notes:

[TOP](#completed-examples)

---

### efficient coverage (complex behavior)

the snippet:
```js
let numbers = _case.args[0];   

const betweens = [];
for (let i = 1; i < numbers.length - 1; i+=2) {
  if (numbers[i-1] <= numbers[i]) {
    if (numbers[i] <= numbers[i+1]) {
      betweens.push(true);                    coverlog[1]++; path.push(1);
    } else {
      betweens.push(false);                   coverlog[2]++; path.push(2);
    };
  } else {
    betweens.push(false);                     coverlog[3]++; path.push(3);
  };
};
actual = true;                                coverlog[4]++; path.push(4);
checkem: for (let between of betweens) {
  if (!between) {
    actual = !actual;                         coverlog[5]++; path.push(5);
    break checkem;    
  };
};
```
coverlog:
```js
const before = {1:0, 2:0, 3:0, 4:0, 5:0};
const efficient = {1:1, 2:1, 3:1, 4:3, 5:2};
const inefficient = {1:14, 2:4, 3:1, 4:10, 5:4};
```
efficient code coverage:
```js
const test_cases = [
		{name:'3,2,1', args:[[3,2,1]], expected:false},
		{name:'1,4,3', args:[[1,4,3]], expected:false},
		{name:'1,2,3', args:[[1,2,3]], expected:true},
  ];
```
inefficient code coverage:
```js
const test_cases = [
		{name:'3,2,1', args:[[3,2,1]], expected:false},
		{name:'1, 2, 3', args:[[1,2,3]], expected:true},
		{name:'1, 3, 3', args:[[1,3,3]], expected:true},
		{name:'1, 4, 3', args:[[1,4,3]], expected:false},
		{name:'1,2,3,4,5', args:[[1,2,3,4,5]], expected:true},
		{name:'1,3,3,5,5', args:[[1,3,3,5,5]], expected:true},
		{name:'1,4,3,4,5', args:[[1,4,3,4,5]], expected:false},
		{name:'1,2,3,4,5,6,7', args:[[1,2,3,4,5,6,7]], expected:true},
		{name:'1,3,3,5,5,9,9', args:[[1,3,3,5,5,9,9]], expected:true},
		{name:'1,4,3,4,5,10,9', args:[[1,4,3,4,5,10,9]], expected:false},
	];
```
your notes:

[TOP](#completed-examples)

---

___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
