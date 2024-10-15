### Locker Problem
* There is a school with 100 students, and correspondingly 100 lockers, all of which start off closed. The first student opens every locker. The second student closes every other locker, starting with the second (2, 4, 6 etc). The third student changes the state of every third locker starting with the third (3,6,9 etc). The fourth would change the status of lockers numbered 4,8,12 etc.,. That is, if the locker is open, it is closed, and if it is closed, it is opened. This continues until all 100 students have passed along the lockers. After the 100th student is done, which lockers are open and which are closed?
             [Note: program should work for any number of students/lockers]

```

Sample Input 1
100
Sample Output 1
open = 10
close = 90

///java

import java.util.*;
class Main{
    public static void main(String[] args){
        Scanner input=new Scanner(System.in);
        
        int n=input.nextInt();
        boolean[] lockers = new boolean[n+1];
        for(int student=1; student<=n; student++){
            for(int locker=student; locker<=n; locker += student){
                lockers[locker] = !lockers[locker];
            }
        }
        
        int openCount=0;
        int closeCount=0;
        for(int i=1; i<=n; i++){
            if(lockers[i]){
                openCount++;
            }
            else{
                closeCount++;
            }
        }
        
        System.out.printf("open: %d\n", openCount);
        System.out.printf("close: %d", closeCount);
        input.close();
    }
}

"""
100 //n
open: 10
close: 90
"""
```
