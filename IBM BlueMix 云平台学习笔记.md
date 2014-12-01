##IBM BlueMix云平台学习笔记 [PaaS]= [DevOps + IaaS]
第一部分：基础篇
----------
###云计算基础
- Iaas面向系统管理人员；Paas面向开发人员；Saas面向业务人员
- PaaS 是运行在 Iaas 层上的一系列软件服务，并把服务器平台或开发环境作为一种服务提供给用户，也就是“平台即服务”。

###BlueMix基础
- BlueMix 的账号就是 IBM ID
- 面向Mobile（MBaaS）和Web开发人员，加快应用开发，缩短部署时间，程序员不需要去关心底层的操作系统，运行时，网络等等一切和 code 本身无关的东西
- 管理使用BlueMix方式：Web界面，CF命令行
- BlueMix提供一系列Runtime和Service,还不支持OpenStack
- BlueMix也提供了中间件服务
- App Client通过REST or HTTP APIs来和BlueMix通信
- 已经集成了Power系统，正在考虑集成System Z系统
- 是一个集合了DevOps和IaaS的Paas
- 以Softlayer为Iaas，基于Cloud Foundry的开放云架构实现


###(CloudFoundry) CF 命令
	
	cf --help
	cf help scale #显示特定命令scale的用法
	cf apps #显示所有已部署的app
	cf stop appName
	cf restart appName
	cf delete appName
	cf scale appName #更改指定app的instance数目及内存分配
	cf logs appName #包括标准输出log和error log  （--recent参数较长用)
	cf marketplace #显示本账号所属组织所有可见的service
	cf events appName #显示app的runtime event
	cf set-env appName variable value #设置环境变量
	cf buildpacks #查看所有可用的buildpack
	cf push 命令默认会将当前目录下的所有内容 push 到云端，
	        除非我们显示的使用 –p 参数显示的指定要部署的内容
	        

###Manifest.yml参数
- disk_quota: 2048	 (默认每个instance是1G)

###IBM DevOps Services （IDS)
####使用Git Command line连接到https://hub.jazz.net
- git clone ....  

####使用Eclipse插件EGit连接到https://hub.jazz.net
- 安装插件：http://download.eclipse.org/egit/updates  
- Window > Show View > Other >git   

####WAS Liberty  [在Eclipse中安装配置WAS Liberty环境](https://developer.ibm.com//wasdev/downloads/)
- 在Eclipse中安装Liberty插件用来开发部署调试应用程序

第二部分：实例篇
----------
###实例1: [简单的 Node.js 文件上传应用程序](http://www.ibm.com/developerworks/cn/cloud/library/cl-bluemix-nodejs-app/index.html)  
**步骤:**  
1. mkdir git; cd git  
2. git clone https://github.com/ibmjstart/bluemix-node-mysql-upload.git (仔细看README.md)  
3. cf login -a https://api.ng.bluemix.net 输入bluemix的邮箱密码，选择dev空间  
4. cf create-service mysql 100 mysql-node-upload 创建一个名为mysql-node-upload且plan值为100的MYSQL service  
5. cd git/bluemix-node-mysql-upload/app  
6. cf push ShibinNodeMySQLUpload --no-manifest --no-start -c "node app.js" 将本地的app.js 推送到bluemix  
7. cf bind-service ShibinNodeMySQLUpload mysql-node-upload 绑定MYSQL 服务到新建的app.  
8. cf start ShibinNodeMySQLUpload  启动app  
9. 访问:http://shibinnodemysqlupload.mybluemix.net/  成功

###实例2: [用自定义的 Go buildpack构建一个算质数及分解质因数的数学app]  (http://www.ibm.com/developerworks/cn/cloud/library/cl-bluemix-go-app/index.html)
**步骤:**  
1. 到go语言官网下载适合系统的安装包：[https://storage.googleapis.com/golang/go1.3.1.darwin-amd64-osx10.8.pkg](https://storage.googleapis.com/golang/go1.3.1.darwin-amd64-osx10.8.pkg)  并安装。
2. 到Jazzhub上下载源码：https://hub.jazz.net/project/mcrudele/Goweb (File->Export )  
3.  go run goweb.go 启动本地服务器，至浏览器中预览:  http://localhost:4001   
4. cf login -a https://api.ng.bluemix.net  输入bluemix的邮箱密码，选择dev空间  
5. 修改manifest.yml里面的host:   host:ShibinGoWeb  
6. cf push ShibinGoWeb -b https://github.com/michaljemala/cloudfoundry-buildpack-go  
7. 到bluemix上面坚持app运行情况，访问：shibingoweb.mybluemix.net

###实例3:[在BlueMix上部署基于Node.js的轻量级开源博客Ghost.js---MarkDown语法](https://www.ibm.com/developerworks/community/blogs/1ff27386-9f09-46fa-965e-ac74f82c184b/entry/%25e5%25b0%2586_ghost_js_%25e9%2583%25a8%25e7%25bd%25b2%25e5%259c%25a8_ibm_bluemix_%25e4%25b8%258a?lang=zh)
**步骤:**  
1. 下载安装最新版Ghost 0.5.1 [https://ghost.org/download/ ](https://ghost.org/download/ ) 解压缩，切换到根目录  
2. git clone https://github.com/ibmjstart/bluemix-ghost-js.git  
3. 将这个repo里面的package.json,cnofig.js,manifest.yml三个文件复制到Ghost 0.5.1根目录  ,这样就能支持Bluemix了。  
4. 修改manifest.yml里面的参数  
5. 创建名为ghostdbservice的MYSQL后段数据库服务(Ghost.js目前只支持mysql)  
	
	cf login -a https://api.ng.bluemix.net 
	#输入bluemix的邮箱密码，选择dev空间
	#设置App实例部署的staging及启动超时时间(分钟)，并推送到Bluemix
	CF_STAGING_TIMEOUT=4 CF_STARTUP_TIMEOUT=4 cf push

###实例4:[用Eclipse的CF插件创建基于WAS Liberty的Java应用](http://www.tudou.com/programs/view/ox2cGjMEVbk/?FR=LIAN)
**步骤:**  
1. 登陆bluemix创建一个Liberty for Java的应用名为：shibin-java-liberty  
2. 点击http://shibin-java-liberty.mybluemix.net/ 发现已经可以正常工作  
3. 点”View Quick Start“可以看到操作手册，可以指导后续开发。  
4. 下载"View Quick Start"里面的本应用基础代码: shibin-java-liberty.zip  
5.  ....

###实例5:使用 Bluemix 中的 Rules 服务构建一个酒店预订应用程序
[使用 Bluemix 中的 Rules 服务构建一个酒店预订应用程序](http://www.ibm.com/developerworks/cn/cloud/library/cl-hotel-rules-app/index.html)

cf login -a https://api.ng.bluemix.net （输入用户名密码）

