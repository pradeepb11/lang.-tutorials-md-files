console.log('Working');

```
//Q  What is an out put ?
const number = [11, 25, 31, 33, 18, 200];
number.sort();
console.log(number);
// ANs: [11,18,200,25,31,33]
```

console.log('=***********************Question********************************=');
//Q  What is out put ?
var of = ['of'];
for (var of of of) {
    console.log(of);
}
// ANs: ['of']

console.log('=***********************Question********************************=');
// eg for of
const off = ['a', 'b', 'c'];
for (var element of off) {
    console.log(element)
}
// ANs: ['a', 'b', 'c']

console.log('=***********************Question********************************=');
//Q what is out put?
console.log('first line');
['a', 'b', 'c'].forEach((element) => {
    console.log(element)
});
console.log('Third line');
// ANs: first line a b c Third line

console.log('=***********************Question********************************=');
//Q What is out put
let quickPromise = Promise.resolve();
quickPromise.then(() => console.log('Promise Finished'))
console.log('Program Finished');
//ANs: Program Finished Promise Finished

//Q What is out put 

//comment  bcoz console TypeError Uncomment and check What is ANS
// getMessage();
// var getMessage = () => {
//     console.log('Good Morning');
// }
// close comment 

//ANs: getMessage is not a function


console.log('=***********************Question********************************=');
// Q What is out put 
let arr = [1, 2, 3];
let str = '1,2,3';
console.log(arr == str);
// ANs: true

console.log('=***********************Question********************************=');
// Q What is out put
console.log(true && 'hi');
console.log(true && 'hi' && 1);
console.log(true && ' ' && 0);
// ANs: true hi 1 0

console.log('=***********************Question Count********************************=');
// Q What is out put
let count = 10;
(function innerfunction() {
    if (count === 10) {
        let count = 11;
        console.log(count)
    }
    console.log(count)
})();
// Ans 11 10 
//The innerFunc is a closure which captures the count variable from the outerscope. i.e, 10. But the conditional has another local variable count which overwrites the ourter count variable. So the first console.log displays value 11. Whereas the second console.log logs 10 by capturing the count variable from outerscope.

console.log('=***********************Question********************************=');

//Q What is the output of below code in non strict mode?
"use strict";
let msg = 'Good Morning';
msg.name = 'John';
console.log(msg.name);
// And Undefined
//It returns undefined for non-strict mode and returns Error for strict mode. In non-strict mode, the wrapper object is going to be created and get the mentioned property. But the object get disappeared after accessing the property in next line.


console.log('=***********************Question********************************=');
// Q What is output 
let zero = new Number(0);
// console.log(zero)
if (zero) {
    console.log('IF')
} else {
    console.log('else')
}
// Ans If
// /The type of operator on new Number always returns object. i.e, typeof new Number(0) --> object.
// /Objects are always truthy in if block
