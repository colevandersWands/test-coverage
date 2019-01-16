# Completed Examples

* [variable swap](#variable-swap)
* [conditionals](#conditionals)
* [conditional in a loop](#conditional-in-a-loop)
* [_super_ interesting inspect](#conditional-inside-loop-inside-conditional)

---

### variable swap

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
test cases:
```js
const test_cases = [
      {name:'1, 2, 3', args:[1,2,3], expected: 2},
      {name:'3, 2, 1', args:[3,2,1], expected: 2},
    ];
```
coverlog:
```js
const before = {1:0, 2:0, 3:0};
const after = {1:2, 2:2, 3:2};
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
coverlog:
```js
const before = {1:0, 2:0, 3:0, 4:0, 5:0, 6:0};
const after = {1:2, 2:2, 3:2, 4:2, 5:6, 6:6};
```
your notes:

[TOP](#completed-examples)

---



### conditional in a loop

the snippet:
```js
let a = _case.args[0];                        
let b = _case.args[1];   
let c = _case.args[2];   


```
test cases:
```js
const test_cases = [

   ];
```
coverlog:
```js
const before = {1:0, 2:0, 3:0, 4:0, 5:0, 6:0};
const after = {1:2, 2:2, 3:2, 4:2, 5:6, 6:6};
```
your notes:

[TOP](#completed-examples)

---


### conditional inside loop inside conditional

This code swaps variable values between a & b using a temporary holder.

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
coverlog:
```js
const before = {1:0, 2:0, 3:0, 4:0};
const after = {1:14, 2:10, 3:6, 4:1};
```
your notes:

[TOP](#completed-examples)

---


___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
