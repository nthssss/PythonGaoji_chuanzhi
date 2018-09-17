# UDP绑定端口问题

```text
import socket

if __name__ == '__main__':

    # 创建udp套接字
    udp_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    # 绑定端口
    # 元组("ip地址不绑定随机获取", 绑定的端口)
    udp_socket.bind(("", 7788))
    # 准备数据
    send_data = "第四天发送".encode("gbk")
    # 发送数据
    udp_socket.sendto(send_data, ("192.168.106.69", 6677))
    # 关闭套接字
    udp_socket.close()
```

