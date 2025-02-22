
用处：只返回自定义词库中的词

# 使用文档

## 下载打包

## 打包引入pom

```xml
<dependency>
    <groupId>com.huaban</groupId>
    <artifactId>jieba-analysis</artifactId>
    <version>1.0.3-custom</version>
</dependency>
```

## 定义自己的词库

custom.txt
```
测试结巴 3 nt
结巴商品 3 nt
红军大学 3 nt
```

## 使用

```java
JiebaSegmenter segmenter = new JiebaSegmenter();
List<String> strs = Arrays.asList("你是结巴商品的大姨红军大学","结巴商品是红军大学你的大姨","你是大姨红军大学的结巴商品","你是大姨");
for (String str : strs) {
    List<SegToken> segTokens = segmenter.process(str, JiebaSegmenter.SegMode.INDEX, true);
    System.out.println(JSON.toJSON(segTokens));
}
```

输出----词库中有的词
```json
[{"endOffset":6,"startOffset":2,"word":"结巴商品"},{"endOffset":13,"startOffset":9,"word":"红军大学"}]
[{"endOffset":4,"startOffset":0,"word":"结巴商品"},{"endOffset":9,"startOffset":5,"word":"红军大学"}]
[{"endOffset":8,"startOffset":4,"word":"红军大学"},{"endOffset":13,"startOffset":9,"word":"结巴商品"}]
[]
```
