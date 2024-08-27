# Multithreading:

## 01. Defining Thread class




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
* 
