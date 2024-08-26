# OOPS:
  ## 1. Class
  ## 2. Object
  ## 3. Data hiding
  ## 4. Abstraction
  ## 5. Encapsulation
  ## 6. Is-A Relationship
  ## 7. Has-A Relationship
  ## 8. Method Signature
  ## 9. Method Overloading
  ## 10. Method Overrriding
  ## 11. Static Control Flow 
  **Static Control Flow in Parent-Child Relationship**
  ## 12. Instance Control Flow
  **Instance Control Flow in Parent-Child Relationship**
  ## 14. TypeCasting
  **Widening(auto) & Narrowing(explicitly)**
  ## 15. Coupling

## 1. Class:

**A logical representation of Object is nothing but Class**
**EX:**
```
class Student {
int id;
String name;
}
```

## 2. Object:

**1. An instance of class is nothing but an object.**
**2. If we have a class, we can create any number of objects for that class based on our requirement.**

**Ex:**
```
class Student {
int id;
String name;
Student(int sid, String sname) {
id=sid;
name=sname;
}
}

class Test {
public static void main(String[] args) {
Student s1=new Student(101, "Padma");
Student s2=new Student(102, "Java");
System.out.println(s1.id + "...." + s1.name);
System.out.println(s2.id + "...." + s2.name);
}
}
```

## 3. Data Hiding:

**1. Data hiding is the process of hiding the data from the direct access.**
**2. By this we can achieve security.**
**3. By using private modifier we can achieve data hiding.**

**Ex:**
```
class Account{
    private double balance;
    public double getbalance(){
        return balance;
    }
    
}

class Test{
    public static void main(String[] args){
        Account a=new Account();
        System.out.println(a.balance); //CE: balance has private access in account 
        System.out.println(a.getbalance()); //0.0
    }
}
```

## 4. Abstraction:

**1.The process of Highlighting the required services by hiding the implementaion is called Abstraction.**
**2. By using abstract classes and references , we can achieve Abstraction.**
**3. We can achieve security as we are not highlighting the internal implementation.**
**4. Enhancement will be increased**
**5. Changes or any other big corrections is very easy that can be done in any other side.**
**6. Modularity and maintainability of the application.**
**7. They will give only services not the implementation part.**
**8. They will give method like getFlights(), this is nothing but a service only.**


## 5. Encapsulation:

**1. Binding the data together with its related methods is the concept of Encapsulation.**

```
class Product{
    private int id;
    private String name;
    public void setId(int id){
        this.id=id;
    }
    public int getId(){
        return id;
    }
    public void setName(String name){
        this.name=name;
    }
    public String getName(){
        return name;
    }
}
```
### Tightly Encapsulated:

**If every instance of the class is declared by using private modifier then that class is tightly encapsulated.**
**If parent class is not tightly encapsulated, then no child class is tightly encapsulated.**

## 6. Is-A Relationship:

**1. This is also known as Inheritance.**
**2. By using extends keyword we can derive inheritance. (Inheritance is nothing but, Parent[superclass] - Child[subclass] relationship)**
**3. The main advantage of Is-A Relationship is code-reusability.**

**Ex: Dog is an Animal.**

```
class Animal{
    String name;
    
    void eat(){
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal{
    void bark(){
        System.out.println("This dog barks");
    }
    void eat(){
        System.out.println("This dog eats bones");
    }
}

class Test{
    public static void main(String[] args){
        Dog d=new Dog();
        d.name="charlie";
        System.out.println("dogs name is: " + d.name);
        
        d.bark();
        
        d.eat();
    }
}
```
**4. We can user parent refernce to represent child object.**
**5. By using this reference we can invoke only parent methods and can't invoke child specific methods.**
**6. So we have to place the most common methods in the parent class only, place the specifics in child methods.**
**hi**

## 7. Has-A Relationship:

**1. This is also known as composition and agreegation.**
**2. there is no specific keyword to define Has-A Relationship, but we can use new keyword to create the dependend object.**
**3. The main advantage of Has-A Relationship is code-reusability.**

**Ex: Car has a Engine.**

```
class car {
    Engine e;
    car(Engine e) {
        this.e=e;
    }
public void move(){
    e.start();
        System.out.println("Car is moving...");
    }
}

class Engine{
    public void start(){
        System.out.println("Engine started");
    }
}

class Test{
    public static void main(String[] args){
        Engine e=new Engine();
        car c=new car(e);
        c.move();
    }
}
```

## 8. Method Signature:

**1. Method signature in java consists Mathod's name and parameter lists(arguments passed).**
**2. Method signature uniquely identifies the method within a class.**
**3. We can create different methods with same method name , but different parameter types arguments, so java compiler can easily identify which method we have to call now like.**

```
class Calculator{
    //Method signature: add(int, int)
    public int add(int a, int b){
        return a+b;
    }
    //Method signature: double(double, double)
    public double add(double a, double b){
        return a+b;
    }
}

class Test {
    public static void main(String[] args){
        Calculator calc=new Calculator();
        System.out.println(calc.add(10,5)); //15  calls add(int, int)
        System.out.println(calc.add(5.2,7.5)); //12.7  calls add(double, double)
    }
}
```

**here, add(int a, int b) and add(duoble a, double b) have the same method name, but different parameters.**

## 9. Method Overloading:

**1. In java we can declare 2 or more methods with same method name, but different parameter lists, such type of methods are called as Overloaded Methods, and this concept is called as Method Overloading.**

**Ex: 01**
```
class Test{
    public static void m1(int a){
        System.out.println("int-arg");
    }
    public static void m1(float f){
        System.out.println("float-arg");
    }
    
    public static void main(String[] args){
        m1(10); // int-arg
     //  m1(25.54); //no suitable method found for m1(double)
        m1(2.5f); //float-arg
        m1('a'); //int-arg
    //  m1(true); //no suitable method found for m1(boolean)
    }
}
```

**Ex:02 **

```
class Test{
    public static void m1(int a, float b){
        System.out.println("int-float");
    }
    public static void m1(float a, int b){
        System.out.println("float-int");
    }
    
    public static void main(String[] args){
        m1(10, 5.2f); //int-float
     // m1(25.54, 65.21); //no suitable found for m1(double, double)
        m1(2.5f, 5); //float-int
    //  m1(10, 10); //no suitable method found for m1(int, int)
    }
}
```

**Ex:03**

```
class Test{
    public void m1(String s){
        System.out.println("String-arg");
    }
    public void m1(Object O){
        System.out.println("Object-arg");
    }
    
    public static void main(String[] args){
       Test t=new Test();
       t.m1(new String()); // or t.m1("Padma"); //String-arg
       t.m1(new Object()); //Object-arg
       t.m1(null); //String-arg
    }
}
```

**Ex:04**

```
class Test{
    public void m1(String s){
        System.out.println("String-arg");
    }
    public void m1(Thread t){
        System.out.println("Thread-arg");
    }
    public void m1(Object O){
        System.out.println("Object-arg");
    }
    
    
    public static void main(String[] args){
       Test t=new Test();
       t.m1(new String());  //String-arg
       t.m1(new Object());  //Object-arg
       t.m1(new Thread());  //Thread-arg
       
    }
}
```

**Ex:05**

```
class Person {
    
}
class Student extends Person {
    
}
class Test {
    public static void m1(Person p){
        System.out.println("Person");
    }
    public static void m1(Student s){
        System.out.println("Student");
    }

public static void main(String[] args){
    Person p=new Person();
    m1(p);
    Student s=new Student();
    m1(s);
    Person p2=new Person();
    m1(p2);
}
}
```

## Polymorphism:
**1. Polymorphism in java allows objects of different classes to be treated as objects of a common Parent class.**
**2. A single function can behave differently based on the objects.**

### Types of Polymorphism:
**1. Compile-time Polymorphism**
   **Method Overloading is called as Static Polymorphism or Compile-time Polymorphism in early binding.**
   **Method Overloading is a reference type Polymorphism.**
   **In Overloading method resolution is take and care by java compiler based on reference type.**


## 10. Method Overriding:

**1. Throught Is-A Relationship whatever Parent class has (properties, behaviors) are by defuault available to the child class.**
**2. If child is not satisfied with parent behavior, then child can change that behavior by using Method Overriding.**

**Ex:01**
```
class P{
    public void gotJob(){
        System.out.println("Achieved");
    }
    public void MakeHappyMom(){
        System.out.println("Love you mummy");
    }
}

class C extends P {
    public void MakeHappyMom(){
        System.out.println("Kavima");
    }
    }
    
class Test{
    public static void main(String[] args){
        P p=new P();
        p.gotJob(); //Achieved
        p.MakeHappyMom(); //Love you mummy
        
        C c=new C();
        c.gotJob(); //Achieved
        c.MakeHappyMom(); //Kavima
        
        P p2=new P();
        p2.gotJob(); //Achieved
        p2.MakeHappyMom(); //Love you mummy
        
    }
}
```

**Method Overriding is dependent on Object not reference.**
**In Method Overriding , method resolution take and care by JVM based on the runtime objects.**
**Hence it is called as Dynamic Polymorphism, and run-time Polymorphism in late binding.**

**If any method's behavior, if we wants to change, we can change only through "Method Overriding".**

## 11. Static Control Flow:

**Whenever we are executing java class, the balance sequence of steps will be performed automatically.**
**Identification of all static memebers from parent to child and top to bottom.**
**Execution of all static variable assignments and static blocks from parent to child and top to bottom only.**
**Execution of main method.**

**Ex:01**

```class Test {
    static int x=10;
    static {
        System.out.println("FSB");
        m1();
    }
    public static void main(String[] args){
        m1();
        System.out.println("Main method");
    }
    public static void m1(){
        System.out.println(y);
        
    }
    static {
        System.out.println("SSB");
    }
    static int y=20;
}

output: FSB
        0
        SSB
        20
        main method

```
**here, first static class blocks only will be executed first, then only main class will be executed.**

**Ex:02**
```
class Test{
    static int x=10;
    static {
        System.out.println(x);
    }
    public static void main(String[] args){
        
    }
}

output: 10
```

**Ex:03**
```
class Test{
    static {
        System.out.println(x);
    }
    public static void main(String[] args){
        
    }
        static int x=10;
}
output: Illegal forward reference
```

**Ex:04**
```class Test{
    static {
        m1();
    }
    public static void main (String[] args) {
        
    }
    public static void m1(){
        System.out.println(x);
    }
    static int x=10;
}

output: 0
```


### Static Control Flow in Parent-Child Relationship

**Whenever we are executing the child class, the below sequence of steps will be performed automatically.**
**Execution of child class main method only.**

**Ex:01**

```
class P{
    static int x=10;
    static {
        m1();
        System.out.println("PFSB");
    }
    public static void main(String[] args){
        m1();
       System.out.println("parent-main");
    }
    
    public static void m1(){
        System.out.println(y);
    }
    static {
        System.out.println("PSSB");
    }
    static int y=20;
}
    
class C extends P{
        static int a=100;
        static {
            m2();
            System.out.println("CFSB");
        }
        public static void main(String[] args){
            m2();
            System.out.println("Child-main");
        }
        public static void m2(){
            System.out.println(b);
        }
        static {
            System.out.println("CSSB");
        }
        static int b=200;
    }

output: while Parent.java:
        0
        PFSB
        PSSB
        20
        parent-main

        while Child.java:
        0
        PFSB
        PSSB
        0
        CFSB
        CSSB
        200
        Child-main
```

**Whenever we are loading parent class, child class won't be loaded automatically.**
**But whenever we are loading child class, parent class will be loaded automatically, but won't execute or load the parent main method or class.**

## 12. Instance Control Flow:

**Always associated with objects only.**
**We cannot access non-static methods directly from static area.**
**Whenever we are creating objects for a class, the balance sequence of steps will be performed automatically.**
**Identification of instance members from top to bottom only.**
**Execution of instance veriable assignments and instance blocks from top to bottom only.**
**Execution of corresponding constructors.**

**Ex:01**

```
class Parent{
    int i=10;
    {
        m1();
        System.out.println("PFIB");
    }
    Parent(){
        System.out.println("Parent-class");
    }
    public static void main(String[] args){
         Parent p=new Parent();
         System.out.println("Parent-main");
         p.m1();
    }
    public void m1(){
        System.out.println(j);
    }
    {
    System.out.println("PSIB");
}
    int j=20;
}

output: while Parent.java
         0
         PFIB
         PSIB
         parent-class
         parent-main
         20
```

### Instance control flow in Parent-Child class Relationship:

**Ex:02**

```
class Parent{
    int i=10;
    {
        m1();
        System.out.println("PFIB");
    }
    Parent(){
        System.out.println("Parent-class");
    }
    public static void main(String[] args){
         Parent p=new Parent();
         System.out.println("Parent-main");
         p.m1();
    }
    public void m1(){
        System.out.println(j);
    }
    {
    System.out.println("PSIB");
}
    int j=20;
}

class Child extends Parent{
    int a=100;
    {
        m2();
        System.out.println("CFIB");
    }
    Child(){
        System.out.println("Child-class");
    }
    public static void main(String[] args){
        Child c=new Child();
        System.out.println("Child-main");
        c.m2();
    }
    public void m2(){
        System.out.println(b);
    }
    {
        System.out.println("CSIB");
    }
    int b=200;
}

output: While Parent.java
        0
        PFIB
        PSIB
        Parent class
        parent-main
        20

        While Child.java
        0
        PFIB
        PSIB
        Parent class
        0
        CFIB
        CSIB
        child class
        child-main
        200
```

**Whenever we are loading parent class, child class won't be loaded automatically.**
**But whenever we are loading child class, parent class will be loaded automatically, but won't execute or load the parent main method or class.**

## Singleton Class:

**For any java class, if we are allowed to create almost only one object, such type of class is called as "Singleton Class".**

**Ex:01**

```
class Test{
    public static void main(String[] args){
        Runtime r1=Runtime.getRuntime();
        Runtime r2=Runtime.getRuntime();
        System.out.println(r1==r2);
        System.out.println(r1.hashCode());
        System.out.println(r2.hashCode());
    }
}

output:
      true
      1608446010
      1608446010
```

## 14. TypeCasting:

**Typecasting in java is the process of converting a variable from one data type to another data type.**

**There are two main types of typecasting is available in java:**

   **1. Widening(Automatically):**
       **Converting a smaller data type to larger datatype. This happens automatically by the compiler without any explicit action by the programmer.**

**Ex for Widening:**
```
class widening{
    public static void main(String[] args){
        int intVal=10;
        double int_to_double = intVal;
        
        System.out.println("Integer value: " + intVal); // Integer value: 10
        System.out.println("Double value: " + int_to_double); // Double value: 10.0
    }
}
```

   **2. Narrowing(Explicitly):**
        **Converting a larger data type to smaller data type. This requires explicit action by the programmer. Because there is a risk of losing data.**

**Ex for NarrowingL**
```
class widening{
    public static void main(String[] args){
        double val=25.25;
        int double_to_int = (int) val;
        
        System.out.println("Double value: " + val); // Double value: 25.25
        System.out.println("Integer value: " + double_to_int); // double_to_int: 25
    }
}
```

## 15. Coupling:

**There are two types of coupling is available in java:**
    **1. Tightly Coupling:**
