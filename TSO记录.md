#TSO学习
###Setup Steps Of New PCOMM/TSO Connection
每一次安装完PCOMM，要做的设置：[IBM PCOMM初始设置的最佳实践 for zOS and IBM i](http://mainframer.github.io/articles/IBM%20PCOMM%E5%88%9D%E5%A7%8B%E8%AE%BE%E7%BD%AE%E7%9A%84%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5%20for%20zOS%20and%20IBM%20i.html)

###TSO的命令列表
     RENAME  OLDNAME  NEWNAME
     EDIT reports.data  PDS需要括号：LISTDS (PARTS.DATA TEST.DATA)
     LINESIZE(80) 每行80个
     ALLOCATE 
     ALTLIB 
     ATTRIB
     CALL
     CANCEL
     DELETE
     EDIT
     END
     EXEC
     EXECUTIL
     FREE
     HELP
     LINK
     LISTALC
     LISTBC
     LISTCAT
     LISTDS
     LOADGO
     LOGOFF
     MVSSERV
     OUTDES
     OUTPUT
     PRINTDS
     PROFILE
     PROTECT
     RECEIVE
     RENAME
     RUN
     SEND
     SMCOPY
     SMFIND
     SMPUT
     STATUS
     SUBMIT
     TERMINAL
     TEST
     TIME
     TRANSMIT
     TSOLIB
     VLFNOTE
     WHEN