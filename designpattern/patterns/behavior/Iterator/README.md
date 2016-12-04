迭代器模式
===
在不暴露对象内部结构的同时，可以顺序的访问聚合对象内部的元素

### 需了解的内容
1. for-of
1. ... 展开符
1. iterator

for-of和for-in之间的差别
````js
var list = [3, 5, 7];
list.foo = 'bar';

for (var key in list) {
  console.log(key);
}

for (var value of list) {
  console.log(value);
}
````
...展开运算符
````js
//ES5
function myFunction(x, y, z) { }
var args = [0, 1, 2];
myFunction.apply(null, args);
//ES6
function myFunction(x, y, z) { }
var args = [0, 1, 2];
myFunction(...args);
//选择性参数
function filter(type, ...items) {
    return items.filter(item => typeof item === type);
}
filter('boolean', true, 0, false);        
filter('number', false, 4, 'Welcome', 7);
````
***
iterator
````js
function* list(value) {
  for (var item of value) {
    yield item;
  }
}

for (var value of list([1, 2, 3])) {
  console.log(value);
}

var iterator = list([1, 2, 3]);

console.log(typeof iterator.next); // function
console.log(typeof iterator[Symbol.iterator]); // function

console.log(iterator.next().value); // 1

for (var value of iterator) {
  console.log(value); // 2, 3
}
````
String，Array，TypedArray，Map和Set都是内置迭代器
***
````js
var string = "hello";

for (var chr of string) {
  console.log(chr);
}
````
***
解构赋值
````js
var hello = 'world';
var [a, b, ...c] = [...hello];
console.log(a, b, c);
````
***
````js
function co(generator) {
    function next() {
        var part = generator.next("");
        if (!part.done) {
            part.value(next);
        } else {
            console.log("完成");
        }
    }
    next();
}
function a() {
    setTimeout(function () {
        console.log(1);
    }, 1000);
}
function b(next) {
    setTimeout(function () {
        console.log(2);
        next();
        // return "b";
    }, 2000);

}
function c(next) {
    setTimeout(function () {
        console.log(3);
        next();
    }, 3000);
}
function* get() {
    var result1 = yield c;
    var result2 = yield b;
    var result3 = yield a;
}

co(get());
````
