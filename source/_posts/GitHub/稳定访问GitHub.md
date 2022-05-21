---
title: 稳定访问 GitHub
date: 2022-05-21 21:15:54
tags:
	- GitHub
---

通过本地 Nginx 代理的方式， 稳定访问 GitHub

<!-- more -->


## 创建证书

生成 key


```bash
openssl genrsa 2048 > ca.key
```

定义证书信息

```bash
export SUBJ="/C=CN/ST=ST$RANDOM/O=O$RANDOM/OU=OU$RANDOM/CN=CN$RANDOM/emailAddress=$RANDOM@localhost"
```

生成证书

```bash
openssl req -new -x509 -days `expr \( \`date -d 99991231 +%s\` - \`date +%s\` \) / 86400 + 1`   -key ca.key -out ca.pem -subj $SUBJ -extensions v3_ca
```

## 创建 Nginx 证书


生成 Key

```bash
openssl genrsa 2048 > nginx.key
```

生成 nginx 证书


```bash
openssl req -new -nodes -key nginx.key -out nginx.csr -subj $SUBJ
```

```bash
openssl x509 -req -days `expr \( \`date -d 99991231 +%s\` - \`date +%s\` \) / 86400 + 1`  -in nginx.csr -out nginx.pem -CA ca.pem -CAkey ca.key -set_serial 0 -extensions CUSTOM_STRING_LIKE_SAN_KU -extfile <( cat << EOF
[CUSTOM_STRING_LIKE_SAN_KU]
subjectAltName=IP:127.0.0.1, IP: ::1 ,DNS:github.com, DNS:*.github.com, DNS:githubusercontent.com, DNS:*.githubusercontent.com
keyUsage = nonRepudiation, digitalSignature, keyEncipherment
EOF
)
```

## 添加证书到系统


### Ubuntu 22.04

转换证书格式

```bash
openssl x509 -in ./ca.pem -out ./ca.crt
```

复制证书到 `update-ca-certificates` 可识别目录

```bash
sudo cp ca.crt /usr/local/share/ca-certificates
```

更新系统证书

```bash
sudo update-ca-certificates 
```

输出 `1 added` 表示一个添加成功

```
Updating certificates in /etc/ssl/certs...
rehash: warning: skipping ca-certificates.crt,it does not contain exactly one certificate or CRL
1 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
```

## Nginx 配置

### 安装 Nginx


```bash
sudo apt install nginx -y
```



### 证书配置


```bash
sudo mkdir /etc/nginx/ca -p
```

```bash
sudo cp nginx.key nginx.pem /etc/nginx/ca
```


### Nginx 配置

```bash
upstream github-com {
    server 140.82.113.4:443;
}
upstream githubusercontent-com {
    server 185.199.108.133:443;
    server 185.199.109.133:443;
    server 185.199.110.133:443;
    server 185.199.111.133:443;
}
upstream cloudflare {
    server 1.0.0.1:443;
}

map $host $default_http_host {
    hostnames; # 不写这个会让你什么都匹配不出来
    default                     cloudflare; # almost always 403
    .github.com                 github-com;
    .githubusercontent.com      githubusercontent-com;
}

server {
    listen 443 ssl default_server;

    ssl_certificate ca/nginx.pem;
    ssl_certificate_key ca/nginx.key;

    allow 127.0.0.0/8;
    deny all;

    location / {
        proxy_pass https://$default_http_host;
        proxy_set_header Host $http_host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Real_IP $remote_addr;
        proxy_set_header User-Agent $http_user_agent;
        proxy_set_header Accept-Encoding '';
        proxy_buffering off;
    }
}

server {
    listen 80 default_server;
    allow 127.0.0.0/8;
    deny all;
    rewrite ^(.*) https://$host$1 permanent;
}
```


## 配置 Hosts

添加以下配置

```
127.0.0.1  localhost raw.github.com githubusercontent.com cloud.githubusercontent.com camo.githubusercontent.com gist.github.com github.com raw.githubusercontent.com user-images.githubusercontent.com avatars3.githubusercontent.com avatars2.githubusercontent.com avatars1.githubusercontent.com avatars0.githubusercontent.com avatars.githubusercontent.com
```


## 浏览器添加证书


搜索显示浏览器会自动信任系统根证书，如果浏览器无法访问，手动添加证书


### Firefox 浏览器


1. 设置
2. 隐私安全
	- 安全
		- 证书 -> 查看证书
		- 证书颁发机构 -> 导入 -> `ca.pem` -> 确定
3. 重启火狐浏览器


## Git Clone


Git Clone 错误解决方法

Nginx 配置文件尾部追加以下内容

```

```

`~/.ssh/config` 添加以下内容


```
Host github.com
    Port 12345
    HostName %h
```


环境变量添加以下内容

```
export GIT_SSL_NO_VERIFY=1
```






参考文章

- [https://zhuanlan.zhihu.com/p/411165246](https://zhuanlan.zhihu.com/p/411165246)







