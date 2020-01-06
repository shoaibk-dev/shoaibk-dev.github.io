---
layout: post
title: Random notes on Javascript
---

In JavaScript, accessing an index that does not exist in the array returns undefined.

In JavaScript, it is possible to set elements using an index that is outside the bounds of the array, and the element will then be added to the array. 
Here, it is added to the end because the array already has 4 elements, so index #4 would come after the last element.
In JavaScript we can access an object’s properties using the “dot” notation or by using the “array” notation with the property name passed as a string.

In JavaScript, the triple-equals operator compares values as well as types, whereas double-equals only compares values. 
If  a===b  returns true, a and b must have the same value, so  a==b  will return true.

JavaScript allows all variable types to be evaluated in the conditions of if-statements. Any non-empty string is considered truthy, which will then evaluate to true.

The forEach function does not return anything or modify the array; it simply applies the function to each element.

Prototype functions are invoked using the keyword new and return objects.

We can use the DOM to get an HTML element using the getElementById function and the id of the element.

The localStorage variable is an object that maintains the same value for different pages. It cannot, however, be used to access any data on the local computer.

A callback function is one that you as the programmer implement but do not invoke; rather, the underlying system (in this case, the browser) invokes it after some event or action.

The outer loop applies the event listener to each element in the “one” class. The inner loop is what is executed when that event occurs, and it changes all elements of the “two” class to red.

To access a class in jQuery, use the “dot” notation as you would in CSS.
Using jQuery, the html function allows us to modify an HTML element’s contents.

jQuery "ON" function.
Specify an object that defines callback functions for different actions/events for a given element or elements.
The argument to the “on” function is an object in which the properties are the names of the different events, and their corresponding values are the corresponding callback functions.

What HTML elements are selected with the jQuery command 
```
$("select[name='id']")
```

This notation allows us to select HTML elements but also specify their attributes; here, we’re selecting <select> elements but also specifying that we want the ones with the “name” attribute set to the value “id”.

In jQuery, the selector $(this) refers to

Depending on the selector, we may choose many elements in a page, and any specified callback function will be applied to each element that is selected. In order to access each individual element in the callback function, we use $(this) within the function.

**A way to work with an array**  
forEach() - iterate over an array  
map() -  transform elements in an array  
filter() - select a subset of multiple elements from an array  
find() - select a single element from an array  
reduce() - derive a single value from multiple elements in an array  
every() - drive a boolean value from multiple elements in an array  

**Functions**  
Functions are first class objects  
All functions are object but not all objects are function.  
What distinguish function from other objects is that function can be called.  
In brief they function objects.  

```> Anonymous function can't be invoke unless its part of a callback function parameter.  ```

IIFE can be used in scenarios where you need to run the function only once, like fetching some initial data, setting some configuration values, checking system status on startup etc.  

**Object and function: call, apply and bind**  
Every function has access to three methods: call, apply and bind  
 - call: method to invoke a method on another object  
   ```ex: console.log(user.sendingMessage.call(student, "Hello from shoaib"));  ```
 - apply: argument are passes as an array  
 - bind: return new method with the new context  
   ```ex: 
       let sendMessageToStudent = user.sendingMessage.bind(student);
       console.log(sendMessageToStudent("yet another message"));```

**Constructor function: simulate OOP in javascript**  
start with an uppercase letter by convention.  
invoke by the new keyword  
it's not recommended to define method due to performance perspective in construct function  
we can add method to function on 'thiis' but not recommended for scenario where we create lot of objects  
for one instance or singlton cases this work fine  
with in the constructor function, this points to the current instance  

> functions inside the constructor function or on the prototype is called as methods

**Javascript MDN:**  
Array Object: ordered set of values(refer with name & index)  
Array object has methods to manipulate arrays (sorting, reversing, joining etc)  
It has property for determinig length - array.length, and other (ex: regular expression)  
Array.of static method to create arrays with single element.  
**push() -** add one or more element to the end of an array and return length of an array.  
**pop() -** remove the last element from an array and return that element  
**shift() -** remove first element and return that element  
**unshift() -** add one or more element to the front of an array and return the length  
**slice() -** extract the section of an array and return new array  
**splice() -**  remove element from an array and optionally replace them. It return the items which were removed  
**reverse() -** 
 -- transpose the element of an array  
 -- first array element becomes the last and last becomes the first.  
 -- return the reference to the array  
**sort() -** sort element of an array in place and return reference to the array  

**Typed Array: new feature in js**  
Provide an easy way to work with binary data and structure  
 - Canvas image data is typed array  
 - WebScokets: support transfering binary data and ArrayBuffer  

**keyed collection**  
4 type of collection: Set, Map, WeakSet & WeakMap  

**Set**:  
collection of values either primitive or object reference  
values must be unique  
added using the add() method  
size property returns the number of values in the set.  
iterated over in the order in which they are inserted  
iterate over them using forEach() / set.prototype  

**Map**:  
data is stored as key value pair that can be added using the set method.  
key and value can be of any type, primitive or object  
size property return number of key-value pairs in the map  
like sets, key are iterated over in the order in which they were inserted  

**WeakSet**:  
value can only be object reference  
Key in a weakmap can only be object reference  
value in weakset & key in a weakmap : are weakly held object reference  
meaning: reference is the only reference to that object, the object can be garbage collected(value in a weakset, key-value pair in a weakmap) will be removed from the collection  
cannot be iterated over - weakset & weakmap are weakly held object reference  
clear method is not available  

**Object**  
3 ways to list/traverse object properties:  
 - for in loop: traverse all enumerable properties of an obj and its prototype chain  
 - Object.keys(o): return an array with all the OWN[not in the prototype chain] enumerable prop names  
 - Object.getOwnPropertyNames(o): return an array containing all prop name of an object  

**Create Object::**  
Object Initializer[obj literals notation] & Constructor Function & object.create() method:  
this: to assign value to the object properties based on the value passed to the function  

> object can have prop that is iteself another object  
> object.create() allow you to choose the prototype object for the object you want to create with having to define the constructor function  

The object being inherited from is known as the prototype.
Inherited props can be found in prototype object of the constructor

**Indexing prop:**  
Refer to prop of an object either by propName or by its ordinal index[index]  
stick to one way that's define initially always - propName or index  

**Defining prop for an object:**  
defined by using the prototype prop, that is shared by all  object of specified type rather than one instance of an object  
```
Car.prototype.color = null;
car1.color = 'red';
```
Defining Method: method is a function that is associated with an object  
method is a prop of an object that is a function  
define method for an object type by including method defn in the object constructor function  
```
function displaycar() {
  var result = this.year + ' ' + this.make;
  printRes(result);
}

function Car() {
  this.year = 'year';
  this.make = 'make';
  this.displayCar = displayCar; // make this function a method of car
}
```
> call displayCar method => car1.displayCar();  
this - refer to calling object in a method  
Defining getter and setter: help mutating data within an object  

**Object model**  
js - object based language based on prototypes rather than being class based.  

Class based vs prototype based language:  
class based - classes and instances  
class define all the properties that characterize a certain set of objects  
class is abstract rather than any particular memeber in a set of objects it describe.  
instance, is the instantiation of a class  

prototype based language: it simply has object  
any object can be associated as the prototype for another object [this allow second object to share the first object properties]  

In js, instead we define constructor function to create object with particular initial set of values  
new operator with construtor function to create new object  

> Javascript implements inheritance by allowing you to associate prototypical object with any constructor function.  

If you add a property to an object that is used as the prototype for a set of objects, the objects for which it is the prototype also get the new property.  

Inheritance in javascript is the ability to have an object delegates some or all of its implementation to another, by way of hierarchical link.
