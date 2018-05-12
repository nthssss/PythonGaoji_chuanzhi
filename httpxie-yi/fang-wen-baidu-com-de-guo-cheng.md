# 访问baidu.com的过程
---
 1.解析baidu.com对应的IP地址：
 - 使用arp获取默认网关的MAC地址；
 - 组织数据发送给默认网关（IP还是DNS服务器的IP，但是MAC地址是默认网关的MAC地址）；
 - 默认网关拥有转发数据的能力，把数据转发给路由器
 - 路由器根据自己的路由协议，选择一个合适的较快的路径转发数据给目的网关；
 - 目的网关（DNS服务器所在的网关）把数据转发给DNS服务器；
 - DNS服务器查询解析出baidu.com对应的IP地址，并原路返回请求这个域名的client;

2.得到了baidu.com对应的IP之后，发送TCP的三次握手，进行连接：
 - 使用HTTP协议发送请求数据给web服务器；
 - web服务器接到数据请求之后，通过查询自己的服务器得到相应的结果，原路返回给浏览器；
 - 浏览器接收到数据之后通过浏览器自己的渲染功能来显示这个网页；
 - 浏览器关闭TCP连接，即四次挥手结束，完成整个访问过程。