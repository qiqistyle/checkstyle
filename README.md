Config.xml

```xml
<?xml version="1.0"?>
        <!DOCTYPE module PUBLIC
                "-//Puppy Crawl//DTD Check Configuration 1.3//EN"
                "http:///www.puppycrawl.com/dtds/configuration_1_3.dtd">
<module name="Checker">
<module name="TreeWalker">
    <module name="AvoidEscapedUnicodeCharacters">
        <property name="allowEscapesForControlCharacters" value="TRUE"/>
        <property name="allowByTailComment" value="TRUE"/>
        <property name="allowIfAllCharactersEscaped" value="TRUE"/>
        <property name="allowNonPrintableEscapes" value="False"/>
    </module>
</module>
</module>
```

test.java

```java
public class Test {
    public static void main(String[] args) {
        String unitAbbrevd = " d";
        String unitAbbrev = "\ufeff";
        String unitAbbrev1 = "\u03bcs"; // Greek letter mu, "s"
        String textBlockUnitAbbrev = """
            \u03bcs"""; // Greek letter mu, "s"
        String unitAbbrev2 = "\u03bc\u03bc\u03bc";
        String unitAbbrev4= "\u03bc\u03bcc";
        String unitAbbrev3 = "\u03bc\u03bcs";
        return '\ufeff' + content;
    }

}
```

Result 

```shell
tangfuqi@tangqiqideMacBook-Air test % java -jar checkstyle-8.39-all.jar -c config.xml test.java
开始检查……
[ERROR] /Users/tangfuqi/Desktop/test/test.java:9:29: 不要使用Unicode转义字符。 [AvoidEscapedUnicodeCharacters]
[ERROR] /Users/tangfuqi/Desktop/test/test.java:10:30: 不要使用Unicode转义字符。 [AvoidEscapedUnicodeCharacters]
检查完成。
Checkstyle以 2 个错误结束。
```

