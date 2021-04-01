# 纯IPV6访问IPV4

DNS64是与NAT64搭配使用的，原理很简单，修改你的DNS到DNS64提供者的DNS，当你发出向解析到IPv4的域名的请求后，DNS会将IPv4地址按照一定格式嵌入IPv6地址中；这个返回IPv6地址会指向NAT64的服务器，NAT64网关会按照它包含的信息获取IPv4的数据并转发给你，这样一来你就能够直接访问IPv4的网站了。
## DNS
http://www.trex.fi/2011/dns64.html

```
2001:67c:2b0::4
2001:67c:2b0::6
```
https://go6lab.si/current-ipv6-tests/nat64dns64-public-test/

```
2001:67c:27e4:15::6411
2001:67c:27e4::64
```
一般修改/etc/resolv.conf的namesever值即可.

DNS64的好处是配置方便。弊端服务商会记录你三天的浏览记录以防止用于不法用途，且NAT64服务器到你的服务器速度未必非常理想。


## 一键写入DNS
写入前建议先备份/etc/resolv.conf
```
mv /etc/resolv.conf /etc/resolv.conf.bak
echo -e "nameserver 2001:67c:2b0::4\nnameserver 2001:67c:2b0::6" > /etc/resolv.conf
```
