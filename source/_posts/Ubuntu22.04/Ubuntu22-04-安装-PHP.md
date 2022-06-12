---
title: Ubuntu22.04 安装 PHP
date: 2022-05-21 22:08:20
tags:
	- Ubuntu22.04
cover: https://blog.image.codedemo.vip/Ubuntu22.04%2Fphp_PNG35.png
---

Ubuntu22.04 安装并使用不同版本的 PHP

<!-- more -->


## 安装 PHP

添加源仓库

```bash
sudo add-apt-repository ppa:ondrej/php
```

安装 PHP 7.3

```bash
sudo apt install php7.3-fpm php7.3-cli php7.3-mbstring php7.3-zip php7.3-mysql php7.3-xml php7.3-gd php7.3-bcmath
```

安装 PHP 7.4

```bash
sudo apt install php7.4-fpm php7.4-cli php7.4-mbstring php7.4-zip php7.4-mysql php7.4-xml php7.4-gd php7.4-bcmath php7.4-curl
```

安装 PHP 8.0

```bash
sudo apt install php8.0-cli php8.0-fpm php8.0-xml php8.0-mbstring php8.0-curl php8.0-gd
```

## 使用不同版本PHP

### 域名配置

使用命令 `sudo vim /etc/hosts` 修改 hosts 文件, 添加域名解析

```
127.0.0.1	73.php.cn
127.0.0.1	74.php.cn
```

### 安装 Nginx

安装 Nginx

```bash
sudo apt install -y nginx
```

### 权限配置

使用命令 `whoami` 查看当前用户名, 比如: 当前用户为 demodeom

```
demodeom@pop-os:~$ whoami
demodeom
```

修改 Nginx 配置 `sudo vim /etc/nginx/nginx.conf `

```
user demodeom;
```

修改 PHP7.3 的配置 `sudo vim /etc/php/7.3/fpm/pool.d/www.conf`

```
user = demodeom
group = demodeom

listen.owner = demodeom
listen.group = demodeom
```


修改 PHP7.4的配置 `sudo vim /etc/php/7.4/fpm/pool.d/www.conf`

```
user = demodeom
group = demodeom

listen.owner = demodeom
listen.group = demodeom
```

重启 Nginx 、PHP7.3 、 PHP7.4 服务

```
sudo service nginx restart 
sudo service php7.3-fpm restart 
sudo service php7.4-fpm restart
```

### 创建测试脚本

创建项目目录

```
mkdir ~/www/73.php.cn -p
mkdir ~/www/74.php.cn -p
```

分别在 `~/www/73.php.cn` 和 `~/www/74.php.cn` 目录下创建 `index.php` ， 文件内容如下

```php
<?php

echo phpinfo();
```
 
### Nginx 配置


使用命令 `sudo vim /etc/nginx/sites-available/73.php.cn.conf` 创建配置文件， 内容如下

```
server {
	listen 80;
	root /home/wyj/www/73.php.cn;
	index index.php index.html index.htm index.nginx-debian.html;
	server_name 73.php.cn;
	location / {
		try_files $uri $uri/ =404;
	}
	location ~ \.php$ {
		include snippets/fastcgi-php.conf;
		fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
	}
}

```

使用命令 `sudo vim /etc/nginx/sites-available/74.php.cn.conf` 创建配置文件， 内容如下

```
server {
	listen 80;
	root /home/wyj/www/74.php.cn;
	index index.php index.html index.htm index.nginx-debian.html;
	server_name 74.php.cn;
	location / {
		try_files $uri $uri/ =404;
	}
	location ~ \.php$ {
		include snippets/fastcgi-php.conf;
		fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
	}
}
```

使用配置

```bash
sudo ln -s /etc/nginx/sites-available/73.php.cn.conf /etc/nginx/sites-enabled/73.php.cn.conf
sudo ln -s /etc/nginx/sites-available/74.php.cn.conf /etc/nginx/sites-enabled/74.php.cn.conf
```

重启 Nginx

```bash
sudo service nginx restart 
```


### 测试


访问 [http://73.php.cn](http://73.php.cn) 即可看到 PHP Version 7.3.27-9+ubuntu20.04.1+deb.sury.org+1

访问 [http://74.php.cn](http://74.php.cn) 即可看到 PHP Version 7.4.15

