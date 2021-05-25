# 浅析 URL

## 一、URL

URL（Uniform Resource Locator 超文本传输协议）由协议、域名或IP、端口号、路径、查询字符串，锚点组成。

协议是指HTTP和HTTPS。

IP用于定位一台设备，或者封装数据报文以便和其他设备交流。域名是IP的别称。

一台机器可以提供很多服务。每个服务一个号码，这个号码就叫端口号。

路径用于请求不同的页面；查询字符串用于在同一个页面查询不同的内容；锚点用于查看同一个内容的不同的位置。

## 二、DNS

DNS的作用是将域名和IP对应起来。

通过nslookup命令可以查询一个域名对应的所有IP。在命令行中的输入nslookup+要查询的域名。回车后，可以看到Non-authoritative answer:命令行下面有一个或多个Address，Address后面的一串数字就是IP。

比如查询baidu.com对应的所有IP：

```shell
nslookup baidu.com
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	baidu.com
Address: 39.156.69.79
Name:	baidu.com
Address: 220.181.38.148
```

## 三、IP

IP用于定位一台设备，或者封装数据报文以便和其他设备交流。

使用ping命令可以获取当前设备访问一个域名所对应的IP。在命令行中输入ping+域名，回车即可。

## 四、域名

域名就是对IP的别称。

一个域名可以对应不同的IP，这个叫做均衡负载。这是为了防止一台机器扛不住。

一个IP可以对应不同的域名，这个叫做共享主机。一般资金不宽裕的开发者会这么做。