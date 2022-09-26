# Excel 表列序号
给你一个字符串 columnTitle ，表示 Excel 表格中的列名称。返回 该列名称对应的列序号 。

示例 3:
输入: columnTitle = "ZY"
输出: 701


```java
class TesttitleToNumber {
    public int titleToNumber(String columnTitle) {
        int l = columnTitle.length();
        int r = 0;
        for (int i = 0; i < l; i++) {
            int a = columnTitle.charAt(i) - 64;
            r += Math.pow(26, l-i-1) * a;
        }
        return r;
    }
}
```

### 时间复杂度：O(n)
