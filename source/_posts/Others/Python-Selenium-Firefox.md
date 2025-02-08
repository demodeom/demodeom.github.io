---
title: Python Selenium Firefox
date: 2024-09-09 21:50:08
tags:
---

为什么选择 Python ？ 因为 Python 脚本编写简单。
为什么选择 Selenium ？ 因为 JS 逆向、登录太复杂（有封号风险）。
为什么选择 Firefox ？ 因为 GoogleChrome 版本的 WebDriver 无法下载。

<!-- more -->

## 驱动

Firefox 版本的 WebDriver 是免费开源的，可以在 GitHub 下载， 下载地址 []()

## 驱动配置

### 方法1

将 驱动文件所在的目录添加到系统环境变量 Path

> PS: 此方法经常遇到 Firefox 无法启动问题

### 方法2

将驱动文件复制到项目脚本文件所在的目录

### 方法3

初始化浏览器


## 初始化浏览器

```python
from selenium import webdriver
driver = webdriver.Firefox()
```

## 窗口最大化

```python
driver.maximize_window()
```

## 访问网页

```python
baidu_url = "https://www.baidu.com"
driver.get(baidu_url)
```

## 查找元素

查找方式

```python
from selenium.webdriver.common.by import By
# ID = "id"
# XPATH = "xpath"
# LINK_TEXT = "link text"
# PARTIAL_LINK_TEXT = "partial link text"
# NAME = "name"
# TAG_NAME = "tag name"
# CLASS_NAME = "class name"
# CSS_SELECTOR = "css selector"
```

查找单个元素

```python
driver.find_element(By.CLASS_NAME, 'login-pwd')
```

查找多个元素

```python
driver.find_elements(By.TAG_NAME, 'input')
```

## 查找元素等待时间

```python
driver.implicitly_wait(30)
```

## 模拟输入

```python
# 1. 找到输入框
user_name_input = driver.find_element(By.CLASS_NAME, 'username')
# 2. 模拟输入
user_name_input.send_keys("13888888888")
```

## 模拟点击

```python
# 1. 找到登录按钮
login_button = driver.find_element(By.CLASS_NAME, 'login')
# 2. 模拟点击
login_button.click()
```

##  获取 Cookie

```python
# 获取 cookie
cookies = driver.get_cookies()
# 保存 cookie
cookie_file = "./cache/cookie.pkl"
pickle.dump(cookies, open(cookie_file, "wb"))
```

## 加载 Cookie

```python
cookie_file = "./cache/cookie.pkl"
cookies = pickle.load(open(cookie_file, "rb"))
for cookie in cookies:
    if isinstance(cookie.get('expiry'), float):
        cookie['expiry'] = int(cookie['expiry'])
    driver.add_cookie(cookie)
return True
```

## HTTPS 代理

```python
# 设置 https 代理
proxy = Proxy()
proxy.http_proxy = "127.0.0.1:8080"
proxy.ssl_proxy = "127.0.0.1:8080"

options = webdriver.FirefoxOptions()
options.proxy = proxy
options.set_capability("acceptInsecureCerts", True)

driver = webdriver.Firefox(options=options)
```

## 滚动滚动条

滚动条向下滚动 500 像素

```python
driver.execute_script("window.scrollBy(0,500)")
```

获取滚动条位置

```python
```





## 



















