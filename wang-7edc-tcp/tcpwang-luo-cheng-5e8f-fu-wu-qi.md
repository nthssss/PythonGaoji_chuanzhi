# TCP网络程序-服务器
---


```
import socket

if __name__ == '__main__':

    # 创建tcp服务端套接字(等待客户端与其建立连接)
    tcp_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # 立即释放端口
    # SOL_SOCKET 代表设置套接字的选项的级别 默认SOL_SOCKET
    # SO_BROADCAST 设置发送广播
    # SO_REUSEADDR 立即释放端口
    tcp_server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, True)
    # 绑定端口
    tcp_server_socket.bind(("", 4567))
    # 设置同一时刻允许多少客户端何其建立连接
    tcp_server_socket.listen(5)
    # client_socket 和当前这个建立连接成功的客户端进行收发数据
    client_socket, ip_part = tcp_server_socket.accept()
    # 发送数据
    send_data = "tcp服务端".encode("gbk")
    # 发送
    client_socket.send(send_data)
    # 接收数据
    recv_data = client_socket.recv(1024)
    # 解码
    recv_content = recv_data.decode("gbk")
    print("客户端%s[%s]:%s" % (ip_part[0], ip_part[1], recv_content))
    print(len(recv_content))
    # 关闭套接字 不再和对应的客户端进行收发数据
    client_socket.close()
    # 关闭套接字 不再等待其他新的客户端何其建立连接
    tcp_server_socket.close()
```


