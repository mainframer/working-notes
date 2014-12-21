#Redis笔记

###安装 [http://download.redis.io/releases/redis-2.8.19.tar.gz](http://download.redis.io/releases/redis-2.8.19.tar.gz)  
	
```
一般安装用make：
tar xzf redis-2.8.19.tar.gz  
cd redis-2.8.19
make

生产环境中安装用install_server.sh：
% cd utils
% ./install_server.sh
```
###启动Redis
```
 % cd src
 % ./redis-server			#使用默认的redis.conf启动Redis
 % ./redis-server /path/to/redis.conf 	#使用自己的redis.conf启动Redis
 % ./redis-server --port 9999 --slaveof 127.0.0.1 6379 	#通过命令行改参数
 % ./redis-server /etc/redis/6379.conf --loglevel debug 
 ```
#### 通过redis-cli跟Redis-server交互
```
 % cd src
 % ./redis-server			#启动redis server
 % ./redis-cli				#另起一个terminal，启动redis-cli
    redis> ping
    PONG
    redis> set foo bar
    OK
    redis> get foo
    "bar"
    redis> incr mycounter
    (integer) 1
    redis> incr mycounter
    (integer) 2
    redis> 
```
###官网交互式入门手册 [http://try.redis.io/](http://try.redis.io/)

####查看帮助
```
help			#查看Redis所有帮助
help SETNX		#查看SETNX命令的帮助
```
####Key-Value:Redis支持的最重要的数据结构
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
####List:  Redis支持的有序集合, 提供了RPUSH, LPUSH, LLEN, LRANGE, LPOP, RPOP等操作。
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
#####Set: Redis支持的无序集合，集合里的元素必须唯一，Redis 提供了以下几种Set操作：SADD, SREM, SISMEMBER, SMEMBERS,SUNION.
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
 
#####Hashes: Redis支持哈希,用来处理从一个string映射到多个string的情况，(eg: A User with a number of fields like name, surname, age, and so forth):
```
HSET user:1000 name "John Smith"
HSET user:1000 email "john.smith@example.com"
HSET user:1000 password "s3cret"
HGETALL user:1000			#用HGETALL返回哈希所有的值
也可以简单的一次性赋所有值：
HMSET user:1001 name "Mary Jones" password "hidden" email "mjones@example.com"
HGET user:1001 name => "Mary Jones"
```
###官方入门文档之——Redis数据类型和抽象介绍:[An introduction to Redis data types and abstractions](http://redis.io/topics/data-types-intro)
>说Redis是key-value存储不准确，它准确地说是`data structures server`，它支持很多数据结构存储，比如下面的：

```
1. Binary-safe 的string.  
2. Lists:  有序的string列表
3. Sets:  唯一的，无序的string集合
4. Sorted sets: 有序的集合，类似Sets，区别是它的每一个string元素都关联一个浮点值叫做score，Sorted sets中的元素是有序的，你可以做类似取前10个元素，后10个元素这样的操作
5. Hashes：哈希，一个string映射到多个string。 
6. Bit maps : 可以对string做类似bits一样的操作。设置或清除特定的单一bits，数出所有bits值为1的，找出第一个bit这类操作。
7. HyperLogLogs: 
```
####Redis Strings
- Redis里的key是 binary safe的，就是说你可以使用任何的binary序列作为key，可以是string，也可以是JEPG文件，也可以是empty string
- Redis里的values也可以是任何值或者jpeg图片之类的，但是大小不能超过512M
- 除了INCR，还有INCRBY, DECR，DECRBY等命令，用法大同小异。
- 还有GETSET, MGET, MSET这类命令也很常用。

####Redis Lists
>Redis里说的Lists是基于`Linked Lists(链表)`，不像`Python`里说的Lists是基于`Array(数组)`。因为基于链表，所有你往一个有10个元素的Lists里插入和往一个拥有10万个元素的Lists插入，用的时间都是一样的短，这一点跟基于Array的不一样。

- LTRIM命令可以对List截取，剩下部分丢弃。`ltrim mylist 0 2`

####Redis Hashes
- 有 HMSET和 HMGET命令，用于一次性设置/取回多个值
- 有HINCRBY命令，可以对值做加法处理。

####Redis Sets
####Redis Sorted sets
####Bitmaps
####HyperLogLogs