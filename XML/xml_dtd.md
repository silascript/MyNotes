# XML DTD笔记

## 引入方式

1. 内部DTD
2. 外部DTD
3. 公用DTD



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

