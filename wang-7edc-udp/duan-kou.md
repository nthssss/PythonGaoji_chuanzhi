# IP地址、端口

## IP地址、端口

IP\(Internet Protocol 网络协议\) 端口：此处学习的端口是网络端口，一般分为知名端口和动态端口：

* 知名端口：0～1023
* 动态端口：1024～65535

## 根据端口号杀死进程：

-&gt; 根据程序端口号查看进程号 -&gt; 根据进程号杀死进程

Ubuntu&Mac

```text
lsof -i:portid  # 根据程序端口号查看进程号
kill -9 pid  # 根据进程号杀死进程
```

Windows

```text
netstat -aon|findstr "portid"  # 根据程序端口号查看进程号
taskkill /pid "pid" -f  # 根据进程号杀死进程
```

