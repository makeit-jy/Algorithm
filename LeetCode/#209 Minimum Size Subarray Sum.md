# #209 Minimum Size Subarray Sum

- 합계가 target보다 크거나 같은 연속 하위 배열의 최소 길이를 반환하는 문제.
- 조건에 부합하는 하위 배열이 없다면 return 0;
- 투 포인터와 적절한 위치에서 return해서 시간복잡도를 줄임.

![#209%20Minimum%20Size%20Subarray%20Sum%20ce0985882ade4ff5868ed2f0c8e16cde/209.Minimum_Size_Subarray_Sum.jpg](#209%20Minimum%20Size%20Subarray%20Sum%20ce0985882ade4ff5868ed2f0c8e16cde/209.Minimum_Size_Subarray_Sum.jpg)

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        if (nums.length == 0) return 0;
        if (nums.length == 1 && nums[0] >= target) return 1;
        int start = 0, end = 0, sum = 0, min = nums.length + 1;
        while (end < nums.length) {
            sum = sum + nums[end];
            while (sum >= target) {
                min = Math.min(min, end-start+1);
                if(min == 1) return 1;
                sum = sum - nums[start++];
            }
            end++;
        }
        return min == nums.length + 1 ? 0 : min;       
    }
}
```

```java
// TEST CODE

import org.junit.Assert;
import org.junit.Test;

public class SolutionTest {

    @Test
    public void solutionTest() {
        Solution s = new Solution();

        Assert.assertEquals(0,
                s.solution(0, new int[]{})
        );

        Assert.assertEquals(1,
                s.solution(4, new int[]{6})
        );

        Assert.assertEquals(2,
                s.solution(7, new int[]{2,3,1,2,4,3})
        );

        Assert.assertEquals(1,
                s.solution(4, new int[]{1,4,4})
        );

        Assert.assertEquals(0,
                s.solution(11, new int[]{1,1,1,1,1,1,1,1})
        );

        Assert.assertEquals(0,
                s.solution(200, new int[]{10,1,12,13,4,3,2,7})
        );

        Assert.assertEquals(2,
                s.solution(10000000, new int[]{10,1,12,5000000,5000000,4,3,2,7})
        );
    }
}
```