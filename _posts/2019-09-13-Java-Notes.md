---
layout: post
title: Java Notes
---

java blogs:
[howtodoinjava](https://howtodoinjava.com/java-sorting-guide/)
[javahungry](https://javahungry.blogspot.com/2017/11/how-to-sort-treemap-by-value-in-java.html)
[geeksforgeeks](https://www.geeksforgeeks.org/set-in-java/)
[memorynotfound](https://memorynotfound.com/sorted-map-example/)
[pragmaticnotes](http://pragmaticnotes.com/tag/java/)


-
https://beginnersbook.com/2014/07/how-to-sort-a-treemap-by-value-in-java/

---

Constructor parameters tell me these things are required for an object. Proper state is not guaranteed without them

mics:

A cluster is group of computers that can individually run a software. 
Clustering is needed for achieving high availability for a server software. 
The main purpose of clustering is to achieve 100% availability or a zero down time in service.

Load balancing is simple technique for distributing work load across multiple machines or clusters.
Fail over means switching to another machine when one of the machine fails.

JEE applications use the concept of distributing web application to provide session-failover and enable load balancing. By adding distributable tag in web.xml file (distributable/).

---

---
•JDBC is a Java API(set of classes and interfaces) that is used to connect and execute query to the database. It uses jdbc drivers to connect to the database.

•JDBC Driver is a software component that enables java application to interact with the database.
•There are 3 JDBC statements:

1.Statement: query is compiled each time.
2.PreparedStatement: query is compiled only once. So performance is better.
3.CallableStatement: To execute procedures and functions.
•The DriverManager class manages the registered drivers.
•The ResultSet object represents a row of a table.
•The ResultSetMetaData interface returns the information of table such as total number of columns, column name, column type etc


---
A static initializer block is executed even before JVM calls the main method. They are executed when a Class is loaded into Memory by JVM.

---
Map doesn't allow duplicate keys, but it allows duplicate values. 
HashMap and LinkedHashMap allows null keys and null values but TreeMap doesn't allow any null key or value. 
Map can't be traversed so you need to convert it into Set using keySet() or entrySet() method.

---
I think this question arises because at times we hear the following,

"Method overloading is performed within class. Method overriding occurs in two classes that have inheritance relationship."

The above statement is correct. But your friend is wrong. why?

Because when you extend a class, the subclass have all the methods defined by superclass. It is as if all the methods of superclass have been implemented by the subclass. That means the hello() method has been implemented by the class C as well. Now, you added a method in class C with different parameter (hello(String s)). That means, class C has two methods in all with same name but different parameters and that is "overloading".

Hope it is crystal clear.

---
[Type Conversion:](#)
The word conversion refers to either implicitly or explicitly changing a value from one data type to another, e.g. a 16-bit integer to a 32-bit integer.

The word coercion is used to denote an implicit conversion.

The word cast typically refers to an explicit type conversion (as opposed to an implicit conversion), regardless of whether this is a re-interpretation of a bit-pattern or a real conversion.

So, coercion is implicit, cast is explicit, and conversion is any of them.

Few examples:

Coercion (implicit):
```
double  d;
int     i;
if (d > i)      
d = i;
```
Cast (explicit):
```
double da = 3.3;
double db = 3.3;
double dc = 3.4;
int result = (int)da + (int)db + (int)dc; //result == 9
```

Casting is the process by which you treat an object type as another type, Coercing is converting one object to another.

Note that in the former process there is no conversion involved, you have a type that you would like to treat as another, say for example, you have 3 different objects that inherit from a base type, and you have a method that will take that base type, at any point, if you now the specific child type, you can CAST it to what it is and use all the specific methods and properties of that object and that will not create a new instance of the object.

On the other hand, coercing implies the creation of a new object in memory of the new type and then the original type would be copied over to the new one, leaving both objects in memory (until the Garbage Collectors takes either away, or both).

----
Http Headers:
Cache-Control: tells all caching mechanism from server to client whether they may cache this object. It's measured in seconds.

Content-Encoding: the type of encoding used on the data.

Content-Language: the natural language for the enclosed content.

---
clone() - Creates and returns a copy of this object.
	equals() - Indicates whether some other object is "equal to" this one.
	finalize() - Called by the garbage collector on an object when garbage collection
			determines that there are no more references to the object.
	getClass() - Returns the runtime class of an object.
	hashCode() - Returns a hash code value for the object.
	notify() - Wakes up a single thread that is waiting on this object's monitor.
	notifyAll() - Wakes up all threads that are waiting on this object's monitor.
	toString() - Returns a string representation of the object.
	wait() - Causes current thread to wait until another thread invokes the notify() method
			or the notifyAll() method for this object.
---

```
def "API TO checkForUserType"(){
 	 	 	71	                                 given :'A assignto user id and doc userid'
 	 	 	72	                                         nAssign
 	 	 	73	                                         ndocId
 	 	 	74	                                 when:'labUtility.checkForUserType() is called'
 	 	 	75	                                        def result= labUtility.checkForUserType(root,nAssign,ndocId);
 	 	 	76	                                 then :'It should return assign id if it is of type 1 or type 2 user else return doc id again if it is of type 1 or type 2 else return 0.'
 	 	 	77	                                        result == expectedResult
 	 	 	78	                                where :'provided values of nAssign and ndocId and expectedResult are'
 	 	 	79	                                        nAssign                         |       ndocId  ||      expectedResult
 	 	 	80	                                        10330                           |       10331   ||              10330
 	 	 	81	                                        10332                           |       10331   ||              10331
 	 	 	82	                                        10332                           |       10332   ||              0
 	 	 	83	                                        10331                           |       10331   ||              10331
 	 	 	84	                                        0                                       |       10332   ||              0
 	 	 	85	                                        0                                       |       10331   ||              10331
 	 	 	86	                                        10332                           |       0               ||              0
 	 	 	87	                                        10331                           |       0               ||              10331
 	 	 	88	                                 }
```

https://medium.com/swlh/navigating-java-maps-treemap-vs-hashmap-vs-linked-hashmap-c97e6d248ecf
ds offers the best peroformance in terms of time complexity
sorted?
grow and shring?
unique / duplicate values ?

TreeMap: implemented as red-black tree
each node which tags the node as black or red
tags allow to balance itself when elements are added or remove
sorted - sort itself based on natural ordering of its key
have option of using the custom comparator

HashMap: store key value pair in hashtable, unordered

LinkedHashMap: [adds, a doubly linked list to the hashmap structure]
get the performance benefits of hashmap as well as ordering in the order the elements are inserted.

2 factors that can impact performance of hashmap:
 - load: fullness of each of these buckets
 - capacity: number of buckets created by the hashing function of hashmap
 
As the number of elements in the sturcture grow, it need to be rehashed to create more buckets. [costly operation depend upon the number of entries]
Hashmap perform best if load factor stays below 75%[buckets are 75% full]

---
https://learning.oreilly.com/videos/learning-spring-programming/9781771372879
https://learning.oreilly.com/videos/spring-framework-for/9781789135923
https://learning.oreilly.com/videos/building-web-applications/9781783286539

https://www.youtube.com/watch?v=-wddkBQZuPs

```
https://stackoverflow.com/questions/3637936/java-integer-equals-vs
https://stackoverflow.com/questions/13098143/why-does-the-behavior-of-the-integer-constant-pool-change-at-127
http://java-latte.blogspot.com/2013/11/java-integer-constant-pool.html



https://medium.com/@bartobri/hash-crash-the-basics-of-hash-tables-bef82a8ea550
https://itnext.io/how-and-why-to-cook-equals-and-hashcode-in-java-c108fd5b17dd
https://medium.com/@animeshgaitonde/the-curious-case-of-java-string-hashcode-6d98c734a313
https://dzone.com/articles/working-with-hashcode-and-equals-in-java
https://medium.com/coding-corpus/java-important-methods-equals-hashcode-and-compareto-6adcdf2814c3
https://medium.com/@ellengomez0122/hashcode-and-equals-in-java-f8f49e9202de
https://medium.com/@bilalak90/hash-tables-c84d1b7aeb96
https://medium.com/@eranda/hashing-and-equality-in-java-bbb1b83ab413
https://medium.com/qudini-engineering/java-object-identity-or-how-to-override-equals-hashcode-and-compareto-400fd4547fe0

https://medium.com/@krishnakanthjc/a-detail-look-on-put-method-of-hashmap-in-java-6944808ef17c
https://medium.com/@mr.anmolsehgal/java-linkedhashmap-internal-implementation-44e2e2893036
https://medium.com/@rahilali1991/how-hashmap-works-in-java-d7ed07fe510e
https://medium.com/@mr.anmolsehgal/java-hashmap-internal-implementation-21597e1efec3


https://medium.com/platform-engineer/understanding-java-memory-model-1d0863f6d973


https://dev.to/carey/java-map-keys-should-always-be-comparable-2c1b
https://dev.to/arpitmandliya/how-hashmap-works-internally-in-java-a-debug-approach-58fn
https://dev.to/vrnsky/java-data-structures-417e
https://dev.to/fahimulhaq/top-8-data-structures-for-coding-interviews-and-practice-interview-questions-2pb



https://medium.com/@oliver_hu/java-series-basics-q-a-part-5-1613ae282ac2
https://www.interviewcake.com/java-interview-questions
https://dev.to/javinpaul/20-core-java-interview-questions-for-experienced-professionals-from-investment-banks-53b7
https://dev.to/javinpaul/top-20-string-coding-problems-from-programming-job-interviews-493m
https://blog.usejournal.com/most-frequently-java-interview-question-127e923f70d9
https://dev.to/vijaykhatri96/top-20-java-interview-questions--1lcf
https://dev.to/arpitmandliya/java-interview-questions-for-4-to-7-years-experience-17k9
https://dev.to/codegym_cc/top-21-interview-questions-for-java-developers-you-totally-should-know-4n3l
https://dev.to/codegym_cc/top-21-interview-questions-for-java-developers-you-totally-should-know-4n3l
https://dev.to/abhishekalbert/top-50-question-and-answer-asked-in-phone-interview--3pkc
https://dev.to/javinpaul/50-data-structure-and-algorithms-problems-from-coding-interviews-4lh2
https://codeburst.io/review-these-50-questions-to-crack-your-java-programming-interview-69d03d746b7f
https://medium.com/erpragatisingh/data-structures-interview-questions-answers-8279ab476734
https://www.java67.com/2015/03/top-40-core-java-interview-questions-answers-telephonic-round.html
https://hackernoon.com/20-string-coding-interview-questions-for-programmers-6b6735b6d31c
https://www.freecodecamp.org/news/review-these-50-questions-to-crack-your-java-programming-interview-69d03d746b7f/
https://dev.to/aershov24/60-java-and-spring-interview-questions-you-must-know-802
```

## Final[https://www.ibm.com/developerworks/library/j-jtp1029/index.html]

```
package com.test;

import java.util.Arrays;

// Not immutable: the states array could be modified by a malicious caller
public class DangerousState {
	
	private final String[] states = new String[] {"Albama", "Alaska", "Texas"};
	
	public String[] getStates() {
		return states;
	}
	
	public String[] changeState(int i) {
		String[] arr = getStates();
		arr[i] = "New York";
		return arr;
	}

	public static void main(String[] args) {
		String[] arr;
		DangerousState ds = new DangerousState();
		
		arr = ds.changeState(1);
		System.out.println(Arrays.toString(arr));
	}
	
}

```

```
package com.test;

// immutable: return an unmodifiable list
import java.util.AbstractList;
import java.util.List;

public class SafeStates {
	
	private final String[] states = new String[] {"Albama", "Alaska", "Mumbai"};
	private final List statesAsList = new AbstractList() {

		@Override
		public Object get(int index) {
			return states[index];
		}

		@Override
		public int size() {
			return states.length;
		}
		
	};
	
	public List getStates() {
		return statesAsList;
	}

	public static void main(String[] args) {
		SafeStates ss = new SafeStates();
		System.out.println(ss.getStates());
	}

}

```

---
inline method call: at runtime this is definitely the version of the method that's going to be called.
Only if the method is private can the compiler inline it freely.

Once a final variable has been assigned, it always contains the same value. If a final variable holds a reference to an object, then the state of the object may be changed by operations on the object, but the variable will always refer to the same object.

This applies also to arrays, because arrays are objects; if a final variable holds a reference to an array, then the components of the array may be changed by operations on the array, but the variable will always refer to the same array.

Passing object to a method:
It is critical to realize that when we say pass an object to a method, we are not
sending a copy of an object, but rather a reference to the object.
[When we pass an object to a method, we are actually passing the address,
or reference, of an object to the method.]

Passing an array to method:
When an array is passed to a method, only its reference is passed. A copy of the array
is not created in the method

```
// parse:
int parseInt = Integer.parseInt("2");

//primitive to Integer
Integer wrappedInt = Integer.valueOf(1);

Integer myInteger = new Integer(10);

// get value of integer class and convert back to primitive
int primitive = myInteger.intValue();
```

```
import org.apache.log4j.Logger;

// https://stackoverflow.com/questions/137975/what-is-so-bad-about-singletons

// Don’t assign static references to instance method calls in Java

public class TestStatic {
	
	private static Logger foo = Logger.getLogger(TestStatic.class); // assign static reference to instance method call
	
	// static method: perform the logic inside of it each time it is called, therefore picking up any change to our configuration object
	public static Logger foo() {
		return Logger.getLogger(TestStatic.class);
	}
	
	
	// DI - most elegant: allow us to inject object, which also gives us the benefit of not having to mutate global state in a singleton
	public static Logger foo(Logger log) {
		return log.getLogger(TestStatic.class);
	}
}
```

```
morgan stanley:

https://www.quora.com/I-want-to-prepare-for-my-technical-interview-rounds-by-J-P-Morgan-Mumbai-branch-What-questions-are-asked-by-J-P-Morgan-for-a-5-year-experienced-Java-developer

https://www.quora.com/How-should-I-prepare-for-Morgan-Stanley-interview-in-java

https://www.glassdoor.co.in/Interview/Morgan-Stanley-Mumbai-Interview-Questions-EI_IE2282.0,14_IL.15,21_IM1070_IP2.htm?countryRedirect=true

https://www.glassdoor.co.in/Interview/Morgan-Stanley-Java-Developer-Interview-Questions-EI_IE2282.0,14_KO15,29.htm?countryRedirect=true

https://in.linkedin.com/in/sanjeevkumar-saxena-84421b45?trk=public_profile_browsemap_profile-result-card_result-card_full-click


https://www.javacodegeeks.com/2015/11/top-20-core-java-interview-questions-and-answers-from-investment-banks.html
propagating exception in java
```

When we say “return an object from a method,” we are actually returning the
address, or reference, of an object to the caller.

1. Class methods can access only the class variables and the class constants of the class.
2. Instance methods, including constructors, can access all types of data members.
3. Class methods cannot call instance methods of the same class.
4. Instance methods can call all other methods of the same class.


The for-each loop only allows access to the elements. The elements cannot
be changed.
 - First, you cannot change an element in the array during the iteration.
 - The for-each loop allows access to only a single array.
 - The for-each loop iterates over every element of an array from the first to the last element. 
   We cannot use the for-each loop to access only a portion of an array or to 
   access the elements in reverse order.
   
   
```
Person[] person = new Person[100];
for (int i = 0; i < 50; i++) {
person[i] = ...; //code to create a new Person object
}

for (Person p : person) {
System.out.println(
p.getName());
}
```

This code will crash when the variable p is set to the 51st element (i.e., an element
at index position 50), because the element is null.  

```
angularJS-services[reusable-api]: function or object that can hold behavior or state across our application.
Instantiated only once - each part of our app get access to the same instances
Repeated behavior, shared state, caches, factories etc are all that can be implemented using angularjs services
[factory, service or provider]




https://books.brainysoftware.com/download



set bean properties
set map values
create scoped variables

<c:set var="helloVar" value="hello" />
the above line can be written in scriplet as follow:
<%
	String helloVar = "hello";
	pageContext.setAttribute("helloVar", helloVar);
%>

set bean properties or map values using <c:set>: used target and peoperty instead of var.
if target is map - the peoperty is the name of the key and value is the value for that key.

<c:set target="" peoperty="" value="" />
target must evaluate to javaBean or map object
if target is javabean that it must contain the appropriate getter/setter methods.

ex: <c:set target="bookMap" peoperty="id" value="1" >
this is equivalent to:
bookMap.put("id", "1");


setting the bean property
<c:set target="book" peoperty="book.title" value="Learning the Java Web">
this is equivalent to:
book.setTitle("Learning the Java Web");


---------------------------------------------------
```

```
public class Loops {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // This will be where we test our methods or "call" them
        MtoNEvens(4, 12);
    }

    //This is where the methods will be written or "defined"
    public static void fiveStars() {
        int x = 1;

        while (x <= 5) {
            System.out.print("*");
            x++;
        }
        System.out.println();
    }

    public static void rowStars2() {
      //TODO: Change this to a do-while loop
       
       int x = 1;
        
        do{
            System.out.print("*");
            x++;  
        }
        while (x <= 5);
        
        System.out.println();
    }
    
    public static void rowStars3() {
        for(int i = 1; i <= 5; i++ ) {
        System.out.print("*");
        }
        System.out.println();
    }
    
    public static void rowNStars(int N) {
        int x = 1;
        while (x <= N) {
            System.out.print("*");
            x++;
        }
        System.out.println();
    }
    
    public static void MtoNValues(int M, int N) {
        
        for(int i = M; i <= N; i++) {
            System.out.print(i + " ");
        }
    }
    
    public static void MtoNEvens(int M, int N) {
    
        int i = M;
        while(i <= N) {
            if(i % 2 != 0) {
                System.out.println(i);
            }
            i++;
        }
    
    }
    
    
}
```

java why ConcurrentHashMap doesn't throw concurrentmodificationexception? 

Tell about the projects you worked and questions based on that  

implement caching in java  

How the locking will happen if method is declared as static and synchronized? 

We have a variable that needs to be accessed inside an anonymous method by passing it as an argument. How do we do this?  

What is the difference between Map and Set. What is the key used for storing an object in the set if the set uses a map for storing its data?  

What is the lifecycle of a Thread?  

What is a repository and how can you access it in Java code?  
You are given a file that has sentences (one line per sentence). You are required to find all the longest sentence (one or more sentence can have same length). Explain the logic or write the code to do this.

number of entries in hashtable exceeds than we rehashed the hashtable using the formula - loadfactor * capacity

Serialization: saving state of an object into a file.
transient variable - not persisted

Arguments are pass to the methods by using the call by value;
the value is the actual data in the case of primitive type data, and a reference to an object in the case of reference data type.

List the catch blocks in the order of specialized to more general exception classes.
At most one catch block is executed, and all other catch blocks are ignored.

If a method throws a checked exception, the caller of this method must explicitly include the try-catch statement or the throws clause in the method header. If a
method throws a runtime, or unchecked, exception, the use of the try-catch
statement or the throws clause is optional.

For any object we need to save to a file, its class definition must include the phrase
implements Serializable.

Encapsulation is when a piece of code is written once, wrapped in a method and accessible only through that method.
maintainence of code become easy as portion of the software code is centralized
size of code shrink compared to a situation with no encapsulation
productivity is enchanced as reuse of code is imposed[encapsulated code is written once and used everywhere]

abstraction:

A class that centralizes and shares state and behaviour for a specific concept
code is centralized and smaller => easier to do maintainence on.

Abstraction the process of finding a concept that is shared by several classes and to create a class for that specific concept that class than would be a parent class for all the classes that have that concept in common.
the class can focus on the code that is more related to their entity.


inheritance:
In java inheritance is when a class is based on another class[class based inheritance]
If classB inherits from classA than classA is the parent class or the superclass of classB and classB is the subclass or child class of classA.
A subclass inherits member from the parent class according the access modifier associated to each member.


composition:
implies a parent child relationship
the child cannot exist independent of the parent [child object intended to compsed the parent object]
the life cycle of the involved objects are the same, if one is garbage collected the other will also be garbage collected.

Aggregation:
implies a parent child relationship
the child can exist independently of the parent. []
the lifecycle of each of the involved objects are independent.

Association:
A form of dependency [a reference to an object]
both object have independent lifecycles.


System.in is an instance of the InputStream class that provides only a facility to
input 1 byte at a time with its read method. However, multiple bytes are required to
represent common types of data such as strings. The Scanner class from the java.util
package provides a necessary input facility to accommodate various input routines.

Once we have a Scanner object, then we can input a single word by using its next
method.

------------------------------

why main static?
when you execute a program:
the jvm loads the class you specify and uses that class name to invoke method main.
no object exist yet, so the main must be static to allow the jvm to launch the program.
can place a main method in every class you declare - only the main method you used to execute the application will be called.

```
threadpoolexecutor in java
multithreading and concurrency in java

process of executing multiple threads simultaneously
thread is a light weight sub program
adv:
doesn't block the user because threads are independent
can perform many operation at the same time, so save time

multitasking 								vs 								multithreading:
Each process has its own address in memory		thread share same memory
process is heavy weight							thread is light weight
instance of a program							subset of a program
switching from one process to another process   cost of communication between thread is low  
required time						

ex: opening mutiple chrome window				opening multiple tabs in a chrome window

Thread life cycle:

join: control thread from out program
regular thread: control take by the thread scheduler

java provide a convinient way to group multiple threads in a single object. In such a way, we can suspend, resume, or interrupt group of thread by a single method call.
```

```
FILE IO:

FileInputStream: read data in the form of bytes from file. Read byte oriented data like audio, video, image etc;
ex:
FileInputStream fin = new FileInputStream(file);
int i = 0;
while(i = fin.read() != -1) {
	syso((char)i);
 }
 
FileOutputStream: writing data to a file.
string to bytes:
byte b[] = string.getBytes(); 

BufferedInputStream: read info from stream. Internally uses buffer meachanism to make the performance fast.

BufferedOutputStream: uses buffer to store data. more efficient way to write data than fileinputstream.
[extends - FilterOutputSteam]

SequenceInputstream: use to read data from multiple stream. It read data sequentially.

DataInputStream and DataOutputStream:
read and write primitive data type from/to the input/output stream in a machine independent way.

ByteArrayOutputStream:

InputStream vs Reader:
Both are abstraction to read data from source.
Source can either be file or socket.
InputStream - read binary data.
Reader - read text data.

Everything we read is in the form of bytes.
To convert bytes to text java uses some character encoding and decoding schemes.

FileReader Vs FileInputStream
FileInputStream to read raw streams of bytes from file or socket in java.
It reads from file byte by byte when call the .read() method.
ex: read image, audio, video data.

FileReader extends InputStreamReader, it uses character encoding provide to this class or default character encoding.
It reads each character from the file.
It is used to read stream of character or text data from file and always specify character encoding.
If character encoding is not specified we may miss some data while reading.

BufferedWriter: Provide buffering for writer instance.
It makes performance fast.
```

```
Bytecode is the compiled format for Java programs. Once a Java program has been converted to bytecode, it can be transferred across a network and executed by Java Virtual Machine (JVM).
```

```
Join(): wait for a thread to finish before continuing

package code.test.thread;

public class MyThread extends Thread {
	
	public void run() {
		try {
			Thread.sleep(2000);
		} catch(InterruptedException ie) {
			System.out.println(ie);
		}
		System.out.println("I am in t1");
	}
	
	public static void main(String[] args) {
		Thread t1 = new MyThread();
		t1.start();
		try {
			t1.join();
		} catch(InterruptedException ie) {
			System.out.println(ie);
		}
		System.out.println("I am in main thread");
	}
}

// Because t1 has to sleep for two seconds, the main thread is waiting for t1 to complete, 
// so the whole program will idle for two seconds and then output sequentially I'm t1.I'm main thread

```

```
package test.problem;

import java.util.HashMap;
import java.util.Iterator;

public final class FinalClassExample {
	
	private final int id;
	private final String name;
	private final HashMap<String, String> testMap;
	
	public int getId() {
		return id;
	}
	
	public String getName() {
		return name;
	}
	
	public HashMap<String, String> getTestMap() {
		return testMap;
//		return (HashMap<String, String>) testMap.clone();
	}
	
//	public FinalClassExample(int id, String name, HashMap<String, String> hm) {
//		System.out.println("Deep COPY");
//		this.id = id;
//		this.name = name;
//		HashMap<String, String> tempMap = new HashMap<String, String>();
//		String key;
//		Iterator<String> it = hm.keySet().iterator();
//		while(it.hasNext()) {
//			key = it.next();
//			tempMap.put(key, hm.get(key));
//		}
//		this.testMap = tempMap;
//	}
	
	public FinalClassExample(int id, String name, HashMap<String, String> hm) {
		this.id = id;
		this.name = name;
		this.testMap = hm;
	}
	
	public static void main(String args[]) {
		HashMap<String, String> h1 = new HashMap<>();
		h1.put("1", "second");
		h1.put("2", "second");
		
		String s = "original";
		int i = 10;
		
		FinalClassExample ce = new FinalClassExample(i, s, h1);
		System.out.println(s == ce.getName());
		System.out.println(s.hashCode() + " " + ce.getName().hashCode());
		System.out.println(h1 == ce.getTestMap());  // 
		System.out.println(h1.hashCode());
		System.out.println(ce.getTestMap().hashCode());
		
		System.out.println(h1.toString());
		System.out.println(ce.getTestMap());
		
		i = 20;
		s = "modified";
		h1.put("3", "third");
		
		System.out.println("----------");
		
		System.out.println(s == ce.getName());
		System.out.println(s.toString() + " " + ce.getName());
		System.out.println(s.hashCode() + " " + ce.getName().hashCode());
		
		System.out.println(h1 == ce.getTestMap());
		System.out.println(ce.getId() + " " + ce.getName() + " " + ce.getTestMap());
		System.out.println(h1.hashCode());
		System.out.println(ce.getTestMap().hashCode());
		
		System.out.println(h1.toString());
		System.out.println(ce.getTestMap());
		
		System.out.println("*****");
		System.out.println(h1.hashCode() + " " + h1.hashCode());
	}

}

```

https://github.com/AllenDowney/ThinkJavaCode - src code

primitives types are compared against each other based on value. [a=200 & b= 200; a == b {true}]

compairing two object reference type using == operator. 
	- check whether 2 object reference are pointing to the same entity on memory or not
	below two ways to initialize object are not same.
	- String s1 = "String 1";
	- String s2 = new String("String 1"); // new operator create memory area
	
	- String s3 = new String("hello");
	- String s4 = new String("hello");
	- boolean b = (s3 == s4) // return false
	
	Object obj = s1; [obj == s1 return true]

using equals() to compare reference type:
	- String s3 = new String("hello");
	- String s4 = new String("hello");
	- boolean b = (s3.equals(s4)); return true [compare content]
	
	


public = methods that can be invoked from other classes
void methods don't yield a result
value methods yield a result

main is followed by ( ) 
	contains a list of variables = parameters 
	where the method stores its arguments 
	main has a single parameter = args = type String[]
	whoever invokes main must provide an array of strings

execution always begins at the first line of main

when you use a method you provide the arguments
when you write a method you name the parameters 

overloading = having more than 1 method with the same name
	it is legal as long as each version takes different parameters
	Java will figure out which version to use based on argument provided

all values in java array must be of same type
	int[] counts;
	counts = new int[4];

	//OR in 1 line
	int[] counts = new int[4];

	//OR specify content of array
	int[] a = {1, 2, 3, 4, 5};

size of array must be non-negative

the variable that refers to the array and the array itself are separate
the value of the variable is a reference 

//both a and b point to the same array = alias
//any changes made to 1 with be reflected in the other
double[] a = new double[3];
double[] b = a;

int[] a = {1, 2, 3, 4};
System.out.println(a);
> [I@bf3f7e0
	[ = value is an array
	I = int

java has a for each loop for arrays like python
for (int value : values) {
	System.out.println(value);
}

primitive types != objects
	int
	double
	boolean
	char

primitive values do not provide methods
each primitive type has a corresponding wrapper class
	provides additional methods

strings are objects
	they contain chars
	provide methods for manipulating character data

// string literals are in double quotes
String fruit = "banana";
// chars are in single quotes
char letter = fruit.charAt(0); // 'b'

java uses unicode to rep char
	each char rep by "code unit" (integer number)

strings are immutable
when using methods applied to strings, you get a new string object as the return value
String name = "Alan Turing";
String upperName = name.toUpperCase(); // "ALAN TURING"
// need to invoke string method by using ()
int length = name.length();

substring indexing works like python
String fruit = "banana"
fruit.substring(0, 3); // "ban"
fruit.substring(6, 6); // ""

should not compare strings using ==
	will compare the reference (memory address)
	not the actual value
use equals method
String ada = "Ada Lovelace";
String alan = "Alan Turing";
if ada.equals(alan) {
	System.out.println("Same name");
}

garbage collection

Point blank = new Point(3, 4);
blank = null;

if there is no references to an object, there is no way to access its attributes or invoke a method on it
however, Point(3, 4) is still taking up space in memory

as the program runs the system automatically looks for stranded objects and reclaims them
then space is reused for new objects

attribute = object's data
method = object's code
class = defines which attributes and methods the object will have

java library source code is stored in 
/Library/Java/JavaVirtualMachines/jdk1.8.0_144.jdk/Contents/Home/src.zip

classes
	defining a class creates new object type with the same name
	every object belongs to some object type
	a class definition is like a template for objects
		specifies what attributes the objects have
			attributes = instance variables = each instance has its own variables 
		what methods can operate on them

data encapsulation
	use objects as parameters and return values 
	rather than passing and returning multiple values 

public class
	can be used by other classes
private instance variables 
	can only be accessed from inside the class
	if you try to read or write these private variables from outside the class = compiler error

information hiding 
	if anything in 1 class changes, the other class will have to change as well
	use methods to interact with another class > the two classes are independent of one another
	private instance variables 
		help keep classes isolated from each other 
		so that changes in one class won’t require changes in other classes
	simplifies what other programmers need to understand in order to use your classes

constructor
	specialized method that initializes instance variables 
	name of constructor = name of class
	have no return type
	keyword static is omitted
	custructors can be overloaded = provide multiple constructors with different parameters 

this 
	refers to the object we are creating
	can read and write the instance variables of this
	can pass this as an argument to other methods
	cannot declare this
	cannot make an assignment to it

client = class that uses objects defined in another class

static members belong to the class not a specific instance
only 1 instance of a static field exists

== checks if 2 objects are identical
	aka same memory address

equals checks if values are equivalent 
	same value

pure methods
	don't modify parameters of an existing object
	don't have side effects like printing
	the return value depends only on the parameters 

modifier methods
	usually void methods but sometimes return reference to the object they modify
	more efficient bc don't create new objects
	error prone

to make a class immutable
	provide getters but no setters
	pure methods only
	can be difficult to work with at first
	avoid hours of debugging later

local variables
	declared inside a method
	created when the method is invoked 
	memory is reclaimed after the method has ended

instance variables
	declared inside a class definition 
	created when you construct an object
	reclaimed when the object is garbage collected

class variables
	defined in class definition
		before method definitions
	static
		identified by keyword static
		means variable is shared
	created when program begins or class is used for the first time
		survive until the program ends 
	shared across all instances of the class
	final
		often used to store constants
	advantage
		don't need to undergo constant garbage collection
		can be used by other methods and classes
		no danger making them public because
			array variables are final
			string references are immutable

comparisons
	< > ==
		can be used to compare primitive types
		these operators do not work on object types
	totally ordered
		some types you can compare any two values and tell which is bigger
	unordered
		no way to tell if 1 is bigger than the other
		true < false => compiler error
		

		
SOME MISC:

java handle object by reference - must not confuse with "pass by reference"
pass by reference - used to describe the medthod calling

java - pass by value language
when a reference is involved, the value that is passes is a copy of the reference(as a value)
Circle c = new Circle(2);
manipulate(c);
syso("Radius: " + c.getRadius);



		
-----------------------------------------------------------------------------------------------------------------------


JAVA AND XML:

text cannot contain any delimiter char sequence such as </, enclose element within CDATA construct.
CDATA Construct:

<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>
<journal>
<article>
<![CDATA[This is some arbitrary text <within> a CDATA!]]>
</article>
</journal>

elements can have attribute:
<article title="Hello"></article> [define as a name - value pair]

<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>
<journal>
<article title="A Tutorial on XML 1.0" >
<![CDATA[This is some arbitrary text <within> a CDATA!]]>
</article>
<article/>
</journal>


To add another attribute named date with the value <04/12/2006>. [Not allowed to include delimiter char within an attribute]
However, &lt; char to escape < and &gt; char to escape >

<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>
<journal>
<article date="&lt;04/12/2006&gt;" title="A Tutorial on XML 1.0" >
<![CDATA[This is some arbitrary text <within> a CDATA!]]>
</article>
<article/>
</journal>


PARSING XML: to extract the content information contained in the document.
Objectives: parsing fundamental aspect of processing an XML document.
 ensure that document is well formed.
 check that the document conforms to xml schema/DTD.
 access/modify elements and attributes that meets the specific need of an application.

Various approaches:
 - DOM parsing
 - Push parsing
 - pull parsing

DOM [Document Object Model] Approach: 
 - platform-and language neutral interfaces for accessing and manipulating content
 - Represent a document as a tree of node object [some node object have child node objects; leaf object with no children]
 - Generic node type is specialized to other node type, and each specialized node type specifies a set of allowable child node types.
 
EXAMPLE:
Document - represent an xml document   - allowable child node: DocumentType, ProcessingInstruction, Element

In memory: complete document is constructed
Can be accessed randomly, [do not have to be accessed in document order]
Random access is fast and flexible [parsing complete document reduce parsing efficiency]
API for DOM parsing approach - JAXP 1.3

PUSH APPROACH: push parser generates synchronous event as document is parsed. [event processed by an application using a callback handler model]
API for push approach - SAX 2.0[also include in JAXP 1.3]
SAX is a read only API [Recommended if no modification or random access navigation of an XML document is required]

ContentHandler[interface] Event Methods:
startElement() - start of an element

ErrorHandler[interface]
fatalError() - Violation of XML


PULL APPROACH: events are pulled from an XML document under the control of the application using the parser.
StAX is similar to the SAX in that both offer event based API's.

In the StAX API,
 - its the application rather than the parser that controls the delivery of the parsing events.
 - offer two events based API: Cursor API & Iterator API [both are under application control]
 - Cursor API: allow walkthrough of the document in document order [lowest level access to all structural and content information]
 - Iterator API - provide  access to the structural and content information in the form of event objects.
 - unlike the SAX API, StAX can be used for reading and for writing XML documents.
 
Cursor API: XMLStreamReader interface is the main interface for parsing an XML document.
It scan an XML document structure and content using the next() and hasNext() methods.
next() - return an integer token for the next parse event.


Iterator API: XMLEventReader interface - for parsing an XML Document.
 - You can use this interface to iterate over an XML document structure and content using the nextEvent() and hasNext() methods.
 - the nextEvent() method returns an XMLEvent object.
 - XMLEvent interface provide utils methods for determinig the next event type and for processing it appropriately.

Recommended for data-binding application. 
[specifically for marshaling and unmarshaling of an xml document during the bidirectional XML-JAVA mapping process]  included in J2SE 6.0

--------

<?xml version="1.0" encoding="UTF-8"?>
<catalog title="OnJava.com" publisher="O'Reilly">
<journal date="January 2004">
<article>
<title>Data Binding with XMLBeans</title>
<author>Daniel Steinberg</author>
</article>
</journal>
<journal date="Sept 2005">
<article>
<title>What Is Hibernate</title>
<author>James Elliott</author>
</article>
</journal>
</catalog>


Parsing with the DOM Level3 API:

Represent an XML document as a tree of DOM nodes.
Each node in the tree is a specialized Node object that is an instance of one of the specialized node type.
classes and interfaces are in the package: org.w3c.dom

NodeList interface represent an ordered list of nodes. 
A NameNodeMap represent an unordered set of nodes, such as attributes of an element.
Both, these are useful in traversing the DOM tree representing an XML document.
XML document parsing API - javax.xml.parsers package

import the org.xml.sax package to access the SAXException and SAXParseException classes, which are used in error handling.
[Relience of the DOM API on the SAX API specified by the JAXP 1.3]

DOM API Parsing Steps:
 - create a DOM parser factory
 - use the parser factory to instantiate a DOM parser.
 - use the DOM parser to parse an XML document and create a DOM tree
 - access and manipulate the XML structure and content
 
The DocumentBuilder class implements the DOM parser.
Steps to instantiate a DocumentBuilder object are as follow: 
 - create a DocumentBuilderFactory object using the static method newInstance().
   DocumentBuilderFactory - class is factory API for generating DocumentBuilder objects.
   
 - create a DocumentBuilder object by invoking the newDocumentBuilder() static method on the DocumentBuilderFactory object.

DocumentBuilder parser create an in memory DOM structure from an XML document.

To handle validation error during parsing, you can define a class that implements the ErrorHandler interface. 

Code Sequence:

// create a DocumentBuilderFactory
DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
// create a DocumentBuilder
DocumentBuilder documentBuilder = factory.newDocumentBuilder();
// create and set an ErrorHandler
ErrorHandlerImpl errorHandler = new ErrorHandlerImpl();
documentBuilder.setErrorHandler(errorHandler);

A parser can parse an XML document from a file, an InputSource, an InputStream, or an URI.

// to parse an XML document froma file.
Document document = documentBuilder.parse(new File("catalog.xml"));

The Document interface provide various methods to navigate the DOM structure.
Example:
 - getDocumentElement()   - return the root element.
 - getElementById(String) - gets an element for a specified ID


The org.w3c.dom.Element - represent an element in the DOM structure.
Obtain element attribute and subelement from an Element object.

Methods in the Element interface:
 - getAttributeNode(String) - return an Attr node for an attribute. 
 - getTagName() - get the element tag name.
 
 
Attr interface represent an attribute node. We can obtain attribute name and value from Attr node.
Attr Interface:
getName()   - return the attriubute name
getValue()  - return the attribute value 

All the specialized Node interfaces, such as Document, Element and Attr inherit methods defined by the Node interface.
List of methods in the Node interface.

 - getAttributes() : Return a NamedNodeMap of attribute for an element.
 - getChildNodes() : Return the child nodes in a node.
 
 
Code: Retrieving the Root Element Name: 

Element rootElement = document.getDocumentElement(); // retrieve the root element with the getDocumentElement()
String rootElementName = rootElement.getTagName();   // obtain the root element name with the getTagName()

Code: Retrieving Root Element Attributes

hasAttributes() : test whether an element has attributes
getAttributes() : retrieve the attributes

if(rootElement.hasAttributes()) {
	NamedNodeMap attributes = rootElement.getAttributes(); 
}


NamedNodeMap interface are used to represent collections of nodes that can be accessed by name.
NamedNodeMap method: [NamedNodeMap iterated over to retrieve the value of attributes]
 - getNodeLength(): return the attrbute list length
 - item(int): attributes in the attribute list are retrieved with the item(int) method
 
Attr object method [Attr attributeObject]
 - getName() - return the attribute name 
 - getValue() - return the attribute value
 
CODE: Retrieving Attribute Values:
for(int i = 0; i < attribute.getLength(); i++) {
	Attr attribute = (Attr) (attribute.item(n));
	Syso("Attribute " + attribute.getName() + " with value " + attribute.getValue());
}


rootElement 
 - subnodes: retrieve the node with the getChildNodes() method.
 - hasChildNodes(): test whether an element has subnodes.
 
CODE: Retrieving Nodes in the Root Element:
if(rootElement.hasChildNodes()) {
	NodeList nodeList = rootElement.getChildNodes();
}


The NodeList interface provides the abstraction of an ordered collection of nodes.
NodeList Methods:
 - getNodeLength() - return the node list length.
 - retrieve the nodes in the node list with the item(int)
 
CODE: Retrieve Nodes in a NodeList:
for(int i = 0; i < nodeList.getLength(); i++) {
	Node node = nodeList.item(i);
}


The Node interface is the primary datatype for the entire Document Object Model. It represents a single node in the document tree.
If a node is of type Element, a Node object may be cast to Element.
Node type id obtained with the Node interface method 
 - getNodeType(): returns a short value [i.e: ELEMENT_NODE (Node type: Element node)]

CODE: Casting Node to Element:
if(node,getNodeType() == Node.ELEMENT_NODE) {
	Element element = (Element) (node);
}
 
If an element has a text node, obtain the text value with the getNodeValue() method
 - String textValue = node.getNodeValue();
 

DOM API Example: DOMParser.java [parse the xml document]
 - DocumentBuilder object - to parse the xml document
 - Document object - represent in memory tree structure
 - retrieve the node representing the root element from the Document object



Parsing with SAX 2.0: [Event based API to parse an XML document.]
SAX 2.0 is a push-model API; events are generated as an XML document is parsed.
Events are generated by the parser and delivered through the callback methods defined by the application.

Key Point:
 - import atleast two package:
    - org.xml.sax: SAX interfaces
	- javax.xml.parsers: SAXParser and SAXParserFactory classes.
	
	xml.sax.helpers: helper classes for using the SAX API

 - ContentHandler is the main interface that an application needs to implement because it provides event notification about the parsing event.
 - DefaultHandler class provides a default implementation of the ContentHandler interface.
 -  To handle SAX parser events, an application can either define a class that implements the ContentHandler interface 
	or define a class that extends the DefaultHandler class.
 - SAXParser class ro parse an XML document.
 - We obtain a SAXParser object from a SAXParserFactory object.
 - To obtain SAXParser object, first create an instance of the SAXParserFactory using the static method newInstance().
    - SAXParserFactory factory = SAXParserFactory.newInstance();
	
	
JAXP Pluggability for SAX: [JAXP 1.3 provides complete pluggability for the SAXParserFactory implementation classes.]

SAX Handlers: [To parse a document using the SAX 2.0 API, you must define two classes.]
 - A class that implements the ContentHandler interface
 - A class that implements the ErrorHandler interface
 
DefaultHandler helper class that fully implements the ContentHandler and ErrorHandler interfaces and provides default behavior 
for every parser event type along with default error handling.

startDocument() and endDocument() methods: the event type is output

In the startElement() method, the event type, element qualified name, and element attributes are output. 
 - startElement(String uri, String localName, String qName, Attributes attributes)
   - parameter - uri:  is the namespace uri [may be null for an element]
   - parameter - localName: is the element name without the element prefix
   - parameter - qName: is the element name with the prefix [if an element is not in a namespace with a prefix, localName is the same as qName]
   - parameter - attributes: is a list of element attributes.
   
 - the startElement() method prints the qualified element  name and the element attributes
 - the Attributes interface method:
    - getQName(): return qualified name of an attribute
	- getValue(): return attrbute value

characters(): invoked for a text event, such as element text, prints the text for a node

methods: fatalError, error and warning - print the error message contained in the SAXParseException object


SAX Parsing Steps:
 - create a SAXParserFactory object with static method newInstance()
 - create a SAXParser object from the SAXParserFactory object with the newSAXParser() method.
 - create a DefaultHandler object, and parse the XML document with the SAXParser method parse(File, DefaultHandler)

Points to remember:
DocumentBuilderFactory considered as top level factory which internally cotains individual factory 
i.e - DocumentBuilderFactory#newInstance() 
which is able to create the family of related products without specifying their concrete classes (as it just return the DocumentBuilderFactory not any specific implementation)

This class use the design pattern.

Refer: https://stackoverflow.com/questions/2280170/why-do-we-need-abstract-factory-design-pattern?rq=1

************************************************************************************************************************



JSP & SERVLET:

name of the web-app: represent the context root, which tomcat uses when resolving URL.

HttpServlet extends GenericServlet - which implements the Servlet interface.
HttpServletRequest extends ServletRequest
HttpServletResponse extends ServletResponse

method = "POST" : use doPost() to handle the http request
response.setContentType("text/html"); - this method come from the ServletResponse interface
request.getParameter("color"); method from the ServletRequest interface [arg , matches the value of the name attribute]

request.setAttribute("styles, result"); - add an attribute to the request object
request.getAttribute("styles"); - getting an object from the request object.

Container provide a mechanism called "request dispatching" that allows one container managed component to call another.
request.getRequestDispatcher("result.jsp"); instantiate a request dispatcher for the jsp

init() always completes before the first call to service()


why is there an init()? why isn't the constructor for initializing a servlet?

Request and Response - key to everything and arguments to the service():

ServletRequest interface:
 - getAttribute(String): object
 - getContentLength(): int
 - getInputStream(): ServletInputStream
 - getLocalPort(): int
 - getParameter(String): String
 - getParameterNames(): Enumeration, and many more methods...
 
ServletResponse interface:
 - getBufferSize(): int
 - setContentType(String): void
 - setContentLength(int): void
 - getOutputStream(): ServletOutputStream
 - getWriter(): PrintWriter, and many more methods...
 
HttpServletRequest interface:
 - getContextPath(): String
 - getCookies(): Cookie[] 
 - getHeader(String): String
 - getQueryString(): String
 - getSession(): HttpSession
 - getMethod(): String, and many more methods...
 
HttpServletResponse interface:
 - addCookie(Cookie): void
 - addHeader(String name, String value): void
 - encodeRedirectURL(String url): String
 - sendError(int): void
 - setStatus(int): void, and many more methods...
 
 
Session is an object used to maintain conversational state with a client.

SingleThreadModel is designed to protect instance variable.




Servlet - Filter:

chain.doFilter(request,response): allow the request pass Filter to continue to the page request.
 - allow request to move forward. It can go to the next filter or to the target.
 
Working models of Filter:


Java servlet Filters: used to intercept a request [conduct pre/post - processing]

 - Logging of request
 - Authentication and Authorization
 - Encryption and Decryption
 - Formatting the request header or body before sending to the servlet.
 
Filter can also be implemented in chain [order - define using the web.xml]

Implementation - Filter Interface
Methods:
 - init(FilterConfig config): invoked when filter is initialized
 - doFilter(HttpServletRequest request, HttpServletResponse response, FilterChain chain): 
     - invoked everytime filter has to filter a request.
	 - filter action on the request can be implemented here.
	 - FilterChain parameter used to implement the next filter in the filter chain.
 - destroy(): invoked when filter is taken out of service	 
	 
Let's use filter:
 - log IP address and timestamp of the request coming to the servlets. [we'll use filter to achieve this requirement]

 
 
----------------------------------------------------------------------------------------------------------------------

JSTL: standard tag libraries that provide tag to control jsp page behaviour
EL: perform comparisons, either between numbers or objects




_________________________________________________________________________________________________


Abstraction:
handling complexity by hiding unnecessary details.
enable user to implement more complex logic on top of the provided abstraction

object provide abstraction that hides the internal implementation details.
 - object available to call and which input parameters are needed to trigger specific operation

  - hide all decisions and processing steps in CoffeeMachine class
  - constructor method that takes a Map of CoffeeBean object to create new CoffeeMachine object and
    brewCoffee method that expect your CoffeeSelection and return a Coffee object


Encapsulation:
bundling data and method that work on that data within one unit
hide the internal representation or state of an object from the outside [information hiding]
attribute that is not visible from the outside of an object, and bundle it with methods that provide read and write access to it. then you can hide specific info and controll access to the internal state of the object.



---

There are two styles to convert a collection to an array: either using a pre-sized array (like c.toArray(new String[c.size()])) or using an empty array (like c.toArray(new String[0]).

In older Java versions using pre-sized array was recommended, as the reflection call which is necessary to create an array of proper size was quite slow. However since late updates of OpenJDK 6 this call was intrinsified, making the performance of the empty array version the same and sometimes even better, compared to the pre-sized version. Also passing pre-sized array is dangerous for a concurrent or synchronized collection as a data race is possible between the size and toArray call which may result in extra nulls at the end of the array, if the collection was concurrently shrunk during the operation.

This inspection allows to follow the uniform style: either using an empty array (which is recommended in modern Java) or using a pre-sized array (which might be faster in older Java versions or non-HotSpot based JVMs). 


There is no fundamental difference between state and attributes therefore it's simpler to define state as being possibly mutable or immutable. While having (immutable) attribute and (mutable) state is not incorrect (and is in many sense equivalent), that distinction makes the definition more complex than necessary. Although IMO the term "state" is probably not the best term to describe the concept since "state" somehow implies that it is supposed to change, while the "state" -- as described in Oracle's article -- does not have that

---

Float.parseFloat(price); // return a primitive type
Float.valueOf(price);  // return an object type

state is just a set of values of the object fields

final means that you can't change the object's reference to point to another reference or another object, but you can still mutate its state (using setter methods e.g). ... final modifier is applicable for variable but not for objects, Whereas immutability applicable for an object but not for variables.
final vs Immutability in Java - GeeksforGeeks


With mutable classes, the exposed methods of these classes do change (or mutate) the internal state of the object, instead of creating a whole new object. As a result, if you have multiple variables pointing to the same mutable object, if one of those variables is used to access the object and make changes to it, accessing that same object from any of the other variables will see the changes as well


Because a collection can be passed to a method as type Collection, all of the methods declared in the Collection interface can be invoked on the incoming reference in a polymorphic manner.

What is a data type?
All data types specify the operations that can be performed on an entity of that type.  (Data types also specify the kinds of data that can be stored in an entity of that type, but that is not germane to this discussion.) 


Connection Pool Manager
Connection pooling means that connections are reused rather than created each time a connection is requested. Your application can use connection pooling through the DataDirect Connection Pool Manager.
Connection pooling is performed in the background and does not affect how an application is coded; however, the application must use a DataSource object (an object implementing the DataSource interface) to obtain a connection instead of using the DriverManager class. A class implementing the DataSource interface may or may not provide connection pooling. A DataSource object registers with a JNDI naming service. Once a DataSource object is registered, the application retrieves it from the JNDI naming service in the standard way.


Each thread has its own stack, and so its own copy of variables it can access. When the thread is created, it copies the value of all accessible variables in its own memory. The volatile keyword is used to say to the jvm "Warning, this variable may be modified in an other Thread". Without this keyword the JVM is free to make some optimizations, like never refreshing those local copies in some threads. The volatile force the thread to update the original variable for each variable.

But both are static variable , then how come it is possible , that threads are maintaining them in their local stack and modified value is not reflected to other thread?

If I am not wrong, Yes that is true for static variables too, as static variables exist in Java and processor does not know about them. So for processor its just a place in memory that is going to be edited by several threads.

But only one copy of that variable will be there , how come different thread will have their own copy?

Processor caching is hardware detail and is unrelated to Java. Yes for us there is only one instance but in memory that can be copied for caching purposes

Only way to get latest data is either you syncronize the get method or declare state as volatile.


Java does manipulate objects by reference, and all object variables are references. However, Java doesn't pass method arguments by reference; it passes them by value.

https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy
In shallow copy, only fields of primitive data type are copied while the objects references are not copied. Deep copy involves the copy of primitive data type as well as objet references.

Collection:
interfaces, the abstract data types that the framework supports.
implementations, the concrete versions of these interfaces.
algorithms, the predefined actions that can be defined on either the interfaces or their implementations.
All implementations are unsynchronized.
All implementations are serializable and cloneable
All implementations support having null elements.


working of thread execution pool
inner workings of objects mutation
System.identityHashCode
lock monitor synchronized metd
Executors.newFixedThreadPool medt
monitor and mutual exclusion:
atomicity
ordering
visibility

it allows multiple threads to coordinate the order in which they run

only one thread at a time is going to be in the critical section to avoid race condition

java1.5;
executor framework, synchronizers[semaphores], blocking queues, atomics[int/long], concurrent collections[concurrentHashmap]

java1.7;
java fork join pool - parallelism support
data parallelism- that is you have the same task and you execute it on different chunks of data and thats get into the divide conquer like model

java1.8;
parallel streams and completeable futures - allow functional programming which simplifies a lot of coding
asynchrnous programming



sciencing.com

---
Good Morning Team,

Please note 2 new code review items on the code review checklist. We will be adding example snippets for these in the checklist. 

Runtime Exception should be caught after all checked exceptions
Custom Exceptions should be checked exceptions 

Runtime Exception should be caught after all checked exceptions
In a nutshell, we should not be catching the generic Exception in our code. Instead, we should catch all possible Checked Exceptions and Runtime Exception to catch any other exceptions that may occur at runtime. 

Since Sonar warns developers to not catch generic Exception, and the compiler warns to catch any Checked Exception, but there is no warning to the developers to catch a Runtime Exception, hence we have added it to the code review checklist. 

Custom Exceptions should be checked exceptions 
Any Custom Exceptions should be Checked Exceptions. i.e. They should extend the java.lang.Exception class not java.lang.RuntimeException

```
when we pass an object to a method, we are actually passing the address, or reference, of an object to a method.
```
