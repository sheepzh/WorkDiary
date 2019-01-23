> 2019-01-10

> memcached tomcat

+ 问题描述：本地使用tomcat和memcached搭建开发环境时，每次登录之后都又跳转到了登录界面。

+ 环境版本：tomcat=8.0.0，memcached=1.4.5

+ 解决方案：
	
	+ tomcat未设置path路径，导致memcached在处理请求时无法正确获取相应的用户session，导致每次重定向至登录界面
	+ 修改tomcat的项目path即可解决

> 2019-01-17

> idea 日志输出 tomcat
    	
+ 问题描述：**idea前端返回报500错误，IntelliJ Idea控制台没有报错信息。**

+ 环境版本：idea=2018.2，tomcat=8.0.0，OS=x86-win7

+ 解决方案：
	+ 直接去用户目录下查看idea生成的日志：${USER_HOME}/.IntelliJIdea${version}/system/tomcat/${project}/logs/localhost-${date}.log
	
	+ 修改tomcat日志配置
	
		1. 打开${CATALINA_HOME}/conf/logging.properties
		2. 修改配置项org.apache.catalina.core.ContainerBase.[Catalina].[localhost].handlers = *.*.**.*
		3. 在原配置项后新加一个类，两者之间用英文逗号隔开：java.util.logging.ConsoleHandler


> 2019-01-21

> json-lib bean spring

+ 问题描述：**后台将数组的json字符串转换成beans时，返回java数组元素内的字段值全为null**

+ 环境版本：json-lib=1.9.1，java=1.8

+ 解决方案：

	* 阅读JSONObject源码可知，json-lib不支持对setter为builder格式的bean进行解析
	* 使用json-lib时不使用builder格式构建setters

> 2019-01-23

> springMVC 请求参数

+ 问题描述：**后台在请求中自动填充数组字段时，VO使用List<String\>类型进行参数接受时报错**

+ 解决方案：
	
	* 问题定位待查。
	* 前端拼接成字符串，后端再解析。