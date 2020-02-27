---
layout: post
title: Custom HashMap
---

import java.util.Arrays;

/**
 * 
 * @author Deepika Anand
 * 	
 * @param CustomHashMap contains array enteries. Such that each element of enteries (say entry) contains a list of key, value pairs
 * enteries : index1 : (k1, v1) -> (k2, v2)
 * 			  index2 : (k3, v3) -> (k4, v4)
 * 			  index5 : (k5, v5) -> (k6, v6)
 * 
 * @param pSize : Maintains the total size set at the time of initialization
 * @param currentItems : Maintains number of current items in the hashMap
 * 
 * hashcode() : Standard Java function to get hashcode for a string
 * The returned integer value is used to take modulus with pSize such that index value is bounded between 0 to pSize - 1  
 */

public class CustomHashMap<T> {
	Entry<T>[] enteries;
	int pSize;
	int currentItems;
	
	/**
	 * Constructor used to get the initial size also to initialize enteries array which in turn will contains key value pairs
	 * @param size
	 */
	public CustomHashMap(final int size) {
		pSize = size;
		enteries = new Entry[size];
		currentItems = 0;
	}	
	
	/**
	 * 
	 * @param key of String format as given in the probem statement
	 * @param value could be any object as given in the problem statement
	 * @return true: to show successful addition of element in the custom hash map
	 * 
	 * COMPLEXITY ANALYSIS
	 * STEP 1 : Getting a hashCode = O(1)
	 * STEP 2 : Find Index given the hashcode and fixed size of the hashmap = O(1)
	 * STEP 3 : If no list is present for this key in the enteries than insertion is O(1)
	 * STEP 4 : If the hash code matches than look for request key in link list of the form (k, v) no since the hascode distributes our 
	 * 			values uniformly so we can argue that on average the insertion cost will be O(1) it would have been O(n) had the hascode not been 
	 * 			uniformly distributed.
	 * 			Hence complexity : theta(n) and O(n)
	 * 
	 * Extra Step : As soon as the required key is inserted, increment the count of currentItems : O(1)
	 * 
	 * Total avergae case complexity = theta(1)
	 * 
	 */
	public boolean set(String key, T value ) {
		
		/**
		 * Step 1: Get the index of enteries table where this hashcode belongs to
		 */
		int hashCode = key.hashCode(); //O(1)
		int index = hashCode % this.pSize; //O(1) 
		
		// If no list of enteries present at index, then create a new Entry and increment currentItems O(1)
		if (enteries[index] == null) { 
			enteries[index] = new Entry<T>(key, value, null);
			currentItems++;
			return true;
		}  
		//Otherwise traverse the current list sarting from 'index' where hashcode matched, if their is some key
		//equal to input key then already present in entry for that hashcode than just replace the value. 
		//Else create a new Entry ad adjust next pointer of link list. 
		//Complexity on average will be O(1) since hashcode will unofrmly distribute the value or else O(n) in worst case
		else {
			Entry<T> entry = enteries[index];
			for ( ; entry.next != null; entry = entry.next) {
				if (entry.key.equals(key)) { //Replace scenario
					T prevVal = (T) entry.value;
					entry.value = value;
					return true;
				}
			}
			//If reached here. It means unique key seen first time - O(1)
			entry.next = new Entry<T>(key, value, null);
			currentItems++;
			return true;
		}
	}
	
	/**
	 * @param key of String format as given in the probem statement
	 * @return the value could be any object corresponding to String key submitted
	 * 
	 * COMPLEXITY ANALYSIS : 
	 *  STEP 1 : Getting a hashCode = O(1)
	 *  STEP 2 : Find Index given the hashcode and fixed size of the hashmap = O(1)
	 *  STEP 3 : starting from the index where hashcode of the input key and hashcode stored matches than start searching from  
	 *  		 link list stored at index. Since the hashcode is uniformaly distributed than we can say that on avergae it will take 
	 *  		 constant time but in really worst case it will order of n
	 *  		 Hence complexity : theta(n) and O(n)
	 *  
	 *  Total avergae case complexity = theta(1)
	 */
	public T get(String key) {
		/**
		 * Step 1: Get the index of enteries table where this hashcode belongs to O(1)
		 */
		int hashCode = key.hashCode();
		
		/**
		 * Step 2 : Find the corresponding index in the enteries array given the hashcode O(1)
		 */
		int index = hashCode % this.pSize;  
		
		/**
		 * Step 3: Now starting from the index value traverse the corresponding link list which is in the form of key value pair 
		 * and find the key such that it is equal to input key.
		 * If no such key is present than return null
		 * 
		 * O(1) operation on an average and O(n) on worst case scenario if all the keys match to the same hashcode
		 * but since we argue that hashcode is uniformly distributed so the complexity will be O(1) on average
		 */
		Entry<T> startPoint = enteries[index];
		Entry<T> entry = startPoint;
		for ( ; entry != null; entry = entry.next) {
			if (entry.key.equals(key)) {
				return entry.value;
			}
		}
		return null; 
	}
	
	/**
	 * 
	 * @param key
	 * @return the value of the key which is deleted. In case no such key is present then returns null
	 * 
	 * COMPLEXITY ANALYSIS : 
	 *  STEP 1 : Getting a hashCode = O(1)
	 *  STEP 2 : Find Index given the hashcode and fixed size of the hashmap = O(1)
	 *  STEP 3 : Starting from Index as found in step 2 search the link list to find the exact (k, v) pair to be deleted.
	 *  	     No, for worst case it will take time propertional to 'n' but since the hascode will distribute the keys  
	 * 			 uniformly therefore we can say that on an average time taken will be constant
	 * 			 Hence complexity : theta(n) and O(n)
	 * 
	 *  Extra Step : As soon as the required key is found decrement the count of currentItems : O(1)
	 *  
	 *  Total avergae case complexity = theta(1)         
	 */
	public T delete(String key) {
		
		/**
		 * Step 1: Get the index of enteries table where this hashcode belongs to O(1)
		 */
		int hashCode = key.hashCode();
		
		/**
		 * Step 2 : Find the corresponding index in the enteries array given the hashcode O(1)
		 */
		int index = hashCode % this.pSize;  //The k, v pair for this hashcode will be at 'index' of enteries array
		Entry<T> currentPoint = enteries[index];
		Entry<T> prevPoint = null; // Keep a previous pointer becuase if match is found currentPoint will be deleted 
								   // so prevPoint will now point next of current pointer
		
		/**
		 * STEP 3 : If the entry to be deleted is present than adjust the required pointers. Return null if that key is not present
		 */
		while( currentPoint != null ) {
			if (currentPoint.key.equals(key)) {
				currentItems--;
				T prevValue = currentPoint.value;
				
				if (prevPoint == null) { // If this was the only entry than just set entry at index to point to null. No adjustment of 
										 // pointer is required.
					enteries[index] = null;
				} else {
					//Adjust pointers depending the to be deleted (k,v) pair was last in the link list or it has further elements.
					prevPoint.next = currentPoint.next == null ? null :  currentPoint.next.next; 
				}
				return prevValue;
			} else {
				prevPoint = currentPoint;
				currentPoint = currentPoint.next;
			}
		}
		return null;
	}
	
	/**
	 * 
	 * @return Current load in the hashmap: float value O(1)
	 * COMPLEXITY ANALYSIS : 
	 * 		Divide currentItems by the current size but take care of divide by zero exception by adding additional check.
	 */
	public float load() {
		if (this.pSize == 0) {
			return 0f;
		}
		return (float)this.currentItems/this.pSize;
	}
	
	@Override
	public String toString() {
		return "CustomHashMap [enteries=" + Arrays.toString(enteries)
				+ ", pSize=" + pSize + ", currentItems=" + currentItems + "]";
	}
	
	public static void main(String[] args) {
		CustomHashMap<Integer> myMap = new CustomHashMap<>(8);
		myMap.set("one", new Integer(1));
		myMap.set("two", new Integer(2));
		myMap.set("three", new Integer(3));
		myMap.set("four", new Integer(4));
		System.out.println("*****************MAP DATA AFTER INSERTION DATA*****************");
		System.out.println(myMap);
		System.out.println("#################LOAD FACTOR AFTER INSERTION#################");
		System.out.println(myMap.load());
		System.out.println("\n");
		
		System.out.println("==================STARTING GET OPEARTIONS==================");
		System.out.println("Value for key = three is " + myMap.get("three")) ;
		System.out.println("Value for key = five is  " + myMap.get("five") + " (since it was not present in the map) ") ;
		
		System.out.println("\n");
		System.out.println("=================STARTING DELETE OPEARTIONS=================");
		System.out.println("Deleted key = three has value = " + myMap.delete("three"));
		System.out.println("*****************MAP DATA AFTER FIRST DELETION*******************");
		System.out.println(myMap);
		System.out.println("#################LOAD FACTOR AFTER FIRST DELETION#################");
		System.out.println(myMap.load());
		
		System.out.println("\n");
		System.out.println("Deleted key = five has value = " + myMap.delete("five") + " (since it was not present in hashmap)");
		System.out.println("*****************MAP DATA AFTER SECOND DELETION*******************");
		System.out.println(myMap);
		System.out.println("#################LOAD FACTOR AFTER SECOND DELETION#################");
		System.out.println(myMap.load());
		System.out.println("NOTE: The load factor remains same after first and second " + 
		"deletion becuase the key sent second time was not found in hashmap");
		
	}
}

/**
 * Helper class 
 * This block is used to form enteries array.
 * Each entry contains key, value and pointer to next entry.
 *
 * @param <T>
 */
class Entry<T> {
	String key;
	T value;
	Entry<T> next;
	
	public Entry(String key, T value, Entry<T> next) {
		this.key = key;
		this.value = value;
		this.next = next;
	}

	@Override
	public String toString() {
		return "Entry [key=" + key + ", value=" + value + ", next=" + next
				+ "]";
	}
}
