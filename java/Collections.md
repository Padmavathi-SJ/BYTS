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


