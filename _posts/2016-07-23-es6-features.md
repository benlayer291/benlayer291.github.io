---
layout:     post
title:      ES6 exploration
summary:    Looking at some of the features of ES6
published: true
categories: code
---

ES6 or ECMAScript2015 is the latest release version of Javascript and comes with a number of new features. It seems kind of crazy that whilst still learning all of the many ins-and-outs of Javascript, along comes a lot more to get to grips with. Get-to-grips with it however we must, as the new features will help to improve code and, in theory, make apps work better.

I thought I would try and go through some of the new features of ES6 that I've had the chance to have a look at and play around with a bit recently. I was introduced to most of these whilst completing the Angular 1.5 and ES6 course on <https://thinkster.io>. It's really excellent and I'd highly reccomend it.

##### 'const' and 'let' keywords

To be used instead of the 'var' keyword, 'let' declares a local variable in the block scope and the 'const' keyword creates a read-only variable.

Looking at 'let', compare use inside an 'if' block:

``` 
var x = 1;

if (x < 10) {
  var v = 1;

  v = v + 21;
  v = v * 100;
  v = v / 8;

  console.log(v) // will log 275
}

console.log(v) // as var is globally scoped, it is 'hooked' to the top of the page so this also logs 275
```
This 'hooking' means the above code is essentially the same as writing:

```
var x = 1;
var v = 1;

if (x < 10) {

  v = v + 21;
  v = v * 100;
  v = v / 8;

  console.log(v) // will log 275
}

console.log(v) // will log 275
```

'let' behaves a bit differently, as it defines a local variable only accesible in the block within which it is declared (no leaking of variables!)

```
var x = 1;

if (x < 10) {
  let v = 1;

  v = v + 21;
  v = v * 100;
  v = v / 8;

  console.log(v) // will log 275
}

console.log(v) // as v is locally scoped within the if block, it is not accesible outside of it and hence will log 'undefined'
```

So what about the 'const' keyword? Well, once the variable is set using const, you can't change it. It is 'read-only', hence the name 'const' I guess...

```
const admin = 'Ben';

admin = 'Jack';

console.log(admin); // will log 'admin' as 'Ben' as const variable are read-only
```

It is worth noting however that properties inside objects declared using 'const' are not read-only and can be changed.

```
const admin = {name: 'Ben'};

admin.name = 'Jack';

console.log(admin.name); //will log 'admin.name' as 'Jack' as properties of objects are not protected
```

##### Template strings

The age old problem in Javascript is when you want to concatentate a variable within a string and you up writing things like this:

``` 
'My name is ' + 'person.name' + ' and i am ' + 'person.age' + ' years old' 
```

It's a pretty trivial example, but one can see how things could quite easily get a little bit out of hand.

Template strings mean that you can interpolate the value of a variable into a string, note the use of a back-tick, `, to indicate a template string.

``` 
`My name is ${person.name} and i am ${person.age} years old`

`${this._AppConstants.api}/users${route}`
```

##### Classes

Classes were one of the big things we were introduced to in Ruby when I was studying at General Assembly. Javascript classes behaviour similiarly but this not to say that Javascript suddenly works with classical instead of prototypical inheritance.

```
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.listName = function listName() {
  console.log(this.name);
};

Person.prototype.listAge = function listAge() {
  console.log(this.age);
};
```

compared to use of 'Class'

```
class Person {

  constructor(name, age)

  this.name     = name;
  this.age      = age;

  listName() {
    console.log(this.name);
  }

  listAge() {
    console.log(this.age);
  }
}
```

##### Default values

Does exactly what it says on the tin, can apply a default value as an arguement of a function.

```
class Person {

  constructor(name, age = 25)

  this.name     = name;
  this.age      = age;

  listName() {
    console.log(this.name);
  }

  listAge() {
    console.log(this.age);
  }
}

var person = new Person('Ben');
console.log(person.age); // logs default value of 25

var person2 = new Person('Jack', 27);
console.log(person2.age); // overrides default value and logs value of 27
```

##### Arrow functions

These look a bit weird at first but the useful thing about them is that they preserve 'this'.

Things to note: 

- 'return' keywork is not required, will automatically return expression on the last line
- If on a single line then '{}' are not required, in fact even '()' are not required


```
class Person {
  constructor(name, age, button) {
    this.name = name;
    this.age  = age;

    button.onclick = function(event) {
      listAge(this.email); // here this is the button (as that has invoked the function and therefore owns it), so this.email is undefined
    }
  }
}
```

compared with:

```
class Person {
  constructor(name, age, button) {
    this.name = name;
    this.age  = age;

    button.onclick = (event) => {
      listAge(this.age); // here this is bound using the arrow function to be the Class so this.age is defined
    }
  }
}
```

##### Other features

There are obviously lots of other features in ES6 including:

- Destructuring
- Rest and Spread

to name but a few, let alone all of the async stuff.

I need to have a look at these a bit more and actually use them in my code before I write about them on here. So, as ever, lots still to do!

A good place to play around with ES6 features is the Babel repl: <https://babeljs.io/repl/>







