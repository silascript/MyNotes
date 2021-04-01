# XML DTD笔记

## 引入方式

1. <a href="#dtd_ref_in">内部DTD</a>
2. <a href="#dtd_ref_ext">外部DTD</a>
3. <a href="#dtd_ref_pub">公用DTD</a>



### <a id="dtd_ref_in">内部DTD</a>

基础语法:

```xml-dtd
<!DOCTYPE 根元素名[
        元素描述
    ]>
```



### <a id="dtd_ref_ext">外部DTD</a>

基础语法:

```xml-dtd
<!DOCTYPE 根元素名 SYSTEM "外部DTD的URI">
```



### <a id="dtd_ref_pub">公用DTD</a>

公用DTD是一种特殊的外部DTD。它是由某个权威机构制定，供特定行业或公众使用。

公用DTD通过**PUBLIC**关键字引入。

公用DTD与外部DTD区别:

1. **PUBLIC**关键字

2. 公用DTD多了个DTD标识名

   

基础语法:

```xml-dtd
<!DOCTYPE 根元素 PUBLIC "DTD标识名" "公用DTD的URI">
```

例子:

![XMLSchema文档截图](xml_dtd.assets/2021-04-01 23-19-10屏幕截图.png)



### 



## DTD文档结构

* <a href="#dtd_declaration">DTD声明部分</a>
* <a href="#dtd_element">元素</a>
* <a href="#dtd_attlist">属性</a>
* <a href="#dtd_entity">实体</a>



#### <a id="dtd_declaration">DTD声明</a>

dtd的声明与XML声明语法相同

```xml
<?xml version="1.0" encoding="UTF-8"?>
```



### <a id="dtd_element">元素</a>

XML元素可以为空，可以为文本字符串，可以包含若干子元素，每个子元素又可包含若干子元素。

DTD是通过元素之间的父子关系，描述了整个文件的结构。

基础语法:

```xml-dtd
<!ELEMENT 元素名 元素类型描述>
```



### <a id="dtd_attlist">属性</a>

基础语法:

```xml-dtd
<!ATTLIST 属性所属元素 属性名 属性类型 [元素对属性的约束] [默认值]>
```



### <a id="dtd_entity">实体</a>

基础语法:

```xml-dtd
<!ENTITY 实体名 "实体值">
```

