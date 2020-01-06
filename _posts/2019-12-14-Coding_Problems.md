---
layout: post
title: Coding Problems
---

```
// https://dev.to/awwsmm/java-daily-coding-problem-001-59pg
/*Problem:
 * Given a list of numbers and a number k, return whether any two numbers from the list add up to k.
 * For example, given [10, 15, 3, 7] and k of 17, return true since 10 + 7 is 17.
 * */
package Day1;

public class Problem1 {
	
	static int[] given = {10, 3, 5, 7};
	static int len = given.length;
	
	public static boolean solution(int[] array, int k) {
		for(int outer=  0; outer < (len - 1); ++outer) {
			for(int inner = outer + 1; inner < len; ++inner) {
				if(given[outer] + given[inner] == k) {
					return true;
				}
			}
		}
		return false;
	}
	
	public static void main(String[] args) {
		System.out.println(solution(given, 17));
	}
	
}

```

---

```
package test.syn;

public class ClassA {

	public static void main(String[] args) {
		
		System.out.println("Hello");

	}

}


package test.syn;

public class ClassB extends ClassA {

	public static void main(String[] args) {
		
		System.out.println("Hi");
		
	}

}

```

```
package test.syn;

public class ThreadTest {
	
	public synchronized static void test1() {
		System.out.println("hello");
	}
	
	public synchronized void test2() {
		System.out.println("HI");
	}
	
	public static void main(String[] args) throws InterruptedException {
		ThreadTest test = new ThreadTest();
		
		Thread t1 = new Thread() {
			public void run() {
				test.test1();
			}
		};
		
		Thread t2 = new Thread() {
			public void run() {
				test.test2();
			}
		};
		
		t1.start();
		Thread.sleep(500);
		t2.start();
		Thread.sleep(500);
		System.out.println(t2.getState());
		
	}

}

```

```
package test.syn;

public class Employee {
	
	@Override
	public boolean equals(Object o) {
		return super.equals(o);
	}
	
	public int hashCode() {
		return super.hashCode();
	}

}


package test.syn;

import java.util.HashMap;
import java.util.Map;

public class EmployeeMap {

	public static void main(String[] args) {
		
		Employee e1 = new Employee();
		Employee e2 = new Employee();
		Employee e3 = new Employee();
		Employee e4 = new Employee();
		
		
		System.out.println(e1.equals(e2));
		System.out.println(e1.equals(e3));
		System.out.println(e1.equals(e4));
		
		System.out.println(e1.hashCode());
		System.out.println(e2.hashCode());
		System.out.println(e3.hashCode());
		System.out.println(e4.hashCode());
		
		Map<Employee, String> map = new HashMap<>();
		map.put(e1, "emp1");
		map.put(e2, "emp2");
		map.put(e3, "emp3");
		map.put(e4, "emp4");
		
		System.out.println(map.get(e1));
		System.out.println(map.get(e2));
		System.out.println(map.get(e3));
		System.out.println(map.get(e4));
		
		/*Map<Integer, String> map = new HashMap<>();
		map.put(1, "one");
		map.put(2, "two");
		map.put(3, "three");
		map.put(4, "four");
		
		System.out.println(map.get(1));
		System.out.println(map.get(2));
		System.out.println(map.get(3));
		System.out.println(map.get(4));*/
		
	}

}


```
