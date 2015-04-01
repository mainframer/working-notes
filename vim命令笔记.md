## 自己常用的Vim命令
- 基本移动：hljk Ww Bb HML G gg nG zz z+Enter ctrl+D/U/F/B
- 插入命令：Ii Aa Oo cw
- 跳转命令：w e b ge ^ $ f F 10G 
- 删除命令：Xx 10x dd dw d3w D d^ dG d1G 2dd dj dk 
- 复制粘贴：yy 3yy y^或者y0 y$ yw y2w yG y1G Pp
- 替换撤销：Rr cc cw C ~ Uu un ctrl+r
- 缩进：<<    >>  3<<   3>>  :set shiftwidth=10  :ce :ri :le(V模式结合)
- 查找： Ff   ?/  Nn


## 其他命令
- 2dd = dj 或者 dk
- 点号.表示重复执行上一次命令
- :wq = :x (约等于)
- :w path_to_new_file  表示另存为 
- vim中输入:sh可切换至shell，然后shell中按ctrl+d回到vim
- ctrl+o光标回到跳转之前的位置
- ～表示将游标所在字母切换大小写
- 同时编辑多个文件： vim 1.txt 2.txt 按:n或者:N切换，若不保存强制切换则:n!或者:N!

