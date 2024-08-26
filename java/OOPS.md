# OOPS:
  ## 1. Class
  ## 2. Object
  ## 3. Data hiding

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
