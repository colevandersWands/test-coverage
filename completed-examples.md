# Completed Examples

* [variable swap](#variable-swap)
* [if, else if, else](#if-else-if-else)
* [variable swap](#variable-swap)

---

### variable swap

This code swaps variable values between a & b using a temporary holder.

the snippet:
```js
let a = _case.args[0];                        
let b = _case.args[1];                        
let temp = _case.args[2];              

temp = b;               coverlog[1]++;
b = a;                  coverlog[2]++;
a = temp;               coverlog[3]++;        

actual = temp;
```
test cases:
```js
const test_cases = [
      {name:'path: 1-2-3', args:[1,2,3], expected: 2},
      {name:'path: 1-2-3', args:[3,2,1], expected: 2},
    ];
```
coverlog:
```js
const coverlog = {1:1, 2:1, 3:1};
```
your notes:

---


### if, else if, else

This code swaps variable values between a & b using a temporary holder.

the snippet:
```js
let a = _case.args[0];                        
let b = _case.args[1];   
let c = _case.args[2];   

if (a && b) {
  actual = 1;                   coverlog[1]++;
} else if(a && !b) {
  actual = 2;                   coverlog[2]++;
} else if(!a && b) {
  actual = 3;                   coverlog[3]++;
} else if(!a && !b) {
  actual = 4;                   coverlog[4]++;    
};
if (a || c) {
  actual = actual + '' + 5;     coverlog[5]++;
};
if (b || c) {
  actual = actual + '' + 6;     coverlog[6]++;
};
```
test cases:
```js
const test_cases = [
      {name:'path: 1-5-6', args:[true,true,true], expected:'156'},
      {name:'path: 2-5-6', args:[true,false,true], expected:'256'},
      {name:'path: 3-5-6', args:[false,true,true], expected:'356'},
      {name:'path: 4-5-6', args:[false,false,true], expected:'456'},
      {name:'path: 1-5-6', args:[true,true,false], expected:'156'},
      {name:'path: 2-5', args:[true,false,false], expected:'25'},
      {name:'path: 3-6', args:[false,true,false], expected:'36'},
      {name:'path: 4', args:[false,false,false], expected:4},
   ];
```
coverlog:
```js
const coverlog = {1:2, 2:2, 3:2, 4:2, 5:6, 6:6};
```
your notes:

---


___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
