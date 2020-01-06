---
layout: post
title: misc questions
---

myPrograms:
```
package code.intrv.test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Scanner;

public class Main {
	
	public static String removeCharInString(String str, char charToBeRemoved) {
		if(str == null)
			return "";
		StringBuilder strbuild = new StringBuilder();
		for(int i = 0; i < str.length(); i++) {
			char ch = str.charAt(i);
			if(ch == charToBeRemoved) {
				continue;
			}
			strbuild.append(ch);
		}
		return strbuild.toString();	
	}
	
	public static boolean isPrime(int num) {
		for(int i = 2; i <= num / 2; i++) {
			if(num % i == 0) {
				return false;
			}
		}
		return true;
	}
	
	private static void largestAndSmallest(int[] num) {
		
		int min = num[0];
		int max = num[0];
		
		for(int i = 0; i < num.length; i++) {
			if(num[i] > max) {
				max = num[i];
			}
			
			if(num[i] < min) {
				min = num[i];
			}
		}
		System.out.println(Arrays.toString(num));
		System.out.println("LARGEST " + max);
		System.out.println("SMALLEST " +  min);
	} 
	
	
	public static void swap(int x, int y) {
		x = x * y;
		y = x / y;
		x = x / y;
		
//		x = x ^ y; 
//		y = x ^ y;
//		x = x ^ y;
		
		System.out.println("X = " + x);
		System.out.println("Y = " + y);
	}
	
	public static void main(String args1) {
		Scanner scanner = new Scanner(System.in);
		System.out.println("enter the number");
		int r = scanner.nextInt();
		int n = 0;
		for(int i = 0; i < r; i++) {
			for(int j = 0; j <= i; j++) {
				System.out.print(++n + " ");
			}
			System.out.println();
		}
	}
	
	public static List<Integer> listOfPrime(int num) {
		boolean isPrime = true;
		List<Integer> list = new ArrayList<>();
		for(int i = 1; i < num; i++) {
			isPrime = isPrime(i);
			if(isPrime) {
				list.add(i);
			}
		}
		return list;
	}
	
	public static int SquareOfNum(int num) {
		int result = num;
		while(!(result * result - num < 1)) {
			result  = (result + num / result) / 2;
		}
		
		return result;
		
	}
	
	// recursive
	public static int factorial1(int num) {
		if(num == 0)
			return 1;
		return num * factorial1(num - 1);
	}
	
	public static int factorial(int num) {
		int result = 1;
		while(num != 0) {
			result = result * num;
			num--;
		}
		return result;
	}
	
	public static String palindrome() {
		return null;
		
	}
	
	static <T> void display(T[] arr) {
		for(int i = 0; i < arr.length; ++i) {
			if(arr[i] != null) {
				System.out.print(arr[i] + " ");
			}
		}
	}
	
	public static void main(String... args) {
		System.out.println(removeCharInString("shoaib khan", 'a'));
		System.out.println(isPrime(85));
		largestAndSmallest(new int[] {0,2,4,5,6});
		
		swap(3, 6);
		
//		main("5");
		
		System.out.println(listOfPrime(100));
		
		System.out.println(SquareOfNum(49));
		
		System.out.println(factorial(5));
		
		String[] arrnames = new String[4];
		arrnames[0] = "shoaib";
		arrnames[1] = "zoheb";
		arrnames[2] = "bilal";
		arrnames[3] = "bushra";
		display(arrnames);
	}
	
}

```

---
CITIUSTECH:

Questions on inheritance,String, working of Hash Map, Collections, Static and init block, design patterns, spring core and mvc  

Oops concept
Mvc concepts
SQL queries

Which Design patterns do you know ? Can you write a code?  
What are various properties of Ajax post method? Write down the code?  
How did you implement DAL in your previous project? Can you write a code?  
Questions on try catch Finally blocks. 
Suppose you have a class Person with two properties say first-name and last name.
I want when you create object of a class and call a toString method on it, it should return first-name and last name. What to do for this behavior? 

exception handling
question related to current project
How to get duplicate elements in int array, the most sufficient way 
Debuging and problem solving approach related question 
singleton pattern
collection related

How to sort a hash map on the basis of values


1. Current project with my current employers
2. Core java questions about abstraction, encapsulation, String and collections.
3. They had a lot of emphasis on Spring. Spring configurations and concepts.  


Conceptual OOP questions
How would you test an ATM machine if it is working properly? (Walk through all the Test Cases) 

Questions on data structures such as linked lists
Questions on databases- inner join, outer join, etc.
Questions on object oriented programming concepts  

java basic programs like fibonacci,prime number etc.  

Bubble sort?
HashMap ,HashSet,
List and link list differences?  


morgan stanley:

https://www.quora.com/I-want-to-prepare-for-my-technical-interview-rounds-by-J-P-Morgan-Mumbai-branch-What-questions-are-asked-by-J-P-Morgan-for-a-5-year-experienced-Java-developer

https://www.quora.com/How-should-I-prepare-for-Morgan-Stanley-interview-in-java

https://www.glassdoor.co.in/Interview/Morgan-Stanley-Mumbai-Interview-Questions-EI_IE2282.0,14_IL.15,21_IM1070_IP2.htm?countryRedirect=true

https://www.glassdoor.co.in/Interview/Morgan-Stanley-Java-Developer-Interview-Questions-EI_IE2282.0,14_KO15,29.htm?countryRedirect=true

https://in.linkedin.com/in/sanjeevkumar-saxena-84421b45?trk=public_profile_browsemap_profile-result-card_result-card_full-click


https://www.javacodegeeks.com/2015/11/top-20-core-java-interview-questions-and-answers-from-investment-banks.html
propagating exception in java



hexaware:

Multithreading, inheritance, oops concepts, Webservices, spring architecture, memory leaks  
use of lazy and eager loading in spring  
exception,hashset,treeset,jsp,servlet
What is notify in multithreading  

1.differnce between concencrete​ wsdl and abstract wsdl ? what is endpoint , bindings
2.what is oops concepts ?
3.what is cohesion, aggregation ?
4.diffence between uinon and join in oracle ?
5.best design pattern ? practical senario to use ? singletonton pattern ?
6 query to join two tables ?
7.what is use of group by in oracle ?  

Logical and technical they asked timecomplexity of algorithms,linked list, tree questions in exam
