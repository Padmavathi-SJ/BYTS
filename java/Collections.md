  # Collection Framework
      
  ## Array
  ## Collection(I)
  ## List(I)
  ## ArrayList(I)

  ## Array:
  
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
    
