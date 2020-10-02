



# Java相关的配置







## Java11生成JRE

进入jdk安装目录后执行以下命令：

```shell
sudo ./bin/jlink --module-path jmods --add-modules java.desktop --output jre
```

>把jmodes目录所有模块都生成jre:
>
>```shell
>sudo ./bin/jlink --module-path jmods --add-modules ALL-MODULE-PATH --output jre
>```
>
>

## Eclipse相关

### Eclipse基础的各种软件找不到jre

>可以将在软件安装目录下建一个软链接指向jdk中的jre（如像java11+的没有预装**jre**，请用上面的命令生成**jre**）
>
>下面以**DBeaver**为例:
>
>```shell
>sudo ln -s /opt/JDK/jdk11/jre /opt/dbeaver/jre
>```

>Eclipse运行需要的模块:
>
>java.base,java.desktop,java.logging,java.xml,java.naming,java.net.http,java.sql,java.sql.rowset
>
>

#### Tomcat配置出问题

>配置tomcat时，提示“eclipse tomcat unknown version of tomcat was specified”
>
>因为配置tomcat需要访问tomcat目录下的lib库,而访问此目录需要相应的权限
>
>所以得修改lib目录的权限:
>
>```shell
>chmod -R 777 apache-tomcat-xxx/lib
>```