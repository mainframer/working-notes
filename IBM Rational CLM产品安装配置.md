#IBM Rational CLM产品安装配置
----------
##Helpful Jazz Articles
1.**拓扑Topologies:**  [https://jazz.net/library/article/820](https://jazz.net/library/article/820)

##不同的安装方式
###1、 By Using Web Installer
- Windows x86 (260.87 MB)
- Linux x86 (260.51 MB)
- Solaris-64 (130.66 MB)
- AIX PPC (137.34 MB)
- Linux for System z (124.04 MB)
- Linux on Power (128.73 MB)

####Install in windows by Web Installer
	Express install：Tomcat+Derby  
	Win Server2008R2(TSAM)  
	CLM-Web-Installer-Win-4.0.6M1 260MB  
	JTS+CCM+QM+TrialKeysforCALM  
	Install path:C:\Program Files\IBM\JazzTeamServer  
	Start->All Program->Start JazzTeamServer  
	CMD: netstat -a -o (see port 9443 is listening)   
	https://localhost:9443/jts/setup ADMIN/ADMIN 
	public URI:https://localhost:9443/jts  
	create admin user:jtsadmin/jtsadmin  

#### Install in REHL6.2 64-bit by Web Installer
REHL6.2 64bit(TSAM)  
CLM-Web-Installer-Linux-4.0.6M1(能用来安装server/client/BuildToolKit)   
**Server:**   
	
	Express install:Tomcat+Derby  
	安装目录：/opt/IBM/JazzTeamServer (Server 4.0.6M1)   
	启动：Applications->Start JazzTeamServer 
	Will have file number limits in Linux. Here is solution:  
	http://pic.dhe.ibm.com/infocenter/clmhelp/v4r0m5/index.jsp?re=1&topic=/com.ibm.jazz.install.doc/topics/c_special_considerations_linux.html&scope=null  
	Issue command: JazzInstallDir/server/repotools-jts -reindex  
**RTC Client:**    
	
	安装目录：/opt/IBM/TeamConcert   (Client)  
**Build System Toolkit:**	           
	
	安装目录：/opt/IBM/TeamConcertBuild (Build System Toolkit 4.0.6M1)
	默认同时安装SCM Command Line Tool 
	自己选择要不要安装IBM JRE6.0

###2、By Using IM (IBM Install Manager)    
###Install in Windows by IM Repositories offering
#####Infor Center:   [Click here InfoCenter](http://pic.dhe.ibm.com/infocenter/clmhelp/v3r0m1/index.jsp?topic=%2Fcom.ibm.jazz.install.doc%2Ftopics%2Ft_s_server_installation.html)  
添加 http://jazzweb.beaverton.ibm.com/calm/main/I/CALM-I20131225-0551/calm-offerings-lpv4/repository/repository.config 到IM-->preference

	Server: 
	choose below 4 products to install them together in the same pkg.
	CCM+JTS+RM+Trial Key for CLM
	安装目录: C:\Program Files\IBM\JazzTeamServer
	choose to instlal Tomcat7 as well
	设置向导：https://localhost:9443/jts/setup ADMIN/ADMIN

	Build System toolkit:
	安装目录：C:\Program Files (x86)\IBM\TeamConcertBuild

	RTC Client:
	安装目录：C:\Program Files\IBM\TeamConcert1
	(允许跟BuildSystemToolkit安装在一起)
	 
###Tips
	WAS/z logs: SDSF->ST Pre AZ*->Check SYSOUT/SYSPRINT
	CLM/Z logs: USS: /var/testsrv1/u/jazz404/logs Use ~/bin/avi to look

  