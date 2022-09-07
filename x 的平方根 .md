# x 的平方根

给你一个非负整数 x ，计算并返回 x 的 算术平方根 。
由于返回类型是整数，结果只保留 整数部分 ，小数部分将被 舍去 。


```java
class Solution {
    public int mySqrt(int x) {
          if (x == 1) {
            return 1;
        }

        long result = x / 2;
        long high = x;
        long low = 0;

        while (true) {
            if (result * result > x) {
                high = result;
            } else if (result * result < x) {
                low = result;
            } else {
                return (int) result;
            }
            if (high - low == 1) {
                return (int) low;
            }
            result = (high - low) / 2 + low;
        }
    }
}
```

### 时间复杂度：O(logx)