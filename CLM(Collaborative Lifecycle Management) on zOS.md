#CLM(Collaborative Lifecycle Management) on z/OS
### **Install CLM on z/OS via SMP/E**
参考链接: [http://pic.dhe.ibm.com/infocenter/clmhelp/v4r0m6/index.jsp?topic=%2Fcom.ibm.jazz.install.doc%2Ftopics%2Fr_rtcz_smpe_installation.html](http://pic.dhe.ibm.com/infocenter/clmhelp/v4r0m6/index.jsp?topic=%2Fcom.ibm.jazz.install.doc%2Ftopics%2Fr_rtcz_smpe_installation.html)
#### **SMP/E**

    1.Run MYUSID.JCL.LIB(ALLOC) to generate MYUSID.IBM.HRCC406.SMPEJOBS.BIN
	2.ftp bin/goto HLQ,then put C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRCC406\IBM.HRCC406.F1.BIN 'MYUSID.IBM.HRCC406.SMPEJOBS.BIN'
	3.Issue receive inda('MYUSID.ibm.hrcc406.smpejobs.bin') from option 6 to extract it.  Input DSNAME——DS('MYUSID.ibm.hrcc406.smpejobs')
	4.Run MYUSID.IBM.HRCC406.SMPEJOBS(BLZSEQAL) to create dataset for ftp in step 4.
	5.ftp
	  bin/goto HLQ,then
	  mput C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRBT406\IBM.HRBT406.F*
	  mput C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRBT406\IBM.HRBT406.SMPMCS
	  mput C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRBA406\IBM.HRBA406.F*
	  mput C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRBA406\IBM.HRBA406.SMPMCS
	  mput C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRCC406\IBM.HRCC406.F*
	  mput C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRCC406\IBM.HRCC406.SMPMCS
	  mput C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRDV406\IBM.HRDV406.F*
	  mput C:\MyFolder\RTC-RQM-RRC-SMPE-4.0.6\HRDV406\IBM.HRDV406.SMPMCS
	6.Run MYUSID.IBM.HRCC406.SMPEJOBS(BLZEXPND) to expand above BIN files.  
	7.Run  MYUSID.IBM.HRCC406.SMPEJOBS(BLZSMPE) 
	8.Run MYUSID.IBM.HRCC406.SMPEJOBS(BLZRECV1) MYUSID.IBM.HRCC406.SMPEJOBS(BLZRECV7) MYUSID.IBM.HRCC406.SMPEJOBS(BLZRECV8) MYUSID.IBM.HRCC406.SMPEJOBS(BLZRECV9)
	9.Run  MYUSID.IBM.HRCC406.SMPEJOBS(BLZALLOC)
	10.Run MYUSID.IBM.HRCC406.SMPEJOBS(BLZISMKD)
	11.Run MYUSID.IBM.HRCC406.SMPEJOBS(BLZDDDEF)
	12.Run MYUSID.IBM.HRCC406.SMPEJOBS(BLZAPPLY) 

###**配置(Configuration)**
####**Build System Toolkit 和 ISPF Gateway**
参考链接： [https://jazz.net/wiki/bin/view/Main/CLMSetupZos4xMilestone#Installing_Build_System_Toolkit](https://jazz.net/wiki/bin/view/Main/CLMSetupZos4xMilestone#Installing_Build_System_Toolkit)

**1,Run MYUSID.TARGET.SBLZSAMP(BLZCPBTK) (change @confgrp@ to CICSADM),create folders for BST**
**2. As per above link (should be done by BLZCPBTK already)**

    		cd /usr/lpp/jazz/v4.0.6/buildsystem/buildtoolkit/
			chmod 755 *.so
			extattr +p *.so
			chmod 755 checkaccess
			extattr +a checkaccess
			cd /usr/lpp/jazz/v4.0.6/scmtools/eclipse
			chmod 755 *.so
			extattr +p libblzdcore.so
			extattr +p libblzdcore64.so
			extattr +p libRTCzMVSExec.so
			extattr +p libRTCzMVSExec64.so
			chmod 755 scm
			cd /usr/lpp/jazz/v4.0.6/ispfclient/bin
			chmod 755 *.sh
			cd /usr/lpp/jazz/v4.0.6/buildagent
			extattr +p -s bfagent

**3.配置Rational Bulid Agent using EE build**

 **配置Configure Rational Build Agent**
   

     vi /usr/lpp/jazz/v4.0.6/buildagent/bfagent.conf
     change port from 5555 to 5406    
	 vi /etc/jazz406/ccm/startbfa.sh
     export _TIMEOUT =172800
	 export JAVA_HOME=/usr/lpp/java/J6.0
	 export JAZZ_USER=MYUSID 
	 export JAZZ_PASSWORD_FILE=/u/jazz406/pa33word
	 /usr/lpp/jazz/v4.0.6/buildagent/bfagent -s -f /usr/lpp/jazz/v4.0.6/buildagent/bfagent.conf

  **启动Start Build Forge Agent**  

     /etc/jazz406/ccm/startbfa.sh

  **Kill Build Forge Agent**  
    
	ps -ef|grep bfagent  

  或者也可以从Job执行： 
	
	MYUSID.TARGET.SBLZSAMP(BLZBFA) 	
  
**4.ISPF gateway**

**配置startispf.sh**
   cp /etc/ispf/ISPF.conf /etc/jazz406/ccm/
   vi /etc/jazz406/ccm/ISPF.conf       (ISPF gateway configuration file)

     ispllib=MYUSID.TARGET.SBLZLOAD,ISP.SISPLOAD                                                                                                                         
     ispmlib=MYUSID.TARGET.SBLZMENU,ISP.SISPMENU                                                                                                                                            
     ispplib=MYUSID.TARGET.SBLZPENU,ISP.SISPPENU                                                                                                                         
   cp /usr/lpp/ispf/bin/ISPZXENV /etc/jazz406/ccm
   vi /etc/jazz406/ccm/ISPZXENV        (ISPF gateway environment file)

     CGI_ISPCONF = '/etc/jazz406/ccm'
	 CGI_ISPWORK = '/etc/jazz406/ccm'
   vi /etc/jazz406/ccm/startispf.sh    (ISPF gateway startup script)

     export PATH=$PATH:/etc/jazz406/ccm:/usr/ispf/bin
 
 **启动Start startispf.sh**

    /etc/jazz406/ccm/startispf.sh  
   
###RTC-EE(Enterprise Extensions) System相关的知识
#### z/OS Build System Toolkit with no installer（130M）
**Build System Toolkit**  

	安装在z/OS上，通过SMP/E安装，目录为：@pathprefix@/usr/lpp/jazz/v4.0.5/buildsystem
	@pathprefix@: 参数，比如mvs255 CZ的就是：/var/testsrv2/ AZ的为：/var/testsrv1/

**Rational Build(Forge) Agent**

	安装在z/OS上，通过SMP/E安装，目录为：/var/testsrv2/usr/lpp/jazz/v4.0.5/buildagent
	@pathprefix@: 参数，比如mvs255 AZ的就是：/var/testsrv1/

**SCM (CLI) Tools**

	CLI: command line interface
	安装在z/OS上，通过SMP/E安装，目录为：/var/testsrv2/usr/lpp/jazz/v4.0.5/scmtools

**ISPF Client**

	安装在z/OS上，通过SMP/E安装，目录为：/var/testsrv2/usr/lpp/jazz/v4.0.5/ispfclient
	ex 'jazz00.tstsrv2.sblzexec(blz)' 'jazz00.tstsrv2 enu trace?i(BLZBUILD)' 
	
