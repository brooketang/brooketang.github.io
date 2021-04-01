# openssl生成根证书


# 自签发证书


根证书是CA认证中心给自己颁发的证书,是信任链的起始点.这里我们自己做CA使用openssl命令来生成根证书.

#### 生成私钥
```shell
openssl genrsa -out key.pem 2048
```
* genrsa    使用RSA算法产生私钥
* -out      输出文件名（路径）
* 2048      指定私钥长度

#### 生成根证书
生成X509格式的自签名证书
```shell
openssl req -x509 -new -days 365 -key key.pem -out cert.crt
```
整个提示将如下所示：
```
OutputCountry Name (2 letter code) [AU]:CN
State or Province Name (full name) [Some-State]:Beijing
Locality Name (eg, city) []:Beijing
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Google, Inc.
Organizational Unit Name (eg, section) []:Test CA ROOT
Common Name (e.g. server FQDN or YOUR name) []:Test CA ROOT
Email Address []:G@G.CN
```
* req   执行证书签发命令
* -new  新证书签发请求
* -days   证书的有效期（天）
* -key  指定私钥文件名（路径）
* -out  输出文件名（路径）
* -subj "/C=CN/ST=Guangdong/L=Shenzhen/O=testo/OU=testg/CN=testca"
* -subj 参数中填写的是证书信息
* C 是国家编号, 2位数
* ST 是省份
* L 是城市名
* O 是组织名
* OU 是组名
* CN 是证书拥有者名称

##### 到这里根证书就制作好了,开始使用
