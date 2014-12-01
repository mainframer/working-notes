#Docker学习
----
###Docker常识
- Docker基于Go语言，LXC技术(Linux Container)，代码托管在Github上  
- 最初的 LXC 技术是由 IBM 研发的，目前已经进入 Linux 内核
- LXC在linux下的配置文件lxc.conf，配置项为键值对形式。
- LXC 采用 cgroup 来对容器进行资源(CPU,RAM,Storage,Network)管理
- 谷歌认为Docker足以改变人们创建软件方式,集装箱式部署
- 如Web应用、后台应用、数据库应用、大数据应用比如Hadoop集群、消息队列等等都可以打包成一个Image部署
- 若果利用容器的话，那么开发直接在容器里开发，提测的时候把整个容器给测试，测好了把改动改在容器里再上线就好了。通过容器，整个开发、测试和生产环境可以保持高度的一致
- 程序员在服务器端的部署应用程序的改变：  
`安装->配置->运行` 变成 `打包->复制->传送->粘贴->运行`
- 各个容器之间的数据和内存空间相互隔离，可以保证一定的安全性。 
- Docker只能在64 bit的Linux下运行
 
###Docker 对比 VM
- 启动速度快，容器通常在一秒内可以启动，而 VM 通常要更久
- 资源利用率高，一台普通 PC 可以跑上千个容器，你跑上千个 VM 试试
- 性能开销小， VM 通常需要额外的 CPU 和内存来完成 OS 的功能，这一部分占据了额外的资源

###Mac下安装Docker
1.下载安装boot2docker https://github.com/boot2docker/osx-installer/releases 它除了安装docker，还会安装一个轻量级虚拟机VitualBox，并在上面跑Docker daemon   
http://docs.docker.com/installation/mac/  
`sudo chmod 755 /usr/local/bin  `
 
单机boot2docker启动  
####boot2docker命令
 	$boot2docker  init
 	$boot2docker start
 	$docker version
 	$docker run hello-world
 	$boot2docker stop
###Docker命令
	docker  #列出所有命令
	docker images #列出所有images
	