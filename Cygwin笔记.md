#Cygwin笔记
- 主机上的c盘对应/cygdrive/c
- 用命令startx打开xterm，之后该可以用Gvim，否则只能用vim  
#### 常用终端快捷键

 ```   
    Ctrl-U: 擦除一行光标前面的部分
	Ctrl-H: 擦除光标前面的一个字符
	Ctrl-A： 光标移到行首
	Ctrl-E： 光标移到行尾
	Ctrl-W: 清除光标之前一个单词
    Ctrl-K: 清除光标到行尾的字符	
	Ctrl-F： 光标后移一个字符 
	Ctrl-B： 光标前移一个字符
```
- 所有cygwin的帮助文档： 
	/usr/share/doc/Cygwin/
- ssh配置 
	`http://blog.csdn.net/chance_wang/article/details/3740464  ssh-host-config`
	
- ~/.bashrc  
- 变量：  输入env查看所有变量
  ```     
   CYGWIN: tty
	path:  c:/cygwin/bin
    LD_LIBRARY_PATH中存储的是动态链接库所在的目录
```
- Vim配置  
`/usr/share/vim/vim73/.vimrc  ~/.vimrc`
- 让配置实时生效
```	
	source ~/.bash_profile
	source ~/.bash_profile
```
- 查看命令的用法： man -k xxx 
- windows下面cygwin类似月apt-get的软件包安装管理器：`apt-cyg`
```
    wget http://apt-cyg.googlecode.com/svn/trunk/apt-cyg -P /bin
    chmod.exe +x /bin/apt-cyg
    apt-cyg安装源为ftp://mirror.mcs.anl.gov，设置为网易镜像源。
    pt-cyg -m http://mirrors.163.com/cygwin
apt-cyg update
```

 	