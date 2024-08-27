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
