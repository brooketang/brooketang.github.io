# 垃圾VPS可堪一战


垃圾VPS套CloudFlare优选ip可堪一战
## [GCORE](https://ruhosting.gcorelabs.com/)
* 88.00 RUB / Month 按天计费。
* Khabarovsk 伯力 1x|512MB|7GB SSD|100M|500GB 电信，联通直联，延迟低
* Amsterdam  阿姆斯特丹 1x|512MB|7GB SSD|500M|1000GB 便宜，量大，欧洲中心
* visa充卢布，支付宝只能充欧元不划算

## [Dedipath](https://dedipath.com/ssd-vps)
* Los Angeles 洛杉矶 1x|512MB|10 GB SSD|1 Gbps|Unmetered	~~$20~~ $10/YR(半价优惠码:LRA2SXDI20 )
* 美西|便宜|无限量

## [EUserv](https://www.euserv.com/en/virtual-private-server/root-vserver/v2/vs2-free.php)
* Thüringen DE 德国 图林根 1x|1GB|10GB SSD|1G|1000GB
* 免费|纯IPV6|~~一个月~~[Github Actions](https://github.com/CokeMine/EUserv_extend)

## [Scaleway](https://www.scaleway.com/fr/tarifs/)
* Amsterdam  阿姆斯特丹 1x|1G|10GB NVMe|100M|Unmetered 便宜，量大，欧洲中心
* ~~0.0025 €/hour~~IPV6 0.0005 €/hour × 24 × 31 = 0.372 €/m (?+税?)

##### 修改ssh端口
```shell
vi /etc/ssh/sshd_config
i
Port 2222 #Port 22=>Port xxx
esc
:wq
systemctl restart sshd
```
