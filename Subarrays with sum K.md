# Subarrays with sum K

Given an unsorted array of integers, find the number of continuous subarrays having sum exactly equal to a given number k.

## Examples:

Input: k = -10, arr = [10, 2, -2, -20, 10]
Output: 3

Explaination:  Subarrays: arr[0...3], arr[1...4], arr[3..4] have sum exactly equal to -10.

Input: k = 33, arr = [9, 4, 20, 3, 10, 5]
Output: 2

Explaination:  Subarrays : arr[0...2], arr[2...4] have sum exactly equal to 33.

Input: k = 1, arr = [1]
Output: 1

Explaination: Since the required sum is 1 and the array also has a single element equal to 1, hence there is only one subarray.

## Brute force Approach
```java
class Solution {
    public int findSubArraySum(int k, int arr[]) {
        int s=0,res=0;
        for(int i=0;i<arr.length;i++){
            s=0;
            for(int j=i;j<arr.length;j++){
                s+=arr[j];
                if(s==k) {
                    res++;
                    continue;
                }
            }
        }
        return res;
    }
}
```
Time complexity  : O(n^2)

Space Complexity : O(1)
