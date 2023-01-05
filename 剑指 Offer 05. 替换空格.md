# 剑指 Offer 05. 替换空格

 请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。 



## 双指针法

为什么要从后向前填充，因为从前向后填充就是O(n^2)的算法了，每次添加元素都要将添加元素之后的所有元素向后移动。

**数组填充类的问题，都可以先预先给数组扩容带填充后的大小，然后在从后向前进行操作。**

这么做有两个好处：

1. 不用申请新数组。
2. 从后向前填充元素，避免了从前先后填充元素要来的 每次添加元素都要将添加元素之后的所有元素向后移动。

```java
class Solution {
    public String replaceSpace(String s) {
        if (s.length() == 0) {
            return s;
        }
        
        char[] c = s.toCharArray();
        int count = 0;	// 空格数
        for (int i = 0; i < s.length(); i++) {
            if (c[i] == ' ') {
                count++;
            }
        }

        if (count == 0) {	// 如果没有空格就直接返回s
            return s;
        }
		
        // 因为要将空格替换成%20，一个空格相比之前多了两个字符，扩充数组空间
        char[] ch = new char[s.length() + count * 2];
        int i = c.length - 1;
        int j = ch.length - 1;

        // 双指针法
        while (i >= 0) {
            if (c[i] == ' ') {
                ch[j--] = '0';
                ch[j--] = '2';
                ch[j] = '%';
            } else {
                ch[j] = c[i];
            }

            i--;
            j--;
        }

        return new String(ch);
    }
}
```

