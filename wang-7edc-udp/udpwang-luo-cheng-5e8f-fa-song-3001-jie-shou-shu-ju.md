# UDP网络程序-发送、接收数据
---
## UDP发送数据


```
# 导入模块
import socket

# 判断程序的入口
if __name__ == '__main__':

    # 创建udp套接字
    """
    参数1:AF_INET -> ipv4 AF_INET6 -> ipv6
    参数2:SOCK_STREAM -> TCP SOCK_DGRAM -> UDP
    """
    upd_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    # 发送数据
    # 准备数据
    send_content = "来自ubuntu的问候"
    # 字符串转成二进制 编码 (gbk utf-8)
    send_data = send_content.encode("gbk")
    # 发送数据
    # 参数1: 发送的二进制数据
    # 参数2: 元组("ip地址", 端口号)
    upd_socket.sendto(send_data, ("192.168.106.90", 6666))
    # 关闭套接字
    upd_socket.close()

```


## UDP接收数据


```
import socket

if __name__ == '__main__':

    # 创建udp套接字
    udp_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    # 准备数据
    send_data = "你好".encode("gbk")
    # 发送数据
    udp_socket.sendto(send_data, ("192.168.106.90", 6666))
    # 接收数据
    # 1024 一次接收的数据最大字节数
    recv_data, ip_part = udp_socket.recvfrom(1024)
    # 二进制转字符串
    recv_content = recv_data.decode("gbk")
    print("ip:%s[%s]:%s" % (ip_part[0], ip_part[1], recv_content))
    # 关闭套接字
    udp_socket.close()
```

