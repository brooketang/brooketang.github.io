# Xray套用CloudFlare优选ip

套壳机场越来越差，Xray套用CloudFlare优选ip可堪一战
## Debian X64
#### 开启BBR加速

```shell
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
lsmod | grep bbr
```
 *OpenVZ平台Google BBR加速TCP之Rinetd方式*
```shell
#适用于单网卡（单IP）服务器：
wget https://github.com/tcp-nanqinlang/lkl-rinetd/releases/download/1.1.0/tcp_nanqinlang-rinetd-debianorubuntu.sh
bash tcp_nanqinlang-rinetd-debianorubuntu.sh
#如果提示only support OpenVZ !，则使用下面这个脚本
wget https://github.com/tcp-nanqinlang/lkl-rinetd/releases/download/1.1.0-nocheckvirt/tcp_nanqinlang-rinetd-debianorubuntu-nocheckvirt.sh
bash tcp_nanqinlang-rinetd-debianorubuntu-nocheckvirt.sh
```
```shell
#适用于多网卡（多IP）服务器，会为所有网卡（所有IP）提供加速：
wget https://github.com/tcp-nanqinlang/lkl-rinetd/releases/download/1.1.0/tcp_nanqinlang-rinetd-debianorubuntu-multiNIC.sh
bash tcp_nanqinlang-rinetd-debianorubuntu-multiNIC.sh
#如果提示only support OpenVZ !，则使用下面这个脚本
wget https://github.com/tcp-nanqinlang/lkl-rinetd/releases/download/1.1.0-nocheckvirt/tcp_nanqinlang-rinetd-debianorubuntu-nocheckvirt-multiNIC.sh
bash tcp_nanqinlang-rinetd-debianorubuntu-nocheckvirt-multiNIC.sh
```
接着按照提示完成操作。
#### 搭建Xray
* 更新系统
```shell
apt update -y #更新
apt install -y wget #安装工具组件
```
* 执行Xray安装脚本
```shell
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```
该脚本运行一次以后，命令行输入 `vasma` 可重复调出该脚本使用。
* 选择Xray
* CloudFlare 解析ip时，先关闭CDN，部署完毕，域名能打开伪装页后再激活小云朵，在SSL/TLS中要选完全（端到端加密，使用服务器上的自签名证书）
* 部分vps在重装系统后nginx会提示80端口被占用，输入下面命令强行释放80端口
```shell
CMD=`lsof -i:"80" | awk '{print $1}' | grep -v "COMMAND" | sort -u` && systemctl disable ${CMD} && systemctl stop ${CMD} && killall -9 ${CMD}
```
* 其余按照提示完成操作。
* 找到`===================VLESS WS TLS CDN===========================`项，`Port`,`id`,`tls`,`host`,`path`为有效参数。
#### 设置参数
下载[better-cloudflare-ip](https://github.com/badafans/better-cloudflare-ip) 相应版本，运行相应脚本，获取`优质ip`。
* 地址        <==     `优质ip`
* 端口        <==     `Port`
* id          <==     `id`
* 流控        <==      
* 加密        <==      none
* 协议        <==      ws/websocket 
* 伪装        <==       none
* 伪装域名    <==         `host`
* path       <==          `path`
* tls        <==      tls
* 证书验证    <==        false

