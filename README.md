# Dubbo Plugin for Apache JMeter

# 介绍

Dubbo Plugin for Apache JMeter是用来在Jmeter里面方便的测试Dubbo接口而开发的插件

# 项目地址

具体可以查看blog地址：https://ningyu1.github.io/site/post/60-jmeter-plugins-dubbo-support/

[项目地址:jmeter-plugins-dubbo](https://github.com/ningyu1/jmeter-plugins-dubbo) 

<a href="https://github.com/ningyu1/jmeter-plugins-dubbo/releases"><img src="https://img.shields.io/github/release/ningyu1/jmeter-plugins-dubbo.svg?style=social&amp;label=Release"></a>&nbsp;<a href="https://github.com/ningyu1/jmeter-plugins-dubbo/stargazers"><img src="https://img.shields.io/github/stars/ningyu1/jmeter-plugins-dubbo.svg?style=social&amp;label=Star"></a>&nbsp;<a href="https://github.com/ningyu1/jmeter-plugins-dubbo/fork"><img src="https://img.shields.io/github/forks/ningyu1/jmeter-plugins-dubbo.svg?style=social&amp;label=Fork"></a>&nbsp;<a href="https://github.com/ningyu1/jmeter-plugins-dubbo/watchers"><img src="https://img.shields.io/github/watchers/ningyu1/jmeter-plugins-dubbo.svg?style=social&amp;label=Watch"></a> <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-blue.svg"></a>

# DubboSample使用

## 支持Jmeter版本

Jmeter版本：3.0

## 插件安装

插件包可以去`github`上下载。将插件包放入Jmeter的lib的ext下。

```
${Path}\apache-jmeter-3.0\lib\ext
```

如果使用的是:`jmeter-plugins-dubbo-1.0.0-SNAPSHOT-jar-with-dependencies.jar`包含所有依赖，推荐使用这个包。

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
