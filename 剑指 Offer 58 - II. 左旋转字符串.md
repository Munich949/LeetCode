# 剑指 Offer 58 - II. 左旋转字符串

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。



思路：先反转前n个，再反转length - n个，再整个反转，就能得到左旋转字符串。



## 代码(不申请额外辅助空间，空间复杂度O(1))

```java
class Solution {
    public static String reverseLeftWords(String s, int n) {
        int length = s.length();
        char[] ch = s.toCharArray();
        reverseString(ch, 0, n - 1);
        reverseString(ch, n, length - 1);
        reverseString(ch, 0, length - 1);
        return String.valueOf(ch);
    }
    public static void reverseString(char[] ch, int start, int end) {
        while (start < end) {
            ch[start] ^= ch[end];
            ch[end] ^= ch[start];
            ch[start] ^= ch[end];
            start++;
            end--;
        }
    }
}
```

