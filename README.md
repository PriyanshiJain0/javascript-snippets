# Javascript Snippets

Topic | No of Snippets
----- | --------------
Misc  | 5
Objects| 10
Arrays | 21
Strings | 0
Prototype | 0
Functions | 0

## Misc Snippets

### ***What will be the output of the following code?***

```js
const obj ={
 a:1,
 log1(){
     console.log(this.a);
 },
 log2: () =>{
     console.log(this.a);
 },
};

obj.log1();
obj.log2();
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
1 undefined
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
let a =10; 
function outer() {
    let b =10;
    console.log(a);
    return function(){
        a++;
        b++;
        console.log(b);
    };
}
outer()();
outer()();
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
10 11 11 11
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
let cond = true;
setTimeout(() => {
    cond =false;
}, 5000);

while(cond){
    console.log("hello");
}
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
Prints Hello Infiniltely.
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
Promise.resolve('Success!').then(()=>{
    throw Error('Oh noes!')
}).catch(error=>{
    return 'actually, that worked'
}).then(data=>{
    throw Error('The fails!')
}).catch(error=> console.log(error.message));
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
The Fails!
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
let nums =[1,3,4];
function add(a,b,...nums){
    const [ , , ...arr] = nums;
    console.log(arr);
    let sum = parseInt(a+b);
    arr.forEach(function(num){
        sum +=num;
    });
    return parseInt(sum);
}
console.log(add(1,2,...nums));
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
[4]
7
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
console.log(i);
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
ReferenceError: i is not defined.
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
const ev = '';
const usrName = ev || 'DEFAULT';
console.log(usrName);

const ev = '';
const usrName = ev || null;
console.log(usrName);

const ev = 'Max';
const usrName = ev || 'DEFAULT';
console.log(usrName);

```

<details><summary><b>Answer</b></summary>
<p>
	
```js
DEFAULT //empty string falsy value hence or operator moves on second operator and returns that value.
null // the 1st value is falsy and hence the 2nd value will be returned even if 2nd operand is falsy.
Max //ev = 'Max' is truthy value hence returns 1st value 
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
const ev = 'Max';
const usrName = ev && 'PRI';
console.log(usrName);

const ev = '';
const usrName = ev && 'DEFAULT';
console.log(usrName);

const ev = 'Max';
const usrName = ev && '';
console.log(usrName);

const usrName = 'Max';
console.log(!!usrName);
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
PRI // if first value is truthy, && operator always returns second value
'' // empty string because if 1st operand is falsy , it will always returns the first operator
'' // empty string
true // usrName = truthy !usrName === falsy !!usrName=== truthy.
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
console.log(4+'4');
console.log('hi' - 'i');
console.log(3*'3');
console.log(3-'3');
console.log(3/'3');

```

<details><summary><b>Answer</b></summary>
<p>
	
```js
44
NaN // only '+' supports string and numbers.
// Js is pretty smart and able to handle operations like these (3-'3')=> between no and string.
9
0
1

```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
console.log(i);
var i;
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
undefined.
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
const obj = {
  name: "some-object",
  getName1() {
    return this.name;
  },
  getName2: () => {
    return this.name;
  },
};

const res1 = obj.getName1();
const res2 = obj.getName2();
console.log(res1);
console.log(res2);
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
some-object
''
```
	
</p>
</details>


### ***What will be the output of the following code?***

```js
function f() {
  console.log(1);

  setTimeout(function () {
    console.log(2);
  }, 1000);

  setTimeout(function () {
    console.log(3);
  }, 0);

  Promise.resolve().then(() => console.log(5));
  console.log(4);
}

f();
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
1
4
5
3
2
```
	
</p>
</details>


### ***What will be the output of the following code?***

```js
for (let i = 0; i < 5; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
0
1
2
3
4
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
for (var i = 0; i < 5; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

<details><summary><b>Answer</b></summary>
<p>
	
```js
5
5
5
5
5
```
	
</p>
</details>

### ***What will be the output of the following code?***

```js
let a = 6;
function test() {
    console.log(a); 
    function again() {
        a = 8;
        console.log(a); 
    }
    let a = 9;
    again();
    console.log(a); 
}
test();
console.log(a);
```
<details><summary><b>Answer</b></summary>
<p>
Uncaught SyntaxError: Identifier 'a' has already been declared.
</p>
</details>

### ***What will be the output of the following code?***

```js
var a = 6;
function test() {
    console.log(a); 
    function again() {
        a = 8;
        console.log(a); 
    }
    let a = 9;
    again();
    console.log(a); 
}
test();
console.log(a);
```
<details><summary><b>Answer</b></summary>
<p>
Uncaught ReferenceError: Cannot access 'a' before initialization.
</p>
</details>

### ***What will be the output of the following code?***

```js
var a = 6;
function test() {
    console.log(a); 
    function again() {
        a = 8;
        console.log(a); 
    }
    var a = 9;
    again();
    console.log(a); 
}
test();
console.log(a);
```
<details><summary><b>Answer</b></summary>
<p>
undefined<br/>
8<br/>
8<br/>
6<br/>	
</p>
</details>

### ***What will be the output of the following code?***

```js
const fn = x => y => z => x + y + z;
fn(1)(2)(3);
```
<details><summary><b>Answer</b></summary>
<p>
6	
</p>
</details>


### ***What will be the output of the following code?***

```js
console.log(1+2+3);
console.log(1+2+'3');
console.log('1'+2+3);
console.log(1+'2'+3);
console.log('1+2'+3);
```
<details><summary><b>Answer</b></summary>
<p>
6<br/>
33<br/>
123<br/>
123<br/>
123<br/>
1+23<br/>	
</p>
</details>

### ***What will be the output of the following code?***

```js
function getDetails() {
	'use strict';
	
	console.log(this)
}

getDetails();
getDetails.call({name: 'Hamran'});
const newFn = getDetails.bind({name: 'Hamran'});
newFn();
```
<details><summary><b>Answer</b></summary>
<p>
undefined<br/>
{name: 'Hamran'}<br/>
{name: 'Hamran'}<br/>
</p>
</details>

### ***What will be the output of the following code?***

```js
let obj = {
	getDetails: function() {
	'use strict';
	
	console.log(this)
	},
	
	getMore: () => {
	'use strict';
	
	console.log(this)
	}
}
obj.getDetails();
obj.getMore();
obj.getMore.call(obj);
```
<details><summary><b>Answer</b></summary>
<p>
{getDetails: ƒ, getMore: ƒ}
Window {0: Window, window: Window, self: Window, document: document, name: '', location: Location, …}
Window {0: Window, window: Window, self: Window, document: document, name: '', location: Location, …}
</p>
</details>


### ***What will be the output of the following code?***

```js
function foo() {
  let a = b = 2;
  console.log('a: ', a);
  console.log('b: ', b);
}

foo();

console.log('outside b: ', b);
console.log('outside a: ', a);
```

<details><summary><b>Answer</b></summary>
<p>
a: 2<br />
b: 2<br />
outside b: 2    (We can access because let a = b = 2 will define b in window and a inside the function)<br />
a is not defined...
</p>
</details>


### ***What will be the output of the following code ?***

```javascript
var output = (function(x){
    delete x;
    return x;
})(0);

console.log(output);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output: 0</h4>
Here, the output of the following code will be 0. The delete operator works on the properties of an object. Here, it is deleting the parameter passed to the function which is not allowed. Hence, same value is returned from the function.
</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
var x = 1;
var output = (function() {
    delete x;
    return x;
})();

console.log(output);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output: 1</h4>
Here, the output of the following code will be 1. The delete operator works on the properties of an object. Here, it is deleting the variable which is not allowed. Hence, same value is returned from the function.
</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
let user = { name : 'harman'};
let output = (function() {
    delete user.name;
    return user.name; 
})();

console.log(output); 
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output: undefined</h4>
Here, the output of the following code will be undefined. The delete operator works on the properties of an object. Here, it is deleting the property of an object.
</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
let num = [2, 3, 4, 5, 6];
delete num[2];
console.log(num);
console.log("Length: ", num.length);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:<br /><br /><i>[2,3,empty,5,6]<br/>Length: 5</i></h4>
delete operator works differently in case of an array. It deletes the value and marks the index value as empty. It does not reindex the array. Hence the length of the array remains the same.</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
let emp1 = {
    name: 'Harman'
}

let emp2 = Object.create(emp1);
delete emp1.name;

console.log(emp2);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output: {}</h4>
<b>Object.create</b> will create a new object with the prototype of the original object. This does not create a new property for the new object. It just sets as the prototype of it and actually emp2.name will access through prototype of emp1 name. Hence, delete emp1.name will delete the property from emp1 object and emp2 can not access it.</p>
<p>Verify name is the property of emp1 object only:</p>

```javascript    
emp1.hasOwnProperty('name'); // true
emp2.hasOwnProperty('name'); // false
```

</details>


## Objects Snippets

### ***What will be the output of the following code ?***

```javascript
(function() {
    'use strict';
    var person = {
        name: 'John'
    };
    
    person.salary = '10000$';
    person['country'] = 'USA';
    
    Object.defineProperty(person, 'phoneNo', {
        value: '8888888888',
        enumerable: true
    });
    
    Object.defineProperty(person, 'password', {
        value: 'harmanleo786@gmail.com'
    });
    
    console.log(Object.keys(person));
})();
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output: ['name', 'salary', 'country', 'phoneNo']</h4></p>
<p><b>Object.keys</b> returns array of own object's enumerable properties names in the same order.</p><p><b>Object.defineProperty</b> method defines the new property directly in an object or modifies the existing property and returns the object. 
    <br/><br/><b>enumerable:</b> property to be enumerable/itetratable in case of Object.keys and for..in loop, default is false. Can be set to true.
    <br/><b>value:</b> initial value to be set to a property, default is undefined
    <br/><b>writable:</b> set true or false to inidicate the value of the property will be writable or not, default is false (read only)</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
(function() {
    const defaultObject = {
        foo: 'foo'
    }

    const objA = Object.create(defaultObject);
    const objB = Object.create(objA);
    
    objA.foo = 'Obj A test';

    console.log("Obj A: ", objA);
    console.log("Obj B: ", Object.keys(objB));
    console.log("Default: ", defaultObject)
})();
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>Obj A: { foo: 'Obj A test' }</p>
<p>Obj B: []</p>
<p>Default: { foo: 'foo' }</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
(function() {
    var person1 = {
        name: 'Shane'
    };

    var person2 = {
        name: 'Shane'
    };

    console.log(person1 == person2);
    console.log(person1 === person2);
}());
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
false
false
</details>

---

### ***What will be the output of the following code ?***

```javascript
(function () {
    const person1 = new Object({ name: 'Shane' });
    const person2 = new Object({ name: 'Shane' });
    
    console.log(person1 == person2);
    console.log(person1 === person2);
})();
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
false
false
</details>

---

### ***What will be the output of the following code ?***

```javascript
(function () {
    const person1 = Object.create({ name: 'Shane' });
    const person2 = Object.create(person1);
    
    console.log(person1 == person2);
    console.log(person1 === person2);
})();
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
false
false
</details>

---

### ***What will be the output of the following code ?***

```javascript
(function () {
    const person1 = Object.create({ name: 'Shane' });
    const person2 = Object.create(person1);
    
    console.log(person1.toString() == person2.toString());
    console.log(person1.toString() === person2.toString());
    console.log(person1.toString());
    console.log(person2.toString());
})();
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
true
true
'[object Object]'
'[object Object]'
</details>

---

### ***What will be the output of the following code ?***

```javascript
const person1 = {
  name: "Harman",
};
const person2 = person1;
console.log(person1 == person2);
console.log(person1 === person2);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
true
true
</details>

---

### ***What will be the output of the following code ?***

```javascript
const person1 = {
  name: "Harman",
};
const person3 = Object.create({ name: "Harman" });
const person2 = person3;
console.log(person1 == person2);
console.log(person1 === person2);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
false
false
</details>

---

### ***What will be the output of the following code ?***

```javascript
const person1 = {
    name: 'Harman'
}
const person2 = person1;
person2.name = 'Harry';
delete person2.name;

console.log("Person1: ", person1.name, "Person2: ", person2.name);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
undefined undefined
</details>

---

### ***What will be the output of the following code (Ask in interview) ?***

```javascript
const person1 = Object.create({ name: "Harman" });
const person2 = person1;
person2.name = 'Harry';
delete person2.name;

console.log("Person1: ", person1.name, "Person2: ", person2.name);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
Harman Harman
<p>Object.create will create an object in the prototype not the direct property of person1.</p>
</details>

---

## Arrays Snippets

### ***What will be the output of the following code ?***

```javascript
const array = new Array('50');
console.log(array);
console.log(array.length);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
['50'] 1
</details>

---

### ***What will be the output of the following code ?***

```javascript
const ar1 = [];
const ar2 = new Array(50);
const ar3 = new Array('10', 12, '14');
const ar3 = new Array(['1', 2, '3', 4, 5.5]);

console.log(ar1, ar2, ar3, ar4);
console.log(ar1.length, ar2.length, ar3.length, ar4.length);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>[]  [empty x 50]  ['10, 12, '14']  [0]['1', 2, '3', 4, 5.5]</p>
<p>0 50 3 1</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const ar1 = new Array('a', 'b', 'c', 'd', 'e', 'f');
ar1[10] = 'j';
console.log(ar1);
delete ar1[10];
console.log(ar1);
console.log(ar1.length);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>['a', 'b', 'c', 'd', 'e', 'f', empty, empty, empty, empty, 'f']</p>
<p>['a', 'b', 'c', 'd', 'e', 'f', empty, empty, empty, empty, empty]</p>
<p>11</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const ar1 = new Array(1, 2, 3, 4, 5);
console.log(ar1.indexOf(2));
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>1</p>
<p><b>indexOf</b> method searches for an item in an array and returns its position. It returns -1 if item is not found in the array. If the item is present for more than once then the index of the first occurance will be returned.</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const ar1 = [
    {
        name: 'Harman'
    },
    {
        name: 'Harman'
    }
];
console.log(ar1.indexOf({ name: 'Harman' }));
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>-1</p>
<p><b>indexOf</b> method searches for an item in an array and returns its position. It returns -1 if item is not found in the array.</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const ar1 = [[10], [12], [20], [12], [11]];
console.log(ar1.indexOf([12]));
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>-1</p>
<p>Here, it is looking at the reference of the array which will be false as [12] inside the indexOf will have new reference in the memory.</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const sampleStr = "abcdefgh";
console.log(sampleStr.indexOf('e'));
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>4</p>
<p>Here, sampleStr is a string and 'e' is present on the 4th index and same is returned</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const sampleStr = "Hey, This is Harman!";
console.log(sampleStr.indexOf('is'));
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>7</p>
<p>Here, sampleStr is a string and 'is' is present on the 7th index and same is returned</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const ar1 = [1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 6];

console.log(ar1.indexOf(2));
console.log(ar1.indexOf(2, 3));
console.log(ar1.indexOf(2, 10));
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>1</p>
<p>6</p>
<p>-1</p>
<p><b>indexOf(searchElement, startIndex)</b> this returns the element index from the starting of the array but start the search from the index mentioned in the function</p>
</details>

---

### ***Filter the array based on the even numbers.***

```javascript
const ar1 = [1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 6];

```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<b>const filteredAr = ar1.filter(item => item % 2 === 0);<br />
console.log('Even numbers: ', filteredAr);</b>
</details>

---

### ***Check if any one of the array element is divisible by 3***

```javascript
const ar1 = [1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 6];

```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<b>const someAreDivisible = ar1.some(item => item % 3 === 0);<br />
console.log('Some are Divisible by 3', someAreDivisible);</b>
</details>

---

### ***Filter only the users which are admin***

```javascript
const users = [
  { name: "Harman", isAdmin: false },
  { name: "Priyanshi", isAdmin: true },
  { name: "Nitin", isAdmin: true },
];
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<b>const filtered = users.filter(user => user.isAdmin === true);<br />
console.log('Filtered: ', filtered)</b>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const ar1 = [1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 6];

console.log(ar1.slice());
console.log(ar1.slice(5));
console.log(ar1.slice(2, 6));
console.log(ar1.slice(2, 2));
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>[1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 6]</p>
<p>[1, 2, 3, 4, 5, 6] - Picks from index 5 till end if no end index mentioned</p>
<p>[3, 4, 5, 1] - It does not take the end index value</p>
<p>[]</p>
<p><b>array.slice(startIndex, endIndex)</b> The <b>slice()</b> method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. The original array will not be modified.</p>
</details>

---

### ***What will be the output of the following code ?***

```javascript
const ar1 = [1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 6];

const deleted = ar1.splice();
const deleted = ar1.splice(2);
const deleted = ar1.splice(2, 0);
const deleted = ar1.splice(2, 0, 10);
const deleted = ar1.splice(2, 3, 15, 16, 17);
const deleted = ar1.splice(2, 1, [12, 13, 14]);
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
<p>[] - This will not delete any element<br />
[3, 4, 5, 1, 2, 3, 4, 5, 6] - Deleting the array elements from index 2 till the end of the array<br />
[] - Removes 0 elements from index 2<br />
[] - Remove 0 elements from index 2 and add 10 at index 2<br />
[3, 4, 5] - Removes 3 elements from index 2 and add 15, 16, 17 at index 2<br />
[3] - Removes 1 element from index 2 and add an array at the same index - Result - [1, 2, [12, 13, 14], 4, 5, 1, 2, 3, 4, 5, 6]<br />
<p>The splice() method changes the contents of an array by removing or replacing existing elements and/or adding new elements in an index of an array.</p>
<p>splice(start)<br />
splice(start, deleteCount)<br />
splice(start, deleteCount, item1)<br />
splice(start, deleteCount, item1, item2, itemN)<br /><p>
</details>

---

### Merge two arrays 

```javascript
const ar1 = [1, 2, 3];
const ar2 = [4, 5, 6];
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
const newAr = ar1.concat(ar2);<br />
concat merges arrays and returns new array.

Note: Using Spread Operator<br />
const newAr = [...ar1, ...ar2];
</details>

---

### Merge three arrays

```javascript
const ar1 = [1, 2, 3];
const ar2 = [4, 5, 6];
const ar3 = [7, 8, 9];
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
const newAr = ar1.concat(ar2, ar3);
</details>

---

### Find array index of a user with id USR007 from the array

```javascript
const users = [
  { id: 'USR001', name: 'John', isAdmin: false },
  { id: 'USR003', name: 'Jacob', isAdmin: true },
  { id: 'USR007', name: 'Shinda', isAdmin: true },
  { id: 'USR008', name: 'Dann', isAdmin: true }
];
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
const findIndex = users.findIndex(user => user.id === 'USR007');<br />
console.log("Index ", findIndex);

indexOf is used to get the index from the array of values whereas findIndex is used to get the index from the array of objects
</details>

---

### Check all the users are admin or not

```javascript
const users = [
  { id: 'USR001', name: 'John', isAdmin: false },
  { id: 'USR003', name: 'Jacob', isAdmin: true },
  { id: 'USR007', name: 'Shinda', isAdmin: true },
  { id: 'USR008', name: 'Dann', isAdmin: true }
];
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
const allAdmins = users.every(user => user.isAdmin === true);<br />
console.log("All Admins: ", allAdmins)

every: The every() method tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value.</details>

---

### Find a user with ID USR003

```javascript
const users = [
  { id: 'USR001', name: 'John', isAdmin: false },
  { id: 'USR003', name: 'Jacob', isAdmin: true },
  { id: 'USR007', name: 'Shinda', isAdmin: true },
  { id: 'USR008', name: 'Dann', isAdmin: true }
];
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
const userFind = users.find(user => user.id === 'USR003');<br />
console.log("User: ", userFind);

The find() method returns the value of the first element in the provided array that satisfies the provided testing function. If no values satisfy the testing function, undefined is returned.</details>

---

### Seprate the array elements with space and returns as a string

```javascript
const strArr = ['This', 'is', 'Harman', 'Kumar'];
//Expected: This is Harman Kumar
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
const output = strArr.join(' ');<br />
console.log("Str: ", output);

The join() method creates and returns a new string by concatenating all of the elements in an array, separated by commas or a specified separator string. If the array has only one item, then that item will be returned without using the separator.</details>

---

### Check some of the users are admin or not

```javascript
const users = [
  { id: 'USR001', name: 'John', isAdmin: false },
  { id: 'USR003', name: 'Jacob', isAdmin: true },
  { id: 'USR007', name: 'Shinda', isAdmin: true },
  { id: 'USR008', name: 'Dann', isAdmin: true }
];
```

<details><summary><b>Answer</b></summary>
<p>
<h4>Output:</h4></p>
const someAdmins = users.some(user => user.isAdmin === true);<br />
console.log("Some Admins: ", someAdmins)

The some() method tests whether some of the elements in the array pass the test implemented by the provided function. It returns a Boolean value.</details>

---



## Functions

### ***Which function is the callback function the following code ?***

```javascript
numbers.sort(function sortAsc(a,b){
return a-b;
});

```

<details><summary><b>Answer</b></summary>
<p>
sortAsync is a callback function because the JS engine calls it to compare rray items.
</p>
</details>

---

```javascript
function ninja(){}
ninja();

```

<details><summary><b>Answer</b></summary>
<p>

Not a callback function, ninja is called as stanard function.
</p>
</details>

---

```javascript
var myButton = document.getElementById("myButton");
myButton.addEventListner("click",function handleClick(){
alert("clicked");
});

```

<details><summary><b>Answer</b></summary>
<p>
handleClick is the callback function , called whenever the button is clicked.
</p>
</details>

---

### ***Identify function declaration function expression, arrow function in the following snipets ?***


```javascript
1. numbers.sort(function sortAsc(a,b){
return a-b;
});

2. numbers.sort((a,b) => b-a);

3. (function(){})();

4. function outer(){
function inner(){
}
return inner;
}

5. (function(){}());

6. (()=>"Yoshi")();
```

<details><summary><b>Answer</b></summary>
<p>
1. function expression as argument to another function
2. arrow function as argument to another function
3. function expression as the callee in a call expression
4. function declaration
5. function expression call wrapped in an expression
6. arrow function as a callee.
</p>
</details>

---

### ***what will be the values of samurai and ninja in the following snipets ?***

```javascript

var samurai =(() => "Tomoe")();

var ninja = (() =>{"Yoshi"})();

```

<details><summary><b>Answer</b></summary>
<p>
samurai : Tomoe
    
ninja :undefined
</p>
</details>


### ***what will be the values of a,b and c for functions call given?***

```javascript

function test(a,b,...c){}

test(1,2,3,4,5);
test();

```

<details><summary><b>Answer</b></summary>
<p>
1st call:  a=1,b=2,c=[3,4,5]
    
    
    
2nd call:  a=undefined,b=undefined,c=[].
</p>
</details>
 

### ***what will be the values message1,message2 variables?***

```javascript

function getNinjaWieldingWeapon(ninja, weapon ="katana"){
return ninja +" "+ weapon;
}

let message1 =  getNinjaWieldingWeapon("Yoshi");
let message2 =  getNinjaWieldingWeapon("Yoshi", "wakizashi");

```

<details><summary><b>Answer</b></summary>
<p>
message1 : Yoshi Katana   
    
message2 : yoshi wakizashi
</p>
</details>
 


### ***State Output of the following snipet and rewrite the sum function with help of rest parameter so that it doesnt use the argument object***

```javascript

function sum(){
let sum=0;
for(let i=0;i<arguments.length; i++){
sum +=arguments[i];
}
return sum;
}

sum(1,2,3);
sum(1,2,3,4);

```

<details><summary><b>Answer</b></summary>
<p>
output : 6 , 10 
    
```javascript
function sum(...rest){
let sum=0;
for(let i=0; i<rest.length; i++){
sum +=rest[i];
}
return sum;
}
```
    
</p>
</details>
 

### ***State the values of variables ninja and samurai***

```javascript

function getSamurai(samurai){
"use strict"
arguments[0]="Ishida";
return samurai;
}

function getNinja(ninja){
arguments[0]="Fuma";
return ninja;
}


var samurai = getSamurai("Toyotomi");
var ninja =getNinja("Yoshi");

```

<details><summary><b>Answer</b></summary>
<p>
    Toyotomi Fuma    
</p>
</details>


### ***State the output***

```javascript

function whoAmI1(){
"use strict"
return this;
}

function whoAmI2(){
return this;
}

whoAmI1();
whoAmI2();

```

<details><summary><b>Answer</b></summary>
<p>
    undefined window
</p>
</details>

### ***State the output***

```javascript

var ninja1 = {
whoAmI : function(){
return this;
}
};

var ninja2 = {
whoAmI : ninja1.whoAmI
}
};

var identify = ninja2.whoAMI;

ninja.whoAmI();
ninja2.whoAmI();
identify();
ninja1.whoAmI.call(ninja2);

```

<details><summary><b>Answer</b></summary>
<p>
  1. ninja1 : whoAMI will be called as a method of ninja1
   
  2. ninja2 : whoAMI will be called as a method of ninja2
    
  3. identify calls function as a function because we are in non-strict mode,this refers to the window
    
  4. ninja2 : using call to supply the function context this refers to ninja 2
</p>
</details>


 ### ***State the output***

```javascript

function Ninja() {
this.whoAmI = ()=> this;
};

var ninja1 = new Ninja();
var ninja2= {
whoAmI : ninja1.whoAmI
};

ninja1.whoAmI();
ninja2.whoAmI();

```

<details><summary><b>Answer</b></summary>
<p>
  ninja1 
    
  ninja1
</p>
</details>

### ***State the output***

```javascript

function Ninja() {
this.whoAmI = function(){
return this;
}.bind(this);
}
var ninja1 = new Ninja();
var ninja2= {
whoAmI : ninja1.whoAmI
};

ninja1.whoAmI();
ninja2.whoAmI();

```

<details><summary><b>Answer</b></summary>
<p>
  ninja1 
    
  ninja1
</p>
</details>

### ***chosse the correct statement from following***

```javascript
1. Closures allow functions to
    a) Access external variables that are in scope when the function is defined
    b) Access external variables that are in scope when the function is called
2.closures come with
    a) Code-size cost
    b) Memorycosts
    c) Processing costs

```

<details><summary><b>Answer</b></summary>
<p>
  1. a  
  2. b
</p>
</details>

### ***In the following code example,mark the identifiers accessed through closures***

```javascript
function Samurai(name){
    var weapon = "katana";
    
    this.getWeapon = function(){
    return weapon;
    }
   this.getName = function() {
   return name;
   }
   
    this.message = name + " wielding a " + weapon;
    this.getMessage =function() {
    return this.message;
}
}

var samurai = new Samurai("Hattori");

samurai.getWeapon();
samurai.getName();
samurai.getMessage();

```
<details><summary><b>Answer</b></summary>
<p>
    
 ```javascript    
 function Samurai(name){
    var weapon = "katana"; 
    this.getWeapon = function(){
    //accesses the local variable :weapon 
    return weapon;
    }
   this.getName = function() {
   //accesses the function parameter : name
   return name;
   }
    this.message = name + " wielding a " + weapon;
    this.getMessage =function() {
    //this.message is not accessed through a closure it is an object property (an not a variable)
    return this.message;
}
}   
```
</p>
</details>

### ***In the following code, how many execution contexts are created, and whats the largest size of the execution context stack?***

```javascript

function perform(ninja){
sneak(ninja);
infiltrate(ninja);
}

function sneak(ninja){
return ninja + " skulking";
}

function infiltrate(ninja){
return ninja+" infiltrating"
}

perform("Kuma");
```

<details><summary><b>Answer</b></summary>
<p>
 
    The largest stack size is 3, in the following situations:
    global code --> perform --> sneak
    global code --> perform --> infiltrate
    
</p>
</details>

### ***Which keyword in JavaScript allows us to define variables that cant be reassigned to a completely new value***


<details><summary><b>Answer</b></summary>
<p>
  const variables cant be reassigned to new values.
</p>
</details>


### ***Where and why the following code throw an exception***

```javascript
getNinja();
getSamurai();

function getNinja(){
return "Yoshi";
}

var getSamurai = () => "Hattori";
```


<details><summary><b>Answer</b></summary>
<p>
An exception will be thrown when trying to invoke the getSamurai function.
    
The getNinja function is defined with a function declaration and will be created before any of the code is executed; we can call it "before" its declaration has been reached 
in the code. The getSamurai function,on te other hand , is an arrow function thats created when the execution reaches it, so it will be undefined when we try to invoke it.
</p>
</details>


### ***Which of the following properties points to an object that will be searched if the target object doesn't have the searcched-for property ?***
a.class

b.instance

c.prototype

d.pointTo


<details><summary><b>Answer</b></summary>
<p>
  c.prototype
</p>
</details>

### ***What's the values of variable a1***

```javascript

function Ninja(){}
Ninja.prototype.talk=function(){
return "Hello";
};

const ninja = new Ninja();
const a1 = ninja.talk();

```

<details><summary><b>Answer</b></summary>
<p>
  Hello
</p>
</details>

### ***What's the values of variable a1***

```javascript

function Ninja(){}
Ninja.message = "Hello";

const ninja = new Ninja();
const a1 = ninja.talk();

```

<details><summary><b>Answer</b></summary>
<p>
  Undefined.
  The message property is defined in the constructor function Ninja, and isnt accessible through the ninja object.
</p>
</details>


### ***Explain the difference between the getFullName method in these two code fragments***

//First Fragment
```javascript

function person(firstName , lastName){
this.firstName = firstName;
this.lastName = lastName;

this.getFullName = function () {
return this.firstName + " " + this.lastName;
}
}
```
//Second Fragment
```javascript

function person(firstName , lastName){
this.firstName = firstName;
this.lastName = lastName;
}


Person.prototype.getFullName = function () {
return this.firstName + " " + this.lastName;
}
```

<details><summary><b>Answer</b></summary>
<p>
  In the first fragment,the getFullName method is defined directly on the instance created with the Person constructor. Each object created with the Person constructor gets its own getFullName method. In the second fragment,the getFulName method is defined on the prototype of the Person function . All instances created with the Person function will have access to the single method.
</p>
</details>

### ***What will ninja.constructor point to ?***

```javascript

function Person(){}
function Ninja(){}

const ninja = new Ninja();

```

<details><summary><b>Answer</b></summary>
<p>
  Ninja function
</p>
</details>

### ***What will ninja.constructor point to ?***

```javascript

function Person(){}
function Ninja(){}

Ninja.prototype = new Person();
const ninja = new Ninja();

```

<details><summary><b>Answer</b></summary>
<p>
  Person Constructor
</p>
</details>

### ***Explain how the instanceof operator works in following example?***

```javascript
function Warrior(){}
function Samurai(){}
Samurai.prototype = new Warrior();
var samurai = new Samurai();
samurai instanceof Warrior;
```

<details><summary><b>Answer</b></summary>
<p>
   returns true. Because the prototype of the function on the right , Warrior.prototype, can be found in the prototype hain of the object on the left.  
</p>
</details>


### ***Traslate the following ES6 code into ES5***

```javascript
class Warrior{
constructor(weapon) {
this.weapon=weapon; 

}
wield() {
return "Wielding " + this.weapon;
}
static duel(warrior1,warrior2) {

return warrior.weild() + " " + warrior2.wield();
}
}
```

<details><summary><b>Answer</b></summary>
<p>
  
```javascript
function Warrior(weapon){
    this.weapon = weapon;
}

Warrior.prototype.wield = function(){
    return "Wielding " + this.weapon;  
}
Warrior.duel = function(warrior1,warrior2){
return warrior1.weild() + " " + warrior2.wield();
}
```
  
</p>
</details>


### ***State the output of following snipet***

```javascript
console.log("Start Promise");
const promise = new Promise((resolve)=>{
    console.log("P_start");
    resolve("P_resolved");
    console.log("P_end");
}); 
console.log("then");
promise.then((data)=>{
    console.log(data);
})
console.log("end");
```

<details><summary><b>Answer</b></summary>
<p>
Start Promise
P_start
7 P_end
then
end
P_resolved
</p>
</details>

### ***State the output of following snipet***

```javascript
console.log("Start Promise");
const promise = new Promise((resolve)=>{

    setTimeout(()=>{
        console.log("P_start");
        resolve("P_resolved");
        console.log("P_end");
    },1000)
   
}); 
console.log("then");
promise.then((data)=>{
    console.log(data);
})
console.log("end");
```

<details><summary><b>Answer</b></summary>
<p>
Start Promise
then
end
(After 1000 mili second)
P_start
P_end
P_resolved
</p>
</details>

### ***State the output of following snipet***

```javascript
for(var i=0;i<5;i++){
    setTimeout(()=>{
        console.log(i)
    });
}
```

<details><summary><b>Answer</b></summary>
<p>
5(5 times).. Beacause scoping of var is functional level so it will take the latest value as 5 every time.
</p>
</details>

### ***State the output of following snipet***

```javascript
for(let i=0;i<5;i++){
    setTimeout(()=>{
        console.log(i)
    });
}
```

<details><summary><b>Answer</b></summary>
<p>
1 2 3 4 5 Beacause scoping of let is block level so it will get memory at every change.
</p>
</details>



### ***State the output of following snipet***

```javascript
console.log(1<2<3);
console.log(3>2>1);
```

<details><summary><b>Answer</b></summary>
<p>
true
false
</p>
</details>

### ***State the output of following snipet***

```javascript
console.log("Start");
setTimeout(function() {
    console.log("Inside setTimeOut");
}, 0);
async function set(){
    await fetch("https://api.github.com/users/octocat").then(function(){
    console.log("inside fetch")});
}
set();
console.log("End");
```

<details><summary><b>Answer</b></summary>
<p>
	
Start
	
End
	
Live reload enabled
	
Inside setTimeOut
	
inside fetch
	
</p>
</details>
