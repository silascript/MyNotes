# Ranger相关





## 配置

生成配置文件

```shell
ranger --copy-config=all
```

就时就在~/.config/ranger目录下生成一堆配置文件。主要配的是scope.sh和rc.conf。







## 预览



### 图片预览

使用**w3m**或**ueberzug**



w3m是终端web浏览器

如果终端使用w3m不支持不生效，就使用**ueberzug**

配置rc.conf如下:

```shell
set preview_images true
set preview_images_method ueberzug
```