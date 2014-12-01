#IBM i重装上阵、操作、管理与开发
----------
###序和前言
1. IBM CDL 5大产品线：WebSphere、Information Management、Lotus、Rational、Tivoli
2. CDL新兴技术学院：Emerging Technology Institute
3. IBM i集成了大量商业应用软件如DB2,IBM i集成了大量第三方应用软件如SAP

##第一篇 基础篇
---

###第1章 IBM i概述
1.**IBM i发展史**:   
196*年 IBM为中小型企业定制中型计算机系统System/3% ==>1988年Rochester实验室发布AS/400服务器==>1994年IBM发布更受欢迎的AS/400 Advanced Series==>1997年发布AS/400e系列服务器for Internet==>随后10年(97~07),硬件平台不断创新，AS/400先后被重命名为eServer iSeries,System i. 而其错做系统也不断改进，由OS/400更名为i5/OS,IBM i.==>2008.04，整合System i和System p系列服务器形成一个新的硬件平台Power Systems，同时发布可在其上运行的3种操作系统(i5/OS,AIX,Linux)，冰将i5/OS更名为IBM i  
2. **IBM i的体系结构**

	技术独立性(64位RISC)
	基于对象的设计
	单级存储
	软件集成
	硬件集成  


###第2章 人机界面
1. 传统字符界面：CL命令、人性化的Menu以及类Unix的QShell
2. GO SYSTEM菜单：系统管理员（管理作业，监控系统状态，处理消息，处理文件对象库，备份恢复）  
   GO ASSIST菜单：所有User，（日常系统管理，设置定时任务，清楚磁盘垃圾，备份磁盘数据）
3. '+for more values' 处输入+回车可以允许输入更多值
4. 查看命令帮助: GO CMDCRT/ GO CMDEDT /  GO CMDDSP ...
5. 输入 'WRK*' 显示所有已WRK开头的CL命令
6. F9显示命令执行的历史
7. QShell的系统profile和User Profile: /etc/profile是系统的, /home/dev3/.profile则是用户自己的
8. iSeries Access For Web 和 iSeries Navigator


###第3章 对象和文件系统
1. QSYS是特殊的系统库，包含所有其他库对象，其余的库不能再包含其他的库对象。库是一组对象的逻辑集合
2. DSPLIB可以显示库列表，库列表中库的顺序就是系统查找库列表的顺序：系统部分==>当前库==>用户部分  
![](./image/IBMi_book_1.jpg)    
3. 特殊库的含义  
	***LIBL:** 当前库列表中所有库  
	***CURLIB:** 当前库  
	***ALL:**系统中所有库  
	***USRLIBL:** 当前库列表中用户部分的库  
	***ALLUSR:** 系统中所有由用户创建的库(所有不是以Q打头的库)  

4.PROD类型的库和TEST的区别是PROD类型库中的数据在调试模式(通过STRDBG运行)下是不可更改的，这就保证了生产数据不会在调试应用程序的时候被不小改动。

###第4章 消息处理
1.提供了程序与用户之间，程序与程序之间，用户与用户之间的通信机制

###第5章 工作管理

1. 所有的工作都是通过Job来完成的。工作管理的内容包括：作业，子系统，内存池，作业队列，输出队列，作业日志，定时作业。
2. 通过完整作业名称(Qualified Job Name)可以从CL端访问作业,QJN构成：作业编号/用户名称/作业名称
	WRKJOB JOB(168904/SHUANGHONG/IBOOK)  可简化为 WRKJOB JOB (IBOOK)
3. 一共有5种作业：交互式作业 和 批处理作业 （打印作业，批作业，通信作业）
##第二篇 系统管理篇 
---

###第6章 基本系统管理
1. `IPL`
2. 关机：`GO POWER`或者`PWRDWNSYS`
3. `WRKSYSVAL SYSVAL(*SEC)` 查看所有的安全系统值
4. 用户概要文件(User Profile)是i里面最基本却具有强大功能的安全控制机制，它规定了用户可以做什么以及系统将以什么样的形式呈现给用户
5. `GO SECTOOLS`来访问i提供给用户的安全工具
6. `GO SAVE`备份文件，`GO BACKUP`访问备份任务菜单，`GO RESTORE`来访问恢复菜单

###第7章 系统管理高级话题
(待定)

###第8章 故障诊断与性能优化
(待定)

###第9章 逻辑分区管理
1. 逻辑分区(LPAR)：将一台服务器分为逻辑上的多台服务器的功能，System i和Power Systems服务器都支持。
2. System i 和Power Systems服务器都是通过硬件管理控制台HMC来对LPAR进行管理和操作。

##第三篇 开发应用篇（p273/p603）
---
1. IBM i提供集成语言环境ILE,支持多种语言混合编程，ILE系列的编译器支持CL,RPG,COBOL,C/C++.通过ILE可以实现这些语言的模块化和联编(Binding).
2. IBM i还支持Java以及PHP.
###第10章 应用程序开发
(待定)
###第11章 辅助开发工具
(待定)
###第12章 IBM i上面的中间件
(待定)
###第13章 PASE
(待定)
###第14章 数据库应用开发
(待定)
###第15章 IBM i上的SOA及Web Service
(待定)
###附录A 词汇表