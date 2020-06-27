# springcoud-config
springcloud配置中心

1：收到更新config-client
每次修改配置需要向客户端发送该命令
curl -X POST "http://localhost:3355/actuator/refresh"


2.对于消息总线的发送命令：
    1:全部client生效的命令 curl -X POST "http://localhost:3344/actuator/bus-refresh"
    2：指定client生效的命令 curl -X POST "http://localhost:3344/actuator/bus-refresh/{distination}"  //{distination}指定服务name+指定端口号                       


问题：

1：关于连不上Rabbitmq的问题

检查你的配置对不对，如果连接rabbitmq的配置没问题，检查你的防火墙端口有没有开出来

默认连接端口是5672，看下你连接的端口是啥 

查看开放的端口：
firewall-cmd --list-ports
开放端口（修改后需要重启防火墙方可生效）：
firewall-cmd --zone=public --add-port=5672/tcp --permanent
重启防火墙：
firewall-cmd --reload



