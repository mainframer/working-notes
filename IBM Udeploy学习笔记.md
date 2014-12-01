## Udeploy&Udeploy on System z ##
###基础知识
- 软件部署是通过各个预生产阶段将软件（广义定义）移至最终生产环境的进程


###下载Download
- http://www.ithov.com/server/132268.shtml IBM UrbanCode Deploy产品的安装和配置
- https://developer.ibm.com/urbancode/products/urbancode-deploy/  

###安装启动 install UCD (Derby +Tomcat)
- install java Add 3 system vars:    

``` 
JAVA_HOME=C:\Program Files (x86)\Java\jre7    
PATH =%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin    
CLASSPATH=%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar    
  ```
-  java -version OK
- unzip ibm-ucd-6.0.1.4.492009.zip
- run install-server.bat
- accept license,enter intall path "C:\IBM\UDeploy", enter JRE path "C:\Program Files (x86)\Java\jre7"
- default... (host name: hero-win7.cn.ibm.com)
- database usernaem: ibm_ucd  database password: password
- C:\IBM\UDeploy\bin\start_server.bat
- logon: https://hero-win7.cn.bim.com:8443 admin/admin

###安装启动Agent (install Agent)
- From web page-->Tools-->Download 'IBM UrbanCode Deploy Agent'  通常情况下，服务器和代理应该不会在同一台机器上
- unzip ibm-ucd-agent.zip
- run C:\hero\UCD\ibm-ucd-agent\ibm-ucd-agent-install\install-agent.bat
- enter install path: C:\IBM\UDeploy_Agent ; enter JRE path 'C:\Program Files (x86)\Java\jre7'
- 确认 Agent 是直连服务器还是连到一个代理中转器（agent relay）上。这里输入 n。表示 Agent 直连服务器。
- Enter the name for this agent: hero-win7-ucd-agent.cn.ibm.com
- Start: C:\IBM\UDeploy_Agent\bin\ibm-ucdagent.cmd start 
 
###概念：Components,Applications, Configuration,Processes,Recources
-  Application : Component = 1 : N  
-  资源是用户定义的一种逻辑表示，通过一种目录结构将多台目标机(Agent) 进行分类，并且与待部署组件关联起来