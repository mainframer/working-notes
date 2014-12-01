#Watir, Selenium Web自动化学习
----------
###知识点难点
- 需要注意的是，有时候如果web元素找不到，看看其中是否包含有iFrame，如果包含有的话，需要加上frame前缀。  
- gem install ocra  ocra是可以一键将gems,scripts写好的脚本代码打包成.exe的工具 http://blog.sina.com.cn/s/blog_6f4a041a01012yhu.html  
- watir能做什么？注册机 秒杀器 外挂 Web跨站脚本漏洞检测工具的设计与实现 面向Web服务安全的漏洞扫描器的设计与实现 亚马逊海淘 BUX http://www.buxzhan.com probux真的能赚钱 univest http://www.tianyawz.cn
- Watir在fast speed模式下运行脚本很快
AutoIt:模拟鼠标，类似关闭弹窗等
有空可以研究一下淘宝的自动化框架：automan  http://www.taobaotest.com
用:id 和:name 定位要比用其他方式定位快！这两种定位方式不是由watir提供的，而是由InternetExploere提供的    
- frame简单的说就是在一个页面里可以套用其他的页面，但是可能我们在看页面的时候没有什么感觉，基本看不出来。但是在做自动化测试的时候，就一定要关注Frame，比方说页面里面有个frame，在这个frame里包含一个其他的页面，包含一个文本框，我们要向这个文本框里写内容要写成
`b.frame(:id=>"frame1").text_field(:id=>"name").set "rex"`

###框架和嵌套框架
代码如：

	<frameset cols="*,*">  
	<frame src="menu.htm" name="menu"> 
	<frame src="main.htm" name="main">
	</frameset>
用`ie.show_frames`可以打印出当前页面框架的数量和名称：

	irb(main):009:0> ie.show_frames
	there are 2 framesframe  
	index: 1 name: menuframe  
	index: 2 name: main
	=> 0..1
- Watir允许通过名称属性来访问框架，如：
`ie.frame(:name, "menu")`
- 如果要访问`menu`框架中的一个超链接`<a href="index.htm">Click Menu Item</a>`，可以
`ie.frame(:name, "menu").link(:text, "Click Menu Item").click`
嵌套框架
`ie.frame(:name, "frame").frame(:name, "nested_frame")`
- 不能set中文的问题,可以用value代替set，举例如下:

```
ie.text_field(:name, "loginname").set"中文账号" 
ie.text_field(:name, "loginname").value = "中文账号"
```
