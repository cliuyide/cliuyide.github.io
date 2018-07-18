---
  title: 【Nginx安装】CentOS7安装Nginx及配置
  date: 2018-07-17 
  categories: linux 
  tags: [linux,nginx,aliyun] 
---
# 【Nginx安装】CentOS7安装Nginx及配置
#### <https://blog.csdn.net/wxyjuly/article/details/79443432/> 原文地址

### 1.安装gcc gcc-c++(如新环境,未安装请先安装)
```
$ yum install -y gcc gcc-c++
```
### 2.安装PCRE库
```
$ cd /usr/local/
$ wget http://jaist.dl.sourceforge.net/project/pcre/pcre/8.33/pcre-8.33.tar.gz
$ tar -zxvf pcre-8.36.tar.gz
$ cd pcre-8.36
$ ./configure
$ make && make install
```
### 3.安装SSL库
```
$ cd /usr/local/
$ wget http://www.openssl.org/source/openssl-1.0.1j.tar.gz
$ tar -zxvf openssl-1.0.1j.tar.gz
$ cd openssl-1.0.1j
$ ./config
$ make && make install
```
### 4.安装zlib库存
```
$ cd /usr/local/
$ wget http://zlib.net/zlib-1.2.11.tar.gz
$ tar -zxvf zlib-1.2.11.tar.gz
$ cd zlib-1.2.11
$ ./configure
$ make && make install
```
### 5.安装nginx
```
$ cd /usr/local/
$ wget http://nginx.org/download/nginx-1.8.0.tar.gz
$ tar -zxvf nginx-1.8.0.tar.gz
$ cd nginx-1.8.0 
$ ./configure  $默认安装在/usr/local/nginx   
$ make  
$ make install
```
### 启动
```
/usr/local/nginx/sbin/nginx
```
我在按照原作者流程是遇到了一点小麻烦,在原来的基础上进行了小的修改.
最后遇到的一个问题就是nginx启动后无法访问该服务.
最后发现是阿里云安全组的问题(我的服务在阿里云上)
<https://www.jianshu.com/p/ec34db456c8b/>原文地址

直接在阿里云实例中，选择 网络与安全中的安全组。修改安全组规则。把http的80和https的443开放即可.









