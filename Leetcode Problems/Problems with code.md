### problem no: 2. Add Two Numbers:

**You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.**

**using java**

```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode t=new ListNode(0);
        ListNode d=t;
        int ca=0;
        while(l1!=null || l2!=null || ca!=0){
            int s=ca;
            if(l1!=null){
                s=s+l1.val;
                l1=l1.next;
            }
            if(l2!=null){
                s=s+l2.val;
                l2=l2.next;
            }
            d.next=new ListNode(s%10);
            ca=s/10;
            d=d.next;
        }
        return t.next;
    }
}
```

### problem no: 189. Rotate Array:

**Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.**

**using c++**

```
class Solution{
    public:
    void rotate(vector <int> &nums, int k){
        int n=nums.size();
        k=k%n;
        vector <int>res(n);
        for(int i=0; i<n; i++){
            res[(i+k) % n] = nums[i];
        }
        nums=res;
    }
};
```
