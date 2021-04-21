# #48 Rotate Image

- n x n 2D 행렬을 시계 방향으로 90도 회전시키는 문제.
- 주의할 점: 다른 2D 행렬을 할당하지 않고 직접 수정하기.

![48 Rotate Image_1](https://user-images.githubusercontent.com/64471645/115522668-4719d900-a2c7-11eb-917f-4886c68cd657.JPG)

![48 Rotate Image_2](https://user-images.githubusercontent.com/64471645/115522743-5862e580-a2c7-11eb-841e-205b0bc985e2.JPG)

![48 Rotate Image_3](https://user-images.githubusercontent.com/64471645/115522803-644ea780-a2c7-11eb-8d8d-bfcc97dcfd60.JPG)
---

```java
import java.util.*;

class Solution {
    public int[][] solution(int[][] matrix) {

        Stack<Integer>[] columns = new Stack[matrix.length];

        for (int i=0; i<matrix.length; i++) {
            columns[i] = new Stack<>();
        }
        for (int i=0; i<matrix.length; i++) {
            for (int j=0; j<matrix.length; j++) {
                columns[i].push(matrix[j][i]);
            }
        }
        for (int i=0; i<matrix.length; i++) {
            for (int j=0; j<matrix.length; j++) {
                matrix[i][j] = columns[i].pop();
            }
        }
        return matrix;
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

        Assert.assertArrayEquals(new int[][]{{15,13,2,5},{14,3,4,1},{12,6,8,9},{16,7,10,11}},
                s.solution(new int[][]{{5,1,9,11},{2,4,8,10},{13,3,6,7},{15,14,12,16}})
        );

        Assert.assertArrayEquals(new int[][]{{7,4,1},{8,5,2},{9,6,3}},
                s.solution(new int[][]{{1,2,3},{4,5,6},{7,8,9}})
        );
    }
}
```
