##AS400 & IBM i系统
####1、基础知识
- AS/400系统的屏幕显示格式有：菜单(`Menu`)、输入表项（`Entry`）、列表(`List`)、信息(`Information`)四种。
- **ADT**:Application Development Tools,应用开发工具。
- **SEU**:Source Entry Utility,AS/400上的源程序编辑器，支持多种编程语言。
- **PDM**:Program Development Manager,系统提供的一个开发编程环境
- **SDA**: Screen Design Aids:屏幕设计辅助软件，可产生目标显示文件和DDS源代码
- **IDDU**:交互式数据描述软件，用于交互式定义数据文件，记录格式，字段等
- **DFU**:Data File Utiility 数据文件应用软件，对数据库CRUD操作
####2、使用CL命令
	crtusrprf wrkusrprf dspcurdir wrkactjob
	call qcmd:用命令窗口取代菜单窗口
####3、使用功能键
	PF9 历史命令 
	SEU下PF4改正RPG语法错误 
	PF14编译源文件
####4、例子收集
（略)
#####5、IBMi上的C语言编程例子
参考链接：[http://www.cnblogs.com/lizmy/archive/2011/05/17/2048722.html](http://www.cnblogs.com/lizmy/archive/2011/05/17/2048722.html)

		 本地机器：i7adt01
		 创建库： crtlib lib(shibin) -> chgcurlib userid -> dsplib
		 创建source pf: crtsrcpf userid/csrc
		 创建mem: addpfm userid/csrc mytestc
		 wrkobjpdm userid ->'12'->'2' enter 
		 SEU编辑helloworld
		 选项14编译
#####6、IBMi上的RPG语言编程
```
	本地机器：i7adt01
	创建source pf:crtsrcpf userid/rpgsrc
	创建mem:addpfm userid/rpgsrc mytestrpg
	wrkobjpdm userid ->'12'->'2' enter SEU编辑helloworld
	用PF4来检查纠正RPG源文件语法错误，错误的会绿色高亮
```

	