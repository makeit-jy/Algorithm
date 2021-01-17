# #152 Maximum Product Subarray

- 연속되는 부분배열의 원소를 곱한 값의 최대값을 출력하면 되는 문제.
- 현재 값(i)과 지금까지의 최대값, 최소값 3개를 비교해서 최종적인 max값을 출력.
- 최소값을 구하는 이유는 음수*음수의 경우 양수가 되어 최대값이 될 수 있기 때문.

```java
class Solution {
  public int maxProduct(int[] nums) {
        
    int result = nums[0], max = nums[0], min = nums[0];

    for(int i=1; i<nums.length; i++) {
       int temp = max;
       max = Math.max(Math.max(nums[i]*max, nums[i]*min), nums[i]);
       min = Math.min(Math.min(nums[i]*temp, nums[i]*min), nums[i]);
       result = Math.max(result, max);
    }
    return result;        
  }
}
```