
jieba分词只返回自定义词库中的词

# 使用文档

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
WordDictionary.getInstance().loadUserDict(Paths.get("/Users/edy/Workspace/gf/baili-demo/libs/baili.txt"));
JiebaSegmenter segmenter = new JiebaSegmenter();
List<SegToken> segTokens = segmenter.process("你是结巴商品的大姨", JiebaSegmenter.SegMode.INDEX, true);
System.out.println(JSON.toJSON(segTokens));
```

输出----词库中有的词
```json
[{"endOffset":6,"startOffset":2,"word":"结巴商品"}]
```
