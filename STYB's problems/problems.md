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

### Move hyphens:

* You are given a function,char*MoveHyphen(char str[],int n);Implement the function to move all hyphens(-) in the string to the front of the given string.NOTE: The function accepts a string “str” of length ‘n’, that contains alphabets and hyphens (-). Return null if str is null.

```
Input 1: Move-Hyphens-to-Front
Output 1: ---MoveHyphenstoFront

Explanation: The string “Move-Hyphens -to-front” has 3 hyphens (-), which are moved to the front of the string, this output is “---MoveHyphenstofront”

Input 2:  String-Compare
Output 2: -StringCompare

//java

import java.util.*;
class Main{
    public static String moveHypensFront(String str){
        int l=str.length();
        StringBuilder hyphenPart = new StringBuilder();
        StringBuilder nonHyphenPart = new StringBuilder();
        for(int i=0; i<l; i++){
            char ch = str.charAt(i);
            if(ch == '-'){
                hyphenPart.append(ch);
            }
            else{
                nonHyphenPart.append(ch);
            }
        }
        return hyphenPart.toString() + nonHyphenPart.toString();
    }
    public static void main(String[] args){
        Scanner input=new Scanner (System.in);
        
        String str=input.nextLine();
        
        System.out.println(moveHypensFront(str));
        input.close();
    }
}
"""
pad-ma-va-thi
---padmavathi
"""
```

### 07. Add two numbers in the given base without converting into base
```
Input Format
get two numbers and base
Output Format
display the sum
Sample Input 1
1010 11001 2
Sample Output 1
100011
Sample Input 2
123  13 4
Sample Output 2
202

import java.util.*;
public class Main{
    public static String addTwoNums(String n1, String n2, int base){
        while(n1.length() < n2.length()){
            n1="0" + n1;
        }
        while(n1.length() > n2.length()){
            n2="0" + n2;
        }
        StringBuilder res = new StringBuilder();
        int sum=0;
        int carry=0;
        for(int i=n1.length()-1; i>=0; i--){
            int digit1 = Character.getNumericValue(n1.charAt(i));
            int digit2 = Character.getNumericValue(n2.charAt(i));
            
            sum = digit1+digit2+carry;
            res.append(sum % base);
            carry=sum/base;
        }
        if(carry > 0){
            res.append(carry);
        }
        return res.reverse().toString();
    }
    public static void main(String[] args){
        Scanner input=new Scanner(System.in);
        
        String n1=input.nextLine();
        String n2=input.nextLine();
        int base=input.nextInt();
        
        System.out.println(addTwoNums(n1, n2, base));
        input.close();
    }
}

```

### 10. Rotate String:

* Consider one string as input. You have to check that given strings with single backward and forward shift are same or not. If they are same then print 1 otherwise print 0.
* Hint: -Backward Shift: A single circular rotation of the string in which the first character becomes the last character and all other characters are shifted one index to the left. For example, abcde becomes bcdea after one left shift.

* Forward  Shift:  A single circular rotation of the string in which the last character becomes the first character and all other characters are shifted to the right. For example, abcde becomes eabcd after one right shift
 
* Input Format:  Candidate has to write the code to accept single string value for str without any additional message.

* Output Format: Written program code should generate output as single integer value i.e. 0 or 1 which represent both forward and backward shift strings are equal or not.
Additional message in output will cause to failure of test cases.

* Constraints:
String str should not allowed space, special character and numbers.
String str should only in English language.

```
Examples:
Examples -1:
Input: 
sfdlmnop
Output: 
0

Examples - 2:
Input: 
mama     
Output: 
1

Explanation:
In first example, string is “sfdlmnop”. 
Forward Shift:- fdlmnops
Backward Shift:- psfdlmno
Above both strings are not equal. So output is 0.

In second example, string is “mama”.
Forward Shift:- amam
Backward Shift:- amam
Above both strings are equal. So output is 1.


import java.util.*;
public class Main{
    public static int compare(String str){
        int len=str.length();
        String forwardShift = str.substring(1) + str.charAt(0);
        String backwardShift = str.charAt(len-1) + str.substring(0, len-1);
        if(forwardShift.equals(backwardShift)){
            return 1;
        }
        return 0;
    }
    public static void main(String[] args){
        Scanner input=new Scanner(System.in);
        
        String str=input.nextLine();
        
       System.out.println(compare(str));
        input.close();
    }
}
"""
mama
1  //o/p

sfdlmnop
0  //o/p
"""
```
