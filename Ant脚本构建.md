## Ant脚本构建 ##
####1、基础知识  
- Apache Ant : 基于Java,是将软件编译、测试、部署等步骤联系在一起加以优化的一个构建工具，常用于**Java**环境中的软件开发。Ant的默认配置文件是`build.xml`。
- 构建:就是把代码从某个地方拿来、编译、再拷贝到某个地方去等操作。
- 跟Make的区别：Make主要用于C/C++构建, Ant主要用于Java构建。
- Ant的构建文件由XML文件组成，一个构建文件包含一个Project,一个Project包含若干个Target,一个Target包含若干个Task。
- 第三方库`antlib:net.sf.antcontrib`是使用Ant编写脚本最重要的补充。为Ant提供了复杂的编程逻辑功能（if）,（for）,（switch),(sortlist)以及常见的算术运算等，它将Ant扩展成了XML编程语言。

####2、安装配置
- 到`http://archive.apache.org/dist/ant/binaries/`下载`apache-ant-1.8.1-bin.zip`
- 解压到目录：`C:/java/apache-ant-1.8.1`
- 配置系统变量:`ANT_HOME`，值为:`C:\java\apache-ant-1.8.1`;在`PATH`环境变量中加入Ant的bin目录：`%ANT_HOME%\bin`; (执行ant命令可能会报找不到tools.jar错误，下载一个即可)
- 将`eclipse`安装目录下的`junit.jar`拷贝到`C:\java\apache-ant-1.8.1\lib`下，并且在系统变量`CLASSPATH`中添加`%ANT_HOME%\lib\junit.jar`，这样就能使ant支持junit。

####3、Ant命令
- ant, ant -verison, -help
- 选项`-quite`告诉Ant运行时只输出少量必要信息；选项`-verbose`告诉Ant运行时输出更多信息。
- 选项`-find`告诉Ant从当前目录往上层目录一直查找`build.xml`文件，不指定则只在当前目录找。
- 选项`-Dproperty=value`，如`-Daaa=aaa`传递给Ant，我们就可以在我们的`buildfile`中用引用`${aaa}`来存取这些环境变量。

####4、Ant例子
- `ant -buildfile test.xml`: 
 使用当前目录下的test.xml运行Ant，执行缺省的target
- `ant -buildfile test.xml -Dbuild=build/classes dist`
 使用当前目录下的test.xml运行Ant,使用名为dist的target,并设定build属性值名为`build/classes`
 
####5、build.xml文件
- `property`定义变量,在`target`里面调用用`${}`来调用
- `depends` 是它所依赖的`target`，在执行这个`compile`的`target`之前，ant会先检查init是否已经被执行过，如果执行过，着直接执行`compile`，如果没有执行过，就会执行它依赖的`target`，然后再执行本身的`target`。
- `target`里面可以再调用`target`
- 单独调用`Build.xml`中的一个`Target： ant targetname`
 