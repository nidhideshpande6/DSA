# 1. Maximum Product Subarray

Given an integer array nums, find a subarray that has the largest product, and return the product.

The test cases are generated so that the answer will fit in a 32-bit integer.

## Example 1:
Input: nums = [2,3,-2,4]

Output: 6

Explanation: [2,3] has the largest product 6.

## Example 2:
Input: nums = [-2,0,-1]

Output: 0

Explanation: The result cannot be 2, because [-2,-1] is not a subarray.
 
```java
class Solution {
    public int maxProduct(int[] nums) {
        
        int n = nums.length;
        int l=1,r=1;
        int ans=nums[0];
        
        for(int i=0;i<n;i++){
            
			//if any of l or r become 0 then update it to 1
            l = l==0 ? 1 : l;
            r = r==0 ? 1 : r;
            
            l *= nums[i];   //prefix product
            r *= nums[n-1-i];    //suffix product
            
            ans = Math.max(ans,Math.max(l,r));
            
        }
        
        return ans;

    }
}
```
## Dry Run Example:

Input:

nums = [2, 3, -2, 4]

Initialization:

n = 4, l = 1, r = 1, ans = 2

### Iteration 1 (i = 0):

l = l * nums[0] = 1 * 2 = 2

r = r * nums[3] = 1 * 4 = 4

ans = max(ans, max(l, r)) = max(2, max(2, 4)) = 4

### Iteration 2 (i = 1):

l = l * nums[1] = 2 * 3 = 6

r = r * nums[2] = 4 * -2 = -8

ans = max(ans, max(l, r)) = max(4, max(6, -8)) = 6

### Iteration 3 (i = 2):

l = l * nums[2] = 6 * -2 = -12

r = r * nums[1] = -8 * 3 = -24

ans = max(ans, max(l, r)) = max(6, max(-12, -24)) = 6

### Iteration 4 (i = 3):

l = l * nums[3] = -12 * 4 = -48

r = r * nums[0] = -24 * 2 = -48

ans = max(ans, max(l, r)) = max(6, max(-48, -48)) = 6

### Output:

6
### Time Complexity:
O(n): Single traversal of the array.
### Space Complexity:
O(1): Only a few variables are used.
