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

### DivisibilityByEleven:
* You are given a function,
int DivisibilityByEleven(int num);

The function accepts an integer 'num' as input. You have to implement the function such that it returns the number of contiguous integer fragments of 'num' that are divisible by 11. Contiguous integer fragments of a number, say 1273, are:
1, 2, 7, 3, 12, 27, 73, 127, 273 and 1273

```
Example
Input
1215598
Output
4
Explanation
55, 121, 12155 and 15598 are contiguous fragments of the number 1215598 that are divisible by 11

Sample Input
55

Sample Output
1


// java

import java.util.*;
class Main{
    public static void main(String[] args){
        Scanner input=new Scanner(System.in);
        
        int num=input.nextInt();
        String numStr = Integer.toString(num);
        int length=numStr.length();
        int count=0;
        for(int i=0; i<length; i++){
            for(int j=i+1; j<=length; j++){
                String fragment = numStr.substring(i, j);
                
                int fragmentNum = Integer.parseInt(fragment);
                
                if(fragmentNum % 11 == 0){
                    count++;
                }
            }
        }
        System.out.println(count);
        input.close();
    }
}
"""
1215598 //n
4 
"""
```
