# OOPS:
  ## 1. Class
  ## 2. Object
  ## 3. Data hiding
  ## 4. Abstraction
  ## 5. Encapsulation
  ## 6. Is-A Relationship

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

**Ex:**

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
