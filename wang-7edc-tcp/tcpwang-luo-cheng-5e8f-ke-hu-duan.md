# TCP网络程序-客户端
---


```
# 导入模块
import socket

if __name__ == '__main__':

    # 创建tcp套接字
    tcp_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # 建立连接
    tcp_socket.connect(("192.168.106.69", 6677))
    # 准备数据
    send_data = "tcp客户端".encode("gbk")
    # 发送数据
    tcp_socket.send(send_data)
    # 接收数据
    recv_data = tcp_socket.recv(1024)
    # 解码
    recv_content = recv_data.decode("gbk")
    print(recv_content)
    # 接收数据
    recv_data = tcp_socket.recv(1024)
    # 解码
    recv_content = recv_data.decode("gbk")
    print(recv_content)
    # 关闭套接字
    tcp_socket.close()
```

