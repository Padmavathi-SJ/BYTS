# Multithreading:

## 01. Defining Thread class
## join()
## sleep()
## Inter-Thread Communication



## Defining Thread class:

* We can define a thread in 2 ways.
      1. By extending Thread class.
      2. By impleenting runnable interface.

### Extending a Thread class:

**Ex:**
```
class AT extends Thread {
    public void run(){
        for(int i=1; i<=3; i++){
            System.out.println("Anushka Thread: " + Thread.currentThread().getName());
        }
    }
}

class ST extends Thread {
    public void run() {
        for(int i=1; i<=3; i++){
            System.out.println("Shruthi Thread: " + Thread.currentThread().getName());
    }
}
}

class Test{
    public static void main(String[] args){
        AT at=new AT();
        at.start();
        ST st=new ST();
        st.start();
        for(int i=1; i<=3; i++){
            System.out.println("Main Thread: " + Thread.currentThread().getName());
        }
    }
}
```
* here, we cannot expect the exact output, because multiple threads are running at the same time or simultaneously.

### By implementing Runnable Interfaces:

**Ex:**

```
class SrikanthThread implements Runnable {
    public void run() {
        for(int i=1; i<=4; i++){
            System.out.println("Shruthi thread: " + Thread.currentThread().getName());
        }
    }
}

class Test {
    public static void main(String[] args){
     Runnable r=new SrikanthThread();
     Thread t=new Thread(r);
     t.start();
     for(int i=1; i<=4; i++){
         System.out.println("Main Thread: " + Thread.currentThread().getName());
     }
    }
}
```
* Here also we cannot expect the axact output.


## join():

* If a Thread wants to wait untill the completion of some other particular thread execution, we go for join() method.

```
public void join() throws InterruptedException
public void join(long ms) throws InterruptedException
public void join(long ms int ns) throws InterruptedException
```
**Ex:**

```
class ST extends Thread {
    public void run() {
        for(int i=1; i<=4; i++){
            System.out.println("Child Thread");
        }
        try {
            Thread.sleep(2000);
        }
        catch(InterruptedException e){
            
        }
    }
}

class Test {
    public static void main(String[] args) throws InterruptedException{
        Thread t=new ST();
        t.start();
        t.join();
        for(int i=1; i<=4; i++){
            System.out.println("Main Thread");
        }
    }
}
```

* here, in the above program child class execution will be completed first as the main thread is calling join() method on child thread object.


## sleep():

* If a thread does not want to perform any task for a particular amount of time, we should go for sleep() method.

```
public static void sleep(long ms) throws InterruptedException
public static void sleep(long ms, int ns) throws InterruptedException
```


## Inter-Thread Communication:

* Two threads can communicate with each other by using wait() and notify() methdos.
* A thread , which is expection updates from another thread has to call "wait()" method and enter into waiting state.
* A thread, which is giving updates informations has to call "notify()" and "notifyAll()" method, so that waiting thread will get the notification and continues its executions by taking those updates.
  
