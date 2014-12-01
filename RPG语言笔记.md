#RPG语言笔记
----------
##概念
	物理文件用于存放数据,使用SEU进行编辑产生的MEMBER不是物理文件，而是物理文件的定义.
	物理文件一般由MEMBER编译产生后，但它的存在不会依赖MEMBER
	源物理文件是特殊的物理文件，用于存放各类源代码的定义
	若无特殊说明物理文件均指存放数据（RECORD）的物理文件（PF-DTA）
	物理文件的删除必须在删除建立在该物理文件上的逻辑文件删除之后
	物理文件的删除必须在删除建立在该物理文件上的逻辑文件删除之后
	
##RPG: Report Program Generator
	Step1:建立User库 CTRLIB建立库 
	Step2:CRTSRCPF建立源物理文件(类似于文件夹的概念，可以包含成员,y用来存放源代码)STRSEU建立源成员
	Step3:进入库的方法 STRPDM-1-库名-(12) 或者WRKLIBPDM-12
		  进入源物理文件的方法 STRPDM-3 或者WRKLIBPDM+F4 /WRKLIBPDM+F4 /WRKMBRPDM+F4
	Step4:建立源物理的Member STRSEU+F4
	
![](./image/IBMi_book_1.jpg)

##PDM工具包
	PDM（ PROGRAMMING DEVELOPMENT MANAGER）也是 IBM i 提供的开发工具包，主要用于处理源代码、对象和库。PDM 的相关命令如下：
	STRPDM（Start PDM）：直接到 PDM 菜单
	WRKLIBPDM（Work with Library using PDM）：指定操作哪一个库或对当前库列表进行操作。
	WRKOBJPDM（Work with Object using PDM）：指定某一库包含的所有对象（可按名称、类型选取）。
	WRKMBRPDM（Work with Members using PDM）：指定操作某一库下某一源文件下包含的所有或部分成员。
##SEU编辑器
	SEU 是 IBM i 提供的全屏幕代码编辑工具，主要功能如下：
	1.创建源文件成员。
	2.编辑源代码，包括添加、修改、删除、复制、移动等功能。
	3.语言相关提示
	4.语法检查功能
	5.分屏浏览 / 编辑
	SEU 使用的是 LPEX（Live Parsing eXtensible）编辑器
	
