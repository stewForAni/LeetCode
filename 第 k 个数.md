# 第 k 个数

有些数的素因子只有 3，5，7，请设计一个算法找出第 k 个数。注意，不是必须有这些素因子，而是必须不包含其他的素因子。例如，前几个数按顺序应该是 1，3，5，7，9，15，21。

(这个数的素因子只含有 3，5，7)

### 三指针

```java
class TestgetKthMagicNumber {
    public int getKthMagicNumber(int k) {
        int[] s = new int[k];s[0] = 1;
        int p1 = 0, p2 = 0, p3 = 0;
        for (int i = 1; i < k; i++) {
            int a = s[p1] * 3;
            int b = s[p2] * 5;
            int c = s[p3] * 7;
            s[i] = Math.min(Math.min(a, b), c);
            p1 = a == s[i] ? p1 + 1 : p1;
            p2 = b == s[i] ? p2 + 1 : p2;
            p3 = c == s[i] ? p3 + 1 : p3;
        }
        return s[k - 1];
    }
}
```
### 时间复杂度：O(k)


### 小顶堆

```java
class TestgetKthMagicNumber2 {
    public int getKthMagicNumber(int k) {
        long l = 0;
        Set<Long> s = new HashSet<>();
        PriorityQueue<Long> p = new PriorityQueue<>();
        p.offer(1L);
        for (int i = 0; i < k; i++) {
            l = p.poll();
            if (s.add(l * 3)) { p.add(l * 3); }
            if (s.add(l * 5)) { p.add(l * 5); }
            if (s.add(l * 7)) { p.add(l * 7); }
        }
        return (int) l;
    }
}
```
### 时间复杂度：O(k)

