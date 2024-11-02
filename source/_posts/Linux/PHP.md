---
title: PHP
date: 2024-10-20 17:52:58
tags:
	- Linux
---


PHP（超文本预处理器）是一种广泛使用的开源服务器端脚本语言，特别适合用于 Web 开发。它能够嵌入 HTML 中，轻松创建动态网页和应用程序。PHP 拥有丰富的功能，支持数据库连接、会话管理和文件操作等。由于其简单易学和强大的社区支持，PHP 成为许多内容管理系统（如 WordPress 和 Drupal）的基础语言。随着不断的更新和扩展，PHP 继续在 Web 开发领域保持重要地位，适合从小型项目到大型企业应用的各种开发需求。

<!-- more -->


将此 PPA 添加到您的系统中

```
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```


```
sudo apt install php8.0-cli php8.0-fpm php8.0-xml php8.0-mbstring php8.0-curl php8.0-gd
```

```
sudo apt install php8.3-cli php8.3-fpm php8.3-xml php8.3-mbstring php8.3-curl php8.3-gd php8.3-intl php8.3-zip php8.3-mysql
```

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('composer-setup.php');"
sudo mv composer.phar /usr/local/bin/composer
```