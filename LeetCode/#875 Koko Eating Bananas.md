# #875 Koko Eating Bananas

![#875%20Koko%20Eating%20Bananas%20e441797bcb1544d3bc048bd824b7146a/875.Koko_Eating_Bananas_1.jpg](#875%20Koko%20Eating%20Bananas%20e441797bcb1544d3bc048bd824b7146a/875.Koko_Eating_Bananas_1.jpg)

![#875%20Koko%20Eating%20Bananas%20e441797bcb1544d3bc048bd824b7146a/875.Koko_Eating_Bananas_2.jpg](#875%20Koko%20Eating%20Bananas%20e441797bcb1544d3bc048bd824b7146a/875.Koko_Eating_Bananas_2.jpg)

---

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        int l = 1;
        int r = Arrays.stream(piles).max().getAsInt();
        while (l < r) {
            int m = (l + r) / 2, total = 0;
            for (int p : piles) {
                total += (p + m - 1) / m;
            }
            if (total > h) l = m + 1;            
            else r = m;
        }
        return l;
    }
}
```

---

```java
// TEST CODE

import org.junit.Assert;
import org.junit.Test;

public class SolutionTest {

    @Test
    public void solutionTest() {
        Solution s = new Solution();

        Assert.assertEquals(4,
            s.solution(new int[]{3,6,7,11}, 8)
        );

        Assert.assertEquals(30,
                s.solution(new int[]{30,11,23,4,20}, 5)
        );

        Assert.assertEquals(23,
                s.solution(new int[]{30,11,23,4,20}, 6)
        );
    }
}
```

---

```java
// Runtime Error

class Solution {
    public int solution(int[] piles, int h) {

        int l = 1, r = 1000000000;
        int answer = r;

        while (l < r) {
            int k = (l + r) / 2;
            int total = 0;
            for(int p : piles) {
                total += Math.ceil(p / k);
            }
            if(total <= h) {
                answer = Math.min(answer, k);
            }
            else l = k+1;
        }
        return answer;
    }
}
```