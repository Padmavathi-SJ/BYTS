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

### problem no: 200. Number of Islands:

**Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.
An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.**

**using java**

```
class Solution {
    public int numIslands(char[][] grid) {
        int r=grid.length;
        int c=grid[0].length;
        int islands=0;
        for(int i=0; i<r; i++){
            for(int j=0; j<c; j++){
                if(grid[i][j] == '1'){
                    islands++;
                    dfs(grid, i, j);
                }
            }
        }
        return islands;
    }
    public void dfs(char [][] grid, int i, int j){
        int r=grid.length;
        int c=grid[0].length;

        if(i<0 || i>=r || j<0 || j>=c || grid[i][j]=='0'){
            return;
        }

        grid[i][j]='0';

        dfs(grid, i-1, j);
        dfs(grid, i+1, j);
        dfs(grid, i, j-1);
        dfs(grid, i, j+1);
    }

}
```

### 42. Trapping Rain Water:

**
```
class Solution {
    public int trap(int[] height) {
        int len=height.length;
        int[] left=new int[len];
        left[0]=height[0];
        for(int i=1; i<len; i++){
            left[i]=Math.max(height[i], left[i-1]);
        }

        int[] right=new int[len];
        right[len-1]=height[len-1];
        for(int i=len-2; i>=0; i--){
            right[i]=Math.max(height[i], right[i+1]);
        }

        int water=0;
        for(int i=0; i<len; i++){
            water += (Math.min(left[i], right[i])) - height[i];
        }

        return water;
    }
}
```
