---
layout: post
title: Essential OOP
---

Context: is the situation in which the pattern applies, 
problem is what we are trying to achieve and any constraint of the context.
Solution is what solve the problem in the context.

DP: A reusable and named solution to a recurring problem in a context.

Abstraction: [Essential Detail]
Is about identifying the essential details or characteristic of an object with the objective of hiding the complexity of how they are implemented. In java abstraction is achieved through interfaces and abstract classes.

we don't need to know the inner mechanisms and this process can be repeated at higher level.

Encapsulation: hiding information | seperating behaviour that changes
Deciding what an object should expose  to the world, the idea is to proect one part of your application from other parts.
This way when you have change one part you don't have to change all the other parts too. This also applies to behaviour , its not just for data. Encapsulation just does not mean making your member variable private and provide getter/setter to control to these variable. And yes, this is a form of encapsulation , but there's more than that. Encapsulation can aslo help you seperate behaviour from other parts of your application 

public class Car {
	public void checkEngine() {
		...
	}
}

Insted of having a big method in the car class for check all the type of engine a car can have, we can extract or  encapsulate this functinality in a seperate class, EngineChecker. And now the car class will have to use this to access the functinality. Its the same principal as with data, seperating parts of your application to protect the access to them.

class EngineChecker {
	public void checkEngine() {
		...
	}
}

public class Car {
	public void setCheckEngine(EngineChecker ec) {
		...
	}
}


Inheritance:
The process by which one class can inherit the methods and properties from another class.
Inheritance let you build classes based on other classes to avoid duplicated code.

Polymorphism:
when one class inherits from another, polymorphism allows a subclass to stand in for the super class. 
you can write code that works on the super class and also on any of its subclass, making your code more flexible because if you need new functinality, you could grab a new subclass and the actual object type is decided at runtime.
