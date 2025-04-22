[Unicode – The World Standard for Text and Emoji](https://home.unicode.org/)
[Unicode表情目录](https://unicode.org/Public/emoji/)

可以判断字体的类型，<br>
ocr以后，<br>
字体可能有问题，<br>
通过查找这个类型的字体，<br>
进行替换<br>
```java
   public static boolean isExtensionACharacter(char ch) {
        Character.UnicodeBlock block = Character.UnicodeBlock.of(ch);
        if (block == Character.UnicodeBlock.KANGXI_RADICALS) {
            return true;
        }
        return false;
    }
```