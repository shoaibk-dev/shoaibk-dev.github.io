---
layout: post
title: Java Arrays
---

```
package com.ocjp.demo;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class PrimitiveArrayEx {
	
	public static void main(String[] args) {
		
		int[] number = {1,2,3,4,5,6,7,8};
		if(contains(number, 2)) {
			System.out.println("Hello 2");
		}
		
		List<Integer> list = convertIntArrToList(number);
		System.out.println(list);
		
		List<String> list1 = new ArrayList<>();
		list1.add("Hello");
		list1.add("World");
		
		String[] arr = (String[]) list1.toArray(new String[list1.size()]);
		System.out.println(Arrays.toString(arr));
		
		
	}

	private static boolean contains(int[] array, int v) {
		
		boolean result = false;
		for(int i : array) {
			if(i == v) {
				result = true;
				break;
			}
		}
		
		return result;
	}
	
	
	public static List<Integer> convertIntArrToList(int[] number) {
		List<Integer> list = new ArrayList<>();
		for(int i : number) {
			list.add(i);
		}
		return list;
	}
	
}

```
site: http://deathbycode.blogspot.com/2010/11/toarray-vs-toarrayt.html

java.util.ArrayList has 2 conversion methods defined to get an array out of the elements stored in the list.

1. public Object[] toArray()
2. public T[] toArray(T[] a), this is a new addtion from java 1.5 onwards.

So a developer (included me :)) who is placed against java 1.5 arena may be in dilemma which one to use. Developers who are like minded as myself will at first glance be tempted to use 1st method as it has minimal signature; no parameters. But soon they use this they have to cast it to their respective type to appease compiler as the method returns Object[].

Something like this:

List list = new ArrayList();
list.add("Hello");
list.add("World");

String[] strArr = (String[]) list.toArray();

What will follow afterwards?...

Exception in thread "main" java.lang.ClassCastException: [Ljava.lang.Object;

Voila!!! It will throw ClassCastException during execution. So what went wrong in the first place? We have defined a list of string and thanks to 'generics social police', we are not allowed to add any other types in the list but Strings. So so far so good. Our list contains all Strings. Then we want to make out an array from this and.. it bombed!!!

Here lies the secret. In java arrays are full fledged objects. And so it also has all idiosyncracies/tantrums that reference types have like inheritence etc.

Java arrays are covariant in nature. It means if A is subtype of B then A[] is also subtype of B[]. This causes enough problem pre-generics days. As evident from the above example it bombs at runtime if the target array(TC) type is not actually an instance of compatible type of source array (SC) type.


As String(TC) and Object(SC) are in same hierarchy and String is subtype of Object hence String[] is also subtype of Object[]. Thus it passes compile time legality check while using casting conversion expression. (We cannot cast String to Integer or int[] to double[] as they do not fall into same hierarchy.. they are mere siblings)
............

The runtime validation during casting (the execution of bytecode instruction.. the actual casting) failing because toArray() internally creates pure Object[] instance. Hence in runtime the 2 objects differ.

public Object[] toArray() {
Object[] result = new Object[size]; // This is the source of confusion..
System.arraycopy(elementData, 0, result, 0, size);
return result;
}

So not only we are getting the type as Object[] it actually points to real Object[] instance; Would it be pointing to String[] the runtime casting will not fail.

e.g:
Object[] oa = new String[10];
String[] sa = (String[]) oa; Passes both compile time and runtime validation

Object[] oa = new Integer[10];
String[] sa = (String[]) oa; Passes only compile time and fails at runtime validation


The mystery is now revealed. But then what is the point of keeping such a method?
We should not forget that the method is dated back pre-generics days of java. So they did not have other choices. To use this method, we have to iterate through the array and cast appropiately.(I those days thers is only raw List available).

So we can now see which tempted us choosing this method at first place has its own price.

Here the 2nd method.

From the method signature it is clear that we do not have to enter any casting couch problems (pun intended :D) in this case.

But one thing is worth to know :

a) From the passed in array, the arraylist class finds the correct component type of the target array using reflection. This is the MOST PRIMARY reason of passing the array. Even if we pass 0-length array it will not throw ArrayIndexOutOfBoundsException.

So in a nutshell, Use toArray(T[]) insted of toArray() from java1.5+.
