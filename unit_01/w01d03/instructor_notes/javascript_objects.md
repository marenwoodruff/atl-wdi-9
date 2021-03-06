---
title: JavaScript Objects
type: lesson
duration: 1hr
creator:
  name: Alex Chin, Gerry Mathe, Sean Shannon
  adapted for WDI ATL 9 by: Maren Woodruff
  city: London, DC
competencies: Programming
---

# JavaScript Objects

### Objectives
*After this lesson, students will be able to:*

- Compare objects and key-value stores to arrays as data structures
- Explain the difference between object properties and methods
- Create empty objects and objects with multiple properties and methods using object literal syntax
- Compare adding and retrieving properties to an existing object using the dot and bracket notations
- Access properties of an object using keys and helper methods (.hasOwnProperty)
- Iterate over the keys of an object to return and manipulate values

### Preparation
*Before this lesson, students should already be able to:*

- Create and manipulate variables with JavaScript
- Create and manipulate arrays in JavaScript
Objects in JavaScript


## Intro

### What is an object? (5m)

I was going to intro this lesson by discussing Ariel's Secret Grotto of human objects, but decided just to continue on the them that began in the last lesson...  In the last lesson, I had you think of 5 objects that define you.  You added these items to an array and were able to iterate over them/console.log them.  But there wasn't any detail given about the items, we just stated their names.  Objects can help us out with that.

* Objects are a type of data structure that is nearly universal across programming languages, although they may have different names in different languages (in Python they are called a dictionary, in Ruby they're called a hash).
* In JavaScript, an object is a type of key-value store, or a way to group many pairs of keys and values together
* Like arrays, objects can hold multiple pieces of data of varying types; but unlike arrays, objects use named keys rather than ordered indices to access those pieces of data.

For example, a puppy has properties, a breed/type, the color of his/her fur, a size, a demeanor etc. Following the same logic, a JavaScript object will have **keys/names** and **values** for each property.

<br />

### Collections of name-value pairs

#### Object literal syntax

Strings are in 'quotes', arrays are in ['square braces'], objects follow the same lexical pattern but use `{curlyBraces: 'and are structured as key/value pairs'}`, the `key` is before the colon and the `value` is after the colon.

Like arrays, these key-value pairs are comma separated!

```javascript
var myObject = {};
```

## Object Properties

Objects in JavaScript **always** have properties associated with them.

You can think of a property on a JavaScript object as a type of variable that contains a value. The properties of an object can be accessed using "dot notation":

```javascript
var person = {
  name: "Danny"
}

person.name;
=> "Danny"
```

You can define or change a property by assigning it a value using `=` as you would a normal variable.

```javascript
var person = {
  name: "Danny"
}

person.name;
=> "Danny"

person.name = "John";
person.name;
=> "John"
```

## Create an object with properties

We are going to create an object `classroom` that contains the properties `name` and `campus`:

```javascript
var classroom = {};
=> undefined

classroom.name = "WDI ATL 9";
=> "WDI ATL 9"

classroom.campus = "Atlanta!";
=> "Atlanta!"

classroom
=> Object {name: "WDI ATL 9", campus: "Atlanta!"}
```

### Bracket notation

There is another way to set properties on a JavaScript object.

```javascript
classroom["name"]   = "WDI ATL 9";
classroom["campus"] = "Atlanta!";
```

This syntax can also be used to read properties of an object:

```javascript
console.log(classroom["name"]);
=> "WDI ATL 9";

classroom.property = "Ponce City Market";

console.log(classroom["property"]);
=> "Ponce City Market";
```

- You can use dot notation or bracket notation to set or change your properties.

For more details see [MDN's Documentation on Property Accessors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Property_Accessors).


### Deleting properties

If you want to delete a property in an object (and by extension, the value attached to the property), you need to use the [`delete`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete) operator:

The following code shows how to remove a property:

```javascript
var classroom = {name: "WDI ATL 9", campus: "Atlanta!", start: "02/21/2017"};
delete classroom.start;

classroom
=> {name: "WDI ATL 9", campus: "Atlanta!"}
```

## Object methods

As we have stated before, the value of a property can be anything in JavaScript, which means that we can also attach functions to objects properties. When a function is attached to a property, this function becomes a `method`. Methods are defined the exact same way as a function, except that they have to be defined as the property of an object.

We will be discussing functions in more detail tomorrow.  

```javascript
var classroom = {
  name: "WDI ATL 9", // key: value,
  campus: "Atlanta!", // key: value,
  start: "02/21/2017",
  instructors: ['Danny', 'Maren', 'Josh', 'John', 'Lisa'],
  sayHello: function() {
    console.log("Hello");
  }
};
```

**EXERCISE**: How do we ask for values in an object? How do we call functions?

To call the method, we add a pair of parentheses at the end, in order to execute it:

```javascript
classroom.sayHello();
=> Hello
```

### Assigning a previously-defined function

We can attach regular functions to objects as methods, even after they are created.

```javascript
var sayHello = function() { console.log("Hello"); }

classroom.sayHello = sayHello;  

classroom.sayHello()
=> Hello
```

##`this` for object references

In JavaScript, `this` is a keyword that refers to the current object. When used in a method on an object, it will always refer to the current object.

```javascript
var classroom = {
  name: "WDI ATL 9", // key: value,
  campus: "Atlanta!", // key: value,
  start: "02/21/2017",
  instructors: ['Danny', 'Maren', 'Josh', 'John', 'Lisa'],
  sayHello: function() {
    console.log("Hello");
  },
  sayHelloToOne: function(instructorIndex) {
    console.log('Hi, ' + this.instructors[instructorIndex]);

    console.log(`Hi, ${this.instructors[instructorIndex]}`);
  },
  classInfo: function(){
    console.log("This is " + this.name + " and the class starts on " + this.start);
  }
};
```

<br />

### Enumerating properties of an object

There are three native ways to list the properties of an object we're just going to explore the `for ... in` loop:

* **for...in loops** This method traverses all enumerable properties of an object and its prototype chain
* **Object.keys(o)**  This method returns an array with all of the enumerable property's names/the keys of the object o.
* **Object.getOwnPropertyNames(o)** This method returns an array containing all of the enumberable property's names/the keys of the object o.

**Loop over an object's properties**

You can use the bracket notation with for...in to iterate over all the enumerable properties of an object.

** If you are still confused by the difference between `==` and `===` review MDN's notes on [equality](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators#Equality_()) and [strict equality](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators#Identity_strict_equality_())**

<br />

## Independent Monkey Exercise (15m)

- Create a `monkey` object, which has the following properties:

  - `name`
  - `species`
  - `foodsEaten`

  And the following methods:

  - `eatSomething(monkeyFood)`
  - `introduce`: produces a string introducing itself, including its name, species, and what it has eaten

- Create 3 monkeys. Make sure all 3 monkeys have all of the properties set and the methods defined.

- Exercise your monkeys by retrieving their properties and using their methods. Practice using dot notation and bracket notation for retrieving these properties.

## Conclusion (5m)

We will continue to use JavaScript objects every day, and you will have plenty of time to practice creating and using objects in JavaScript. There are a lot of resources available on the web for you to dive deeper, but the most detailed and understandable one is probably on MDN- Mozilla Developer Network.

- [JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
- [Intro to Object-Orientated Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)
- [Objects in Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
