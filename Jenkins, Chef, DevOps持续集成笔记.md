##Jenkins & Chef & DevOps持续集成笔记
---
###Jenkins [http://jenkins-ci.org/](http://jenkins-ci.org/)
####基础知识  
- 基于Java，原名Hudson，为持续集成而生，用于监控持续重复的工作  

####搭建运行
#####方式一 ——直接一个War包
- 最简单的搭建方式：只需下载一个war包：jenkins.war
- 运行：java -jar jenkins.war ，打开浏览器：http://localhost:8080/ 即可用Jenkins
- 后台运行：nohup java -jar jenkins.war  

#####方式二——放在Tomcat中运行
Mac下安装轻量级Web应用服务器容器Tomcat  
- 官网下载[apache-tomcat-8.0.12.tar.gz](http://apache.fayea.com/apache-mirror/tomcat/tomcat-8/v8.0.12/bin/apache-tomcat-8.0.12.tar.gz)
- 解压到~/Library/Tomcat
- sudo chmod 755 ~/Library/Tomcat/bin/*.sh
- 进入tomcat下的/bin目录，启动tomcat
将jenkins.war文件放入tomcat下的webapps目录下，启动jenkins时，会自动在webapps目录下建立jenkins目录，所以在地址栏上需要输入的地址于上一种方法有点不一样：
http://localhost:8080/jenkins。

###Chef
(待定)
###DevOps
（待定)
