  # Collection Framework
      
  ## Array
  ## Collection(I)
  ## List(I)
  ## ArrayList(I)
  ## LinkedList(I)
  ## Vector(I)
  ## Stack
  ## Set(I)
  ## HashSet
  ## LinkedHashSet
  ## SortedSet
  ## TreeSet
  ## Map(I)
  ## HashMap(I)
  ## LinkedHashMap
  ## SortedMap(I)
  ## TreeMap
  

### Array:
  
  * An array is index based based homogeneous data elements of fixed size.
  * All arrays are objects in java.
  * The main advantage of array is, we can represent multiple valuse by using a single variable, so that readability will be improved.
  * The main disadvantage is array is fixed in size, so we cannot increase or decrease based on our runtime requirement.

### Limitations of object type arrays:

* Arrays are not growable in nature.
* By using arrays we can represent only homogeneous data elements. we cannot represent heterogeneous data elements.
* Arrays are not implemented by using data structure. Hence for every requirement programmer only need to write the logic. so complexity will be increased.

**To overcome these limitations, we got to a concept called "Collections".**

* Collections are auto growable in nature.
* By using collections, we represent homogeneous and heterogeneous data elements.
* Collections are internally implemented by data structures, so we can expect ready made support.
* If we wants to represent a group of individual objects as a single onject, we got ot a concept called "Collection object".


## Collections:

* If we wants to represent a group of individual objects as a single onject, we got ot a concept called "Collection object".
* Collections interfacs acts as a parent for all collection classe.

  ### Important methods:
     * add(Object obj)
     * addAll(Collection c)
     * remove(Object obj)
     * removeAll(Collection c)
     * retainAll(Collection c)
     * contains(Object obj)
     * containsAll(Collection c)
     * clear()
     * isEmpty()
     * size()
     * Object[] toArray[]
     * Iterator iterator()
       
* There is no class which directly implements collection interface.
* There is no getter method to retrieve an object from the Collection from Collection Inetrface.


## List(Interface):

* If we wants to represent a group of individual objects as a single object, where "duplicates" are allowed, and insertion order must be "preserved" we should go to that concept called "List".

### Important methods
    * add(int index, Object obj)
    * addAll(int index, Collection c)
    * remove(int index)
    * get(int index)
    * set(int index, Object newObject)
    * IndexOf(Object obj)
    * LastIndexOf(Object obj)
    * ListIterator listIterator()


## ArrayList(I):

* Underlying data struture is autogrowable array or Resizable array or Dynamic array.
* Duplicates are allowed.
* Insertion order will be preserved.
* Heterogeneous elements are allowed. (only in TreeMap & TreeSet concepts heterogeneous elements are not allowed)
* Null insertion is possible

### Constructors:
```
ArrayList l=new ArrayList();
or
List l=new ArrayList();
```

* the above code will create an empty array list with "default initial capacity 10". by the following formula.
  ```
  newCapacity=oldCapacity + (oldCapacity >> 1);
  ```
```
ArrayList l=new ArrayList(int initialCapacity);

Ex:
ArrayList l=new ArrayList(1000);
ArrayList l=new ArrayList(Collection c);
```

**Ex:**
```
import java.util.*;

class Test{
    public static void main(String[] args){
        List l = new ArrayList();
        
        l.add("Padmavathi"); 
        l.add(5);
        l.add("Kavitha");
        l.add(true);
        l.add(2);
        l.add("Mummy");
        l.add(null);
        
        System.out.println(l); //[Padmavathi, 5, Kavitha, true, 2, Mummy, null]
        
        l.remove(3);
        System.out.println(l);  //[Padmavathi, 5, Kavitha, 2, Mummy, null]
        
        l.remove(Integer.valueOf(3));
        System.out.println(l);  //[Padmavathi, 5, Kavitha, 2, Mummy, null]
    }
}
```

* Usually we use Collection concept to hold and transfer the data from one application to another application across network. To provide support for this requirement, every collection class implements "Serializable Interface".
* ArrayList class also implements "Cloneable Interface" , so that we can get "duplicate object creation capability" for our ArrayList class.
* ArrayList and Vector classes implements "Random Access" , so that we can retrieve any element "randomly" at the same retrivel time.

  **Ex:**
```
import java.util.*;
import java.util.RandomAccess;
import java.io.Serializable;

class Test{
    public static void main(String[] args){
        List l = new ArrayList();
        
        System.out.println(l instanceof Serializable); //true
        System.out.println(l instanceof Cloneable); //true
        System.out.println(l instanceof RandomAccess); //true
    }
}
```

* Every Collection class implements both Serializable and Cloneable Interfaces.
* But LinkedList does not implement RandomAccess.

**Ex:**

```
import java.util.*;
import java.util.RandomAccess;
import java.io.*;

class Test{
    public static void main(String[] args){
        List l = new LinkedList();
        
        System.out.println(l instanceof Serializable); //true
        System.out.println(l instanceof Cloneable); //true
        System.out.println(l instanceof RandomAccess); //false
    }
}
```
### Difference between ArrayList and Vecot:

### ArrayList:
* Methods present in ArrayList are not synchronized by default.
* Multiple thread are allowed to operate an object at the same time.
* So It is not thread safe.
* Relatively Performance is high.

### Vector:
* Methods present in Vector are Synchronized by default.
* Only one thread is allowed to operate an object at the same.
* So It is thread safe.
* Relatively performance is low.

* By default ArrayList is not thread safe, but we can get thread safe ArrayList by using "synchronizedList() method of Colliction utility class.

  ```
  List l=new ArrayList();
  List sl=new synchronizedList(l);
  ```

* Collection utility class also difines the below methods to get "thread-safe Set & Map".
  ```
  public static Set synchronizedSet(Set s);
  public static Map synchronizedMap(Map m);
  ```

  * mutable---> We can modify
  * immutable(unmodifiable)---> We cannot modify
 
  **Ex:**
```
  import java.util.*;
class Test{
    public static void main(String[] args){
        Set s=new HashSet();
        Map m=new HashMap();
    Set ss=Collections.unmodifiableSet(s);
    Map mm=Collections.unmodifiableMap(m);
    }
}
```
* We can make unmodifiable by using unmodifiable() method of Collection utility classes.

**Ex:**
```
import java.util.*;
class Test{
public static void main(String[] args){
List l=new ArrayList();
List ul=Collection.unmodifiableList(l);
}
}
```

* Collection utility classes can also defines below methods to make a Set and Map as unmodifiable.
* 
**Ex:**
  ```
  Set ss=Collections.unmodifiableSet(s);
  Map mm=Collections.unmodifiableMap(m);
  ```
* ArrayList is the best choice for our frequent requirement is "retrievel".
* ArrayList is the worst choice if our frequent requirement is addition or deletion of the particular objects at the beginning or middle. Becaulse, it requires many swap operations.


## LinkedList(I):

* Underlying data structure is "doubly LinkedList".
* Duplicates are allowd
* Heterogeneous elements are allowed.
* Insertion order will be preserved.
* Null insertion is possible.
* LinkedList does not implements "RandomAccess".
* LinkedList is the best choice for our frequent requirement is "addition or deletion".
* LinkedList is the worst choice for our frequent requirement is "Retrievel".

**Ex:**
```
LinkedList l=new LinkedList();
LinkedList l=new LinkedList(Collection c);
```
* Usually, LinkedList will be used to implement Stacks and Queues.

**Important Methods:**
  * addFirst(Object obj);
  * addLast(Object obj);
  * getFirst();
  * getLast();
  * removeFirst();
  * removeLast();
    
**Ex:**

```import java.util.*;
class Test{
    public static void main(String[] args){
        LinkedList l=new LinkedList();
       
       l.add("A");
       l.add(100);
       l.add("A");
       l.addFirst("S");
       l.add(10.5);
       l.addLast("P");
       System.out.println(l); //[S, A, 100, A, 10.5, P]
       
       l.removeFirst(); 
       System.out.println(l); //[A, 100, A, 10.5, P]
       
       l.removeLast();
       System.out.println(l); //[A, 100, A, 10.5]
       
    }
}
```


## Vector(I):

* Underlying data structure is growable array.
* Duplicates are allowed.
* Heterogeneous elements are allowed.
* Insertion order will be preserved.
* Null insertion is possible.
* The methods present in Vector are "syncgronized by default" so it is "thread-safe".

```
Vecctor v=new Vector();
```
* It creates an empty vector object with the default initial capacity 10. Once it reaches its maximum capacity, then it will be increased by using the below formula.

  ```
  newCapacity=oldCapacity * 2;
  ```

  ```
  Vector v=new Vector(int initialCapacity);
  Vector v=new Vector(int initialCapacity, int incrementalCapacity);
  Vectro v=new Vector(Collection c);
  ```
  ### Important Methods:
   * addElement(Object obj);
   * removeElement(Object obj);
   * removeElementAt(int index);
   * removeAllElements();
   * elementAt(int index);
   * firstElement();
   * lastElement();
   * int size();
   * boolean isEmpty();
   * enumeration elements();

```
import java.util.*;
class Test{
    public static void main(String[] args){
        Vector v=new Vector();
        System.out.println(v.capacity()); //10
       
       for(int i=0; i<10; i++){
           v.addElement(i);
       }
       System.out.println(v.capacity()); //10
       v.addElement("x");
       System.out.println(v.capacity()); //20 because newCapacity=oldCapacity*2 
       
       for(int i=11; i<22; i++){
           v.addElement(i);
       }
           
       System.out.println(v.capacity()); //40
       System.out.println(v); [1,2,3,4,5,6,7,8,9,x,11,12,13,14,15,16,17,18,19,20,21]
    }
}
```

### Stack:

*A special data structure for "FIRST IN LAST IN" purpose.

### Important Methods:
  * push(Object obj);
  * pop();
  * peek();
  * empty();
  * search(Object obj);

**Ex:**
```
import java.util.*;
class Test{
    public static void main(String[] args){
        Stack s=new Stack();
        
        System.out.println(s.empty()); //true
        
        s.push("S");
        s.push("P");
        s.push(100);
        s.push("A");
        
        System.out.println(s); //[S,P,100,A]
        System.out.println(s.search("P")); // 3
        System.out.println(s.search("X")); // -1
        System.out.println(s.peek()); // A
        System.out.println(s.empty()); false
    }
}
```

## Set(I):

* set is the child of Collection Interface.
* We cannot create objects for Interfaces and abstract classes.

* null in sorting --> null pointer exception
* We cannot sort heterogeneous elements, because we cannot compare those elements

## HashSet:

* Underlying data structure is hashtable.
* Duplicate elements are not allowed. If we try to add duplicate elements that add() method just returns false.
* Insertion order won't be preserved , because it is based on "hashcode" of the objects.
* Heterogeneous elementsare allowed.
* Null insertion is possible, but only once.

```
Hashset s=new HashSet(int initialCapacity);
HashSet s=new HashSet(int initialCapacity, float fillRatio);
HashSet s=new HashSet(Collection c);
```
* It creates an empty HashSet object with default initial capacity 16 and with fillRatio 0.75(must 0-1).

```
import java.util.*;
class Test{
    public static void main(String[] args){
        HashSet s=new HashSet();
        
        s.add("S");
        s.add(100);
        s.add("P");
        s.add(null);
        s.add(10.5);
        s.add(null); //null insertion is posibble but only once
        System.out.println(s.add("P")); // false, because duplicate element
        System.out.println(s); // [P, null, S, 100, 10.5] based on hashcode it alllocated in indies
}
}
```

## LinkedHashSet:

* LinkedHashSet is exactly same as Hashset except the below differences.
  
* In HashSet Data structure is hashtable, in LinkedHashSet , data structure is "LinkedList + hashTable".
* In hashSet insertion order is not preserved(based on hashcode), but in LinkedHashSet, insertion order is preserved.
  

**Ex:**
```
import java.util.*;
class Test{
    public static void main(String[] args){
        Set s=new LinkedHashSet();
        
        s.add("S");
        s.add(100);
        s.add("P");
        s.add(null);
        s.add(10.5);
        s.add(null); //null insertion is possible but only once.
        System.out.println(s.add("P")); // false, because duplicate elements are not allowed
        System.out.println(s); //[S, 100, P, null, 10.5]
}
}
```

## SortedSet(I):

* If we wants to represent a group a group of individual objects without duplicates according to some sorting order then we go to a concept called "SortedSet".
* heterogeneous elements are not allowed, because we cannot compare.
* duplicates are not allowed

### Important methods:
  * first();
  * last();
  * headSet(e); <e
  * tailSet(e); >=e
  * subSet(e1, e2); >=e1 & <e2

**Ex:**
```
import java.util.*;
class Test{
    public static void main(String[] args){
        SortedSet s=new TreeSet();
        
        s.add("S");
        s.add("A");
        s.add("S");
        s.add("D");
        s.add("T");
        s.add("X");
        //s.add(10); //ClassCaste E
        //s.add(null); //NullPointer E
        
        System.out.println(s); // [A, D, S, T, X]
        System.out.println(s.first()); // A
        System.out.println(s.last()); // X
        System.out.println(s.headSet("G")); // [A, D] because "<G"
        System.out.println(s.tailSet("S")); // [S, T, X] because ">=S"
        System.out.println(s.subSet("D", "X")); // [D, S, T] because '>=D' and '<X'
        System.out.println(s.comparator()); // null
}
}
```


## TreeSet:

* Data structure - balanced Tree.
* heterogeneous elements are not allowed , O/w--> CE: CCE
* duplicate are allowed.
* null insertion is not possible , O/W--> CE: NPE
* Insertion order won't preserved, based on sorting order.

  ```
  TreeSet s=new TreeSet();
  --->meant for Default Natural Sorting Order (DNSO)
  TreeSet s=new TreeSet(Comparator());
  ---> meant for custom sorting order (CSO)
  ```
**Ex:**
```
import java.util.*;
class Test{
    public static void main(String[] args){
        SortedSet s=new TreeSet();
        
        s.add(10);
        s.add(5);
        s.add(20);
        s.add(12);
        s.add(6);
        s.add(25);
        //s.add("S"); //CCE
        //s.add("P"); //CCE
        //s.add(null); //NPE
        
        System.out.println(s); // [5,6,10,12,20,25]
        
}
}
```


## Map(I):

* If we wants represent the objects in the form of "key-value" pairs, we got to c concept called "Map".
* Duplicates are not allowed for keys, but for values allowed.
* In map , each key-value pair is called as "Entry object". so the Map is nothing but a group of entries.
* Without existing Map Interface, there is no chance of existing Entry Interface , This is why java people declared the Entry Interface insidethe Map Interface.

  ```
  interface Map {
  ---
  ---
  ---
  interface Entry{
  getKey()
  getValue()
  setValue(Object newValue)
  }
  }
  ```

### Important Methods:
  * put(Object key, Object value) --> adds a new key-value pair if that key is not already present in map. O/W old value will be replaced by new value and returns the old value.
  * putAll(Map m)
  * get(Object obj)
  * remove(Object key)
  * containsKey(Object key)
  * containsValue(Object value)
  * isEmpty()
  * clear()
  * size()
  * set keySet()
  * set entrySet()
  * collection values()


## HashMap(I):

* Ds- hashtable.
* duplicate are not allowed for keys but for values allowed.
* Heterogeneous elements are allowed for both keys and values.
* Null insertion is possible for keys but only once, but for values no restrictions.
* Insertion order won't be preserved, based on hashcode of the objects.

```
HashMap m=new HashMap();
```
* Default initial capacity is  -16 and fillRatio is -0.75.

```
HashMap m=new HashMap(int initialCapacity);
HashMap m=new HashMap(int initialCapacity, float fillRatio);
HashMap m=new HashMap(Map m);
```

```
import java.util.*;
class Test{
    public static void main(String[] args){
        Map<String, Integer> m=new HashMap<>();
        
        m.put("Vijay", 100);
        m.put("Ajith", 400);
        m.put("Adharva", 200);
        m.put("Surya", 300);
        
        System.out.println(m.put("Ajith", 1000)); // 400
        
        System.out.println(m); // [Adharva=200, Surya=300, Ajith=400, Vijay=100]
        
        Set<String> keys=m.keySet();
        System.out.println(keys); // [Adharva, Surya, Ajith, Vijay]
        
        Collection<Integer> values=m.values();
        System.out.println(values); // [200,300,1000,100]
        
        Set <Map.Entry<String, Integer>> entries=m.entrySet();
        System.out.println(entries); // [Adharva=200, Surya=300, Ajith=1000, Vijay=100]
        
        Iterator <Map.Entry<String, Integer>> itr=entries.iterator();
        
        while(itr.hasNext()) {
            Map.Entry<String, Integer> e=itr.next();
            
            System.out.println(e.getKey() + "....." + e.getValue());
            // Adharva...200
            // Surya....300
            // Ajith....1000
            // Vijay....100
            
            if(e.getKey().equals("Surya")){
                e.setValue(700);
            }
        }
        
        System.out.println(m); // [Adharva=200, Surya=700, Ajith=1000, Vijay=100]
}
}
```

* HashMap(I) implements both serializable and clonable interfaces, but no implements RandomAccess.

### Difference between HashMap and HashTable:
### HashMap:
 * Methods present in HashMap not synchronized by default.
 * Multiple threads are allowed to operate an hashMap  object at the same time.
 * So this is not-thread safe.
 * Null insertion is possible.
 * comparing to Hashtable , performance is hight.

### HashTable:
 * Methods present in hashTable rae synchronized by default.
 * Only one thread is allowed to opearate hashTable object at the same time.
 * So this is thread-safe.
 * Comparing to HashMap , performance is low.
 * Null insertion is not possible for both keys and values.

* By default HashMap is not tyhread-safe, so we can get thread-safe HashMap by using "SynchronizedMap()" method of Collection utility classes.

```
public static Map synchronizedMap(Map m);
Map m=new HashMap();
Map sm=Collections.synchronizedMap(m);
```


## LinkedHashMap:

* LinkedHashMap is exactly same as HashSet except the following differences.
* Underlying data structrue is LInkedList + HashTable.
* In HashSet insertion order is not preserved.
* But in LinkedHashSet, insertion order is preserved.

**Ex:**
```
import java.util.*;

class Test{
    public static void main(String[] args){
        HashMap<String, Integer> m=new LinkedHashMap<>();
        
        m.put("Vijay", 100);
        m.put("Ajith", 400);
        m.put("Adharva", 200);
        m.put("Surya", 300);
        System.out.println(m);// [Vijay=100, Ajith=400, Adharva=200, Surya=300] because in LinkedHashMap insertion order is preserved.
    }
}
```

## SortedMap(I):

* If we wants to represent the objects in the form of key-value pairs according to some sorting order, we go to a concept called "SortedMap".
* Insertion order is preserved.

### Important Methdos:
  * firstKey();
  * lastKay();
  * headMap(Object obj);
  * tailMap(Object obj);
  * subMap(Object obj, Object obj);
  * comparator();

**Ex:**
```
import java.util.*;

class Test{
    public static void main(String[] args){
        SortedMap<String, Integer> m=new TreeMap<>();
        
        m.put("Vijay", 100);
        m.put("Ajith", 400);
        m.put("Adharva", 200);
        m.put("Surya", 300);
        m.put("Charan", 500);
        
        System.out.println(m); //[Adharva=200, Ajith=400, Charan=500, Surya=300, Vijay=100]
        System.out.println(m.firstKey()); //Adharva
        System.out.println(m.lastKey()); //Vijay
        System.out.println(m.headMap("Charan")); //[Adharav=200, Ajith=400] < Charan
        System.out.println(m.tailMap("Charan")); //[Charan=500 Surya=300, Vijay=100] >=Charan
        System.out.println(m.subMap("Adharva", "Charan")); //[Adharva=200, Ajith=400] >=Adharva < Charan
        System.out.println(m.comparator()); //null
        
    }
}
```

## TreeMap:

* Underlying data structrue is Red black Tree.
* duplicates are not allowed for keys, but for values allowed.
* Insertion order won't be preserved , it is based on sorting order of the keys.
* Heterogeneous elements are not allowed for keys, O/W we will get CCE, but for values allowed.
* Null insertion is not possible for keys, O/W we will get NPE, but for values allowed.

```
TreeMap tm=new TreeMap();
  ---> meant for "Default Natural Sorting Order", so keys must be homogeneous and comparable.
TreeMap tm=new TreeMap(comparator());
  ---> meant for"Custom Sorting Order", so keys need not be homogeneous and comparable.
```

**Ex:**

```
import java.util.*;

class Test{
    public static void main(String[] args){
        SortedMap<String, Integer> m=new TreeMap<>(new CC());
        
        m.put("Vijay", 100);
        m.put("Ajith", 400);
        m.put("Adharva", 200);
        m.put("Surya", 300);
        m.put("Charan", 500);
        
        System.out.println(m); // [Vijay=100, Surya=300, Charan=500, Ajith=400, Adharva=200]
    }
}

class CC implements Comparator<String> {
    public int compare(String s1, String s2) {
        return s2.compareTo(s1);
    }
}
```

## Hashtable:

* Underlying data structure is HashTable.
* Duplicates are not allowed fir keys, but for values allowed.
* Heterogeneous elements are allowed for both keys and values.
* Null insertion is not possible for both keys and values.
* Insertion order won't be preserved, it is based on hashCode of the keys.

```
HashTale h=new HashTable();
  --> It create an empty hashTable object with default initial capacity 11 and fillRation 0.75.
HashTable h=new HashTable(int initialCapacity);
HashTable h=new HashTable(int initialCapacity, float fillRatio);
HashTable h=new HashTable(h);
```

**Ex:**

```
import java.util.*;

class Test{
    public static void main(String[] args){
        Map m=new Hashtable();
        
        m.put("Vijay", 100);
        m.put(400, "Ajith");
        m.put("Adharva", 200);
        m.put(300, "Surya");
        m.put("Charan", 500);
        //m.put(null,"x"); //NPE
        
        System.out.println(m); //[Adharva=200, Charan=500, Vijay=100, 400=Ajith, 300=Surya]
    }
}
```
