# #322 Coin Change

```java
class Solution {
  public int coinChange(int[] coins, int amount) {
    int total[]= new int[amount+1];
    total[0]=0;
    for(int i=1;i<total.length;i++){
        total[i]=amount+1;
        for(int j=0;j<coins.length;j++){
            if(i>=coins[j]){
               total[i]=Math.min(total[i-coins[j]]+1,total[i]);
            }                
        }
    }
    return total[amount] > amount ? -1 : total[amount];
  }
}
```
