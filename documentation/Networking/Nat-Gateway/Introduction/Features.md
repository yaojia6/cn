# 产品功能


京东云NAT网关提供SNAT，应用层网关(ALG)和流量监控功能



## SNAT

SNAT功能为VPC内无公网IP的虚机实例提供访问互联网的代理服务，同时阻止互联网主动连接这些虚机实例，起到了一定的安全防范作用。同时多个内网实例可通过一个NAT网关公网IP出公网，共享带宽。



## 应用层网关(ALG)

通过对应用层协议载荷(payload)中的IP和端口进行转换，进而支持协议之间跨NAT网关的正常通信，京东云NAT网关支持ICMP协议



## 流量监控

监控页面提供了公网入出速率（bps）、并发连接数、新建连接数、NAT网关丢包数、源端口耗尽丢包数等多个维度的数据，方便用户实时监控NAT网关流量健康状况
