



# Java相关的配置







## Java11生成JRE

进入jdk安装目录后执行以下命令：

```shell
sudo ./bin/jlink --module-path jmods --add-modules java.desktop --output jre
```



## Eclipse或以Eclipse基础的各种软件找不到jre

>可以将在软件安装目录下建一个软链接指向jdk中的jre（如像java11+的没有预装**jre**，请用上面的命令生成**jre**）
>
>下面以**DBeaver**为例:
>
>```shell
>sudo ln -s /opt/JDK/jdk11/jre /opt/dbeaver/jre
>```

