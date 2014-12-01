#Power System学习笔记
----------
###红宝书
[http://publib.boulder.ibm.com/html/as400/online/V4R4PDF.HTM](http://publib.boulder.ibm.com/html/as400/online/V4R4PDF.HTM)

###概念

> IBM i is an EBCDIC based operating system that runs on IBM Power Systems and on IBM PureSystems. It is the current evolution of the operating system, previously named i5/OS, and originally named OS/400 when it was introduced with the AS/400 computer system in 1988.  
> It is one of the operating systems supported on IBM Power Systems alongside AIX and Linux and on IBM PureSystems alongside AIX, Linux and Windows.


#####AS/400大约有80多种文件类型，QSYS是唯一一个可以包含lib的lib

#####开源终端TN5250
> http://sourceforge.net/projects/tn5250/

### IBM Power System服务器（可运行IBM i/AIX/Linux操作系统）
Rational Developer for Power System（以下简称 RD Power） 是一个针对 IBM Power System服务器（支持 IBM i、AIX、Linux）的 Eclipse 集成开发环境。RD Power 的亮点之一，是提供了功能强大的 RPG 可视化编程环境，可用于远程编辑、编译、调试、运行包括 UI 界面与报表在内的各种 IBM i RPG 程序。相比于传统的“绿屏”命令字符界面，RD Power 的可视化编程大大提高了 RPG 开发效率，节省了开发时间与成本。

###CL(用户与操作系统之间的接口，用户管理和操作 AS/400 系统）
	常用：
	CPYF		Copy File 
	CRTSRCPF 	Creating a Source Physical File
	CRTPF       Create Physical File 
	WRKF	 	Work with File
	DSPMSG   	Display message
	CRTUSRPRF 	Create User Profile 
    WRKUSRPRF 	Work with User Profiles 
	SIGNOFF     Sign off
	QSH         Start Qshell
	GO LICPGM   Work with licensed Program(查看/卸载安装的软件) 
	不常用：	
	SNDMSG     Send msg to user
	WRKDEVD    Work with Device Desripyions
###QSHell
	Qshell是一个针对AS/400的类Unix的接口
	WAS7安装目录：/QIBM/ProdData/WebSphere/AppServer/V7/Base/bin
	JTS安装目录： /QIBM/ProdData/JazzTeamServer405 
	Build System Toolkit安装目录： /QIBM/ProdData/RTC405/Build/jazz/buildsystem/buildtoolkit，通过'GO LICPGM'安装
	Rational Build(Forge) Agent安装目录：/QIBM/ProdData/RTC405/Build/jazz/buildsystem/buildagent 通过'GO LICPGM'安装
	./startbfa.qsh: 启动build agent （目录见上面)
##IBM i Navigator
[IBM Navigator for i 的学习路线图](https://www.ibm.com/developerworks/community/blogs/IBMi/entry/knowledge_path_of_ibm_navigator_for_i?lang=zh "IBM Navigator for i 的学习路线图")  


	
	
	

                                       