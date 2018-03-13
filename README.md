# Dubbo Plugin for Apache JMeter

# 介绍

Dubbo Plugin for Apache JMeter是用来在Jmeter里更加方便的测试Dubbo接口而开发的插件

# 项目地址

具体可以查看blog地址：https://ningyu1.github.io/site/post/60-jmeter-plugins-dubbo-support/

[项目地址:jmeter-plugins-dubbo](https://github.com/ningyu1/jmeter-plugins-dubbo) 

<a href="https://github.com/ningyu1/jmeter-plugins-dubbo/releases"><img src="https://img.shields.io/github/release/ningyu1/jmeter-plugins-dubbo.svg?style=social&amp;label=Release"></a>&nbsp;<a href="https://github.com/ningyu1/jmeter-plugins-dubbo/stargazers"><img src="https://img.shields.io/github/stars/ningyu1/jmeter-plugins-dubbo.svg?style=social&amp;label=Star"></a>&nbsp;<a href="https://github.com/ningyu1/jmeter-plugins-dubbo/fork"><img src="https://img.shields.io/github/forks/ningyu1/jmeter-plugins-dubbo.svg?style=social&amp;label=Fork"></a>&nbsp;<a href="https://github.com/ningyu1/jmeter-plugins-dubbo/watchers"><img src="https://img.shields.io/github/watchers/ningyu1/jmeter-plugins-dubbo.svg?style=social&amp;label=Watch"></a> <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-blue.svg"></a>

# 版本更新

[V1.2.0](https://github.com/ningyu1/jmeter-plugins-dubbo/releases/tag/V1.2.0)
1. 使用gson进行json序列化、反序列化
2. 使用dubbo泛化调用方式重构反射调用方式
3. 支持复杂类型、支持泛型，例如："java.lang.List<ResourceVo>,Map<String,ResourceVo> map,List<Map<String, ResourceVo>> list"

本次版本主要对反射参数类型进行了增强，支持复杂类型、支持参数泛型，可以参考如下的参数对照表：

|Java类型|paramType|paramValue|
|:------|:--------|:---------|
|int|int|1|
|double|double|1.2|
|short|short|1|
|float|float|1.2|
|long|long|1|
|byte|byte|字节|
|boolean|boolean|true或false|
|char|char|A，如果字符过长取值为："STR".charAt(0)|
|java.lang.String|java.lang.String或String或string|字符串|
|java.lang.Integer|java.lang.Integer或Integer或integer|1|
|java.lang.Double|java.lang.Double或Double|1.2|
|java.lang.Short|java.lang.Short或Short|1|
|java.lang.Long|java.lang.Long或Long|1|
|java.lang.Float|java.lang.Float或Float|1.2|
|java.lang.Byte|java.lang.Byte或Byte|字节|
|java.lang.Boolean|java.lang.Boolean或Boolean|true或false|
|JavaBean|com.package.Bean|{"service":"test1","url":"test-${__RandomString(5,12345,ids)}","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001}|
|java.util.Map以及子类|java.util.Map以及子类|{"service":"test1","url":"test-${__RandomString(5,12345,ids)}","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001}|
|java.util.Map&#60;String,JavaBean> |java.util.Map|{"name":{"service":"test1","url":"test-${__RandomString(5,12345,ids)}","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001},"value":{"service":"test1","url":"test","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001}}|
|java.util.HashMap&#60;Object,Object>|java.util.HashMap|{"name":{"service":"test1","url":"test-${__RandomString(5,12345,ids)}","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001},"value":{"service":"test1","url":"test","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001}}|
|java.util.Collection以及子类|java.util.Collection以及子类|["a","b"]|
|java.util.List&#60;String>|java.util.List|["a","b"]|
|java.util.List&#60;JavaBean>|java.util.List|[{"service":"test1","url":"test-${__RandomString(5,12345,ids)}","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001},{"service":"test1","url":"test-${__RandomString(5,12345,ids)}","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001}]|
|java.util.List&#60;Map&#60;Object, JavaBean>>|java.util.List|[{"name":{"service":"test1","url":"test-${__RandomString(5,12345,ids)}","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001},"value":{"service":"test1","url":"test","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001}},{"name":{"service":"test1","url":"test-${__RandomString(5,12345,ids)}","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001},"value":{"service":"test1","url":"test","action":"GET","enabled":true,"isPublic":false,"appId":8,"menuId":30001}}]|
|java.util.List&#60;Long>|java.util.List| [1,2,3]|
|java.util.ArrayList&#60;Object>|java.util.ArrayList|["ny",1,true]|

[V1.1.0](https://github.com/ningyu1/jmeter-plugins-dubbo/releases/tag/V1.1.0)
1. 工具界面输入信息均支持使用jmeter变量${var}，函数${__RandomString(5,12345,ids)}进行参数化。
2. 接口参数类型与值支持使用jmeter变量${var}，函数${__RandomString(5,12345,ids)}进行参数化

ps.很遗憾的是升级插件后以前的jmx文件无法打开需要重新创建jmx脚本

下面是测试截图 
![1](https://user-images.githubusercontent.com/3387548/37082704-310fa8ce-2228-11e8-88ff-f278ce1a0009.png)
![2](https://user-images.githubusercontent.com/3387548/37082705-315581b4-2228-11e8-930a-e246f18dc371.png)
![3](https://user-images.githubusercontent.com/3387548/37082707-319ca698-2228-11e8-8b20-47cf315ee267.png)

[V1.0.0](https://github.com/ningyu1/jmeter-plugins-dubbo/releases/tag/V1.0.0)
1. 增加了DubboSample，协议支持：zookeeper、dubbo
2. 增加调用接口与方法以及参数支持
3. 主要用于Dubbo RPC接口测试

# DubboSample使用

## 支持Jmeter版本

Jmeter版本：3.0

## 插件安装

插件包可以去`github`上下载。将插件包放入Jmeter的lib的ext下。

```
${Path}\apache-jmeter-3.0\lib\ext
```

如果使用的是：`jmeter-plugins-dubbo-1.0.0-SNAPSHOT-jar-with-dependencies.jar`包含所有依赖，推荐使用这个包。

如果使用的是：`jmeter-plugins-dubbo-1.0.0-SNAPSHOT.jar`需要自行添加插件的依赖包，依赖包版本如下：

```
dubbo-2.5.3.jar
javassist-3.15.0-GA.jar
zookeeper-3.4.6.jar
zkclient-0.1.jar
jline-0.9.94.jar
netty-3.7.0-Final.jar
slf4j-api-1.7.5.jar
log4j-over-slf4j-1.7.5.jar
```

## 插件使用

启动`Jmeter`添加`DubboSample`如下图：

![](https://ningyu1.github.io/site/img/jmeter-plugins-dubbo/1.png)

添加后能看到`DubboSample`的具体操作页面，如下图：

![](https://ningyu1.github.io/site/img/jmeter-plugins-dubbo/2.png)

根据上图提示传入值即可。

接口以及接口依赖包请添加到`classpath`下，可以放在`apache-jmeter-3.0\lib\ext`下，也可以通过下图方式添加：

![](https://ningyu1.github.io/site/img/jmeter-plugins-dubbo/3.png)

## 运行结果

![](https://ningyu1.github.io/site/img/jmeter-plugins-dubbo/4.png)

![](https://ningyu1.github.io/site/img/jmeter-plugins-dubbo/5.png)

![](https://ningyu1.github.io/site/img/jmeter-plugins-dubbo/6.png)

## 注意事项

1. 当使用zk，address填入zk地址（集群地址使用","分隔）,使用dubbo直连，address填写直连地址和服务端口
2. `timeout`：服务方法调用超时时间(毫秒)
3. `version`：服务版本，与服务提供者的版本一致
4. `retries`：远程服务调用重试次数，不包括第一次调用，不需要重试请设为0
5. `cluster`：集群方式，可选：failover/failfast/failsafe/failback/forking
6. 接口需要填写类型完全名称，含包名
7. 参数支持任何类型，包装类直接使用`java.lang`下的包装类，小类型使用：`int、float、shot、double、long、byte、boolean、char`，自定义类使用类完全名称。
8. 参数值，基础包装类和基础小类型直接使用值，例如：int为1，boolean为true等，自定义类与`List`或者`Map`等使用json格式数据。
9. 更多dubbo参数查看官方文档：[http://dubbo.io/books/dubbo-user-book/references/xml/dubbo-reference.html](http://dubbo.io/books/dubbo-user-book/references/xml/dubbo-reference.html)
