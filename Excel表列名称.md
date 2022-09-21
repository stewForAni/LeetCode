# Excel表列名称

```java
class TestconvertToTitle {
    public String convertToTitle(int columnNumber) {
        StringBuilder r = new StringBuilder();
        while (columnNumber > 26) {
            int m = columnNumber % 26;
            r.append(getS(m));
            columnNumber = m == 0 ? columnNumber / 26 - 1 : columnNumber / 26;
        }

        return r.append(getS(columnNumber)).reverse().toString();
    }

    public String getS(int a) {
        if (a == 0) {
            return "Z";
        }
        return String.valueOf((char) (a - 1 + 65));
    }
}
```

### 时间复杂度：O(log26 / columnNumber)
