#Redis学习笔记

###安装 [http://download.redis.io/releases/redis-2.8.19.tar.gz](http://download.redis.io/releases/redis-2.8.19.tar.gz)  
	
```
tar xzf redis-2.8.19.tar.gz  
cd redis-2.8.19
make
```
###官网交互式入门手册 [http://try.redis.io/](http://try.redis.io/)
#####查看帮助
```
help			#查看Redis所有帮助
help SETNX		#查看SETNX命令的帮助
```
#####Key-Value:Redis支持的最重要的数据结构
```
SET server:name "fido" 		#设置key-value对
GET server:name 			#通过key值得到value: "fido"
SET connections 10
INCR connections => 11		#对key值使用INCR使其value自增1
使用INCR是因为它是原子操作，可以防止读到脏数据。
DEL connections				# 删除一个key-value对，再用GET取值返回nil
SETNX newconnections 5		#SETNX表示set if no exist，若已经存在，则不起作用
SET resource:lock "Redis Demo"
EXPIRE resource:lock 120		#EXPIRE可以对key添加有效期，这里是120秒
TTL resource:lock => 113	#用TTL实时查看有效期，返回-2表示过期，返回-1表示永不过期
```
#####List: Redis支持的有序集合List，提供了RPUSH, LPUSH, LLEN, LRANGE, LPOP, RPOP等操作。
```
RPUSH friends "Alice"		
RPUSH friends "Bob"		#RPUSH表示从右侧添加元素
LPUSH friends "Sam"		#LPUSH表示从左侧添加元素
LRANGE friends 0 -1			#LRANGE 0 -1返回List的所有元素
LRANGE friends 0 1			#LRANGE 0 1返回List前两个元素
LRANGE friends 1 2			#LRANGE 1 2返回List的第2，3个元素
LLEN friends => 3			#LLEN返回List长度
LPOP friends => "Sam"		#LPOP返回并删除List第一个元素
RPOP friends => "Bob"		#RPOP返回并删除List最后一个元素
```
#####Set:Redis支持的无序集合，集合里的元素必须唯一，Redis 提供了以下几种Set操作：SADD, SREM, SISMEMBER, SMEMBERS,SUNION.
```
 SADD superpowers "flight"
 SADD superpowers "x-ray vision"
 SADD superpowers "reflexes"  	#SADD往set里面添加元素，试图添加重复元素会被自动过滤
 SREM superpowers "reflexes"	#SREM从set里移除一个元素
 SISMEMBER superpowers "flight" => 1
 SISMEMBER superpowers "reflexes" => 0 #SISMEMBER验证set里元素
 SMEMBERS superpowers 		#SMEMBERS返回set所有元素
 SUNION superpowers birdpowers #SUNION对两个set求并集
 ```
 
#####Hashes: Redis支持哈希，用来处理从一个string映射到多个string的情况，(eg: A User with a number of fields like name, surname, age, and so forth):
```
HSET user:1000 name "John Smith"
HSET user:1000 email "john.smith@example.com"
HSET user:1000 password "s3cret"
HGETALL user:1000			#用HGETALL返回哈希所有的值
也可以简单的一次性赋所有值：
HMSET user:1001 name "Mary Jones" password "hidden" email "mjones@example.com"
HGET user:1001 name => "Mary Jones"
```