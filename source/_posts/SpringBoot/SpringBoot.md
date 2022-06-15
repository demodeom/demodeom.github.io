---
title: SpringBoot
date: 2022-05-09 20:08:12
tags:
---

SpringBoot 从项目创建、项目开发 到 项目部署

<!-- more -->

## 创建 SpringBoot 项目

### 初始化项目

创建项目步骤

1. 访问 [https://start.spring.io/](https://start.spring.io/)
2. 配置项目
3. 添加依赖
4. 下载代码

配置说明

1. 
2. 
3. 

[![OPuAF1.png](https://s1.ax1x.com/2022/05/02/OPuAF1.png)](https://imgtu.com/i/OPuAF1)


### 使用阿里镜像


修改 `pom.xml` 文件 , `project` 标签下添加以下内容

```xml
<!--阿里云镜像加速-->
<repositories>
    <repository>
        <id>public</id>
        <name>aliyun</name>
        <url>https://maven.aliyun.com/repository/public</url>
        <releases>
            <enabled>true</enabled>
        </releases>
    </repository>
</repositories>
<!--阿里云镜像加速-->
<pluginRepositories>
    <pluginRepository>
        <id>public</id>
        <name>aliyun</name>
        <url>https://maven.aliyun.com/repository/public</url>
        <releases>
            <enabled>true</enabled>
        </releases>
        <snapshots>
            <enabled>false</enabled>
        </snapshots>
    </pluginRepository>
</pluginRepositories>
```

### 目录结构


domain jpa 实体
repository jpa 数据接口访问层
service 数据服务接口层
service.impl 数据服务接口实现层
controller 前端控制器层
utils 工具类库
config 配置类
dto 数据传输对象
vo 视图包装对象
constant 常量类


数据传输对象Data Transfer Object用于封装多个实体类domain之间的关系，不破坏原有的实体类结构
视图包装对象View Object用于封装客户端请求的数据，防止部分数据泄露如：管理员ID，保证数据安全，不破坏 原有的实体类结构


项目配置文件：resources/application.yml
静态资源目录：resources/static/  用于存放html、css、js、图片等资源
视图模板目录：resources/templates/ 用于存放jsp、thymeleaf等模板文件

参考文章

- [https://blog.csdn.net/qq_39615545/article/details/90172038](https://blog.csdn.net/qq_39615545/article/details/90172038)

## 控制器




## SpringSecurity

### 依赖

```
<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

### 初次体验

默认路由

- `/login`
- `/logout`

默认账号

- 用户名 `user`
- 用户临时密码 在标准输出中可以找到

```
Using generated security password: 2effbc5f-ca7c-4417-b4d0-b303c6984d8b
```

### 接入登录


#### 自定义 User

AdminUser

```java

```


#### 用户名、密码校验


```java
package com.example.demo.service;

import com.example.demo.domain.LoginUserDetails;
import com.example.demo.domain.User;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.core.userdetails.UsernameNotFoundException;
import org.springframework.stereotype.Service;

@Service
public class UserDetailService implements UserDetailsService {

    @Override
    public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
        User user = new User(1, "demo", "{noop}123456");

        return new LoginUserDetails(user);
    }
}
```

"{noop}" 表示密码无加密， 乌龟的腚(规定)

#### 自定义 UserDetails


```java 
package com.example.demo.domain;

import org.springframework.security.core.GrantedAuthority;
import org.springframework.security.core.userdetails.UserDetails;
import java.util.Collection;

public class LoginUserDetails implements UserDetails {
    private final User user;

    public LoginUserDetails(User user) {
        this.user = user;
    }

    @Override
    public Collection<? extends GrantedAuthority> getAuthorities() {
        return null;
    }

    @Override
    public String getPassword() {
        return user.getPassword();
    }

    @Override
    public String getUsername() {
        return user.getUserName();
    }

    @Override
    public boolean isAccountNonExpired() {
        return false;
    }

    @Override
    public boolean isAccountNonLocked() {
        return false;
    }

    @Override
    public boolean isCredentialsNonExpired() {
        return true;
    }

    @Override
    public boolean isEnabled() {
        return true;
    }
}
```
### 自定义加密方式

```java
package com.example.security;

import org.springframework.context.annotation.Bean;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;

public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Bean
    public PasswordEncoder passwordEncoder()
    {
        return new BCryptPasswordEncoder();
    }
}
```

```java
 User user = new User(1, "demo", "$2a$10$/yt3T6kamOoLJmBYefsWxuyylLtNb6LyrzYK3H4CvyDrsn6cUD.Ly");
```

`$2a$10$/yt3T6kamOoLJmBYefsWxuyylLtNb6LyrzYK3H4CvyDrsn6cUD.Ly` 是 `123456` 加密之后的结果


`org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;` 提供了两个方法， 

- encode 加密
- matches 校验密文是否匹配

```java
BCryptPasswordEncoder bCryptPasswordEncoder = new BCryptPasswordEncoder();
String cipherText = bCryptPasswordEncoder.encode("123456");
System.out.println(cipherText);
// $2a$10$2dwE.oxadWDqZx1voU6jCuXMJuqamx647pN94i3N5CZoqvAFNH1FC

boolean r = bCryptPasswordEncoder.matches("123456", cipherText);
if (r){
    System.out.println("密码正确");
}else {
    System.out.println("密码错误");
}
// 密码正确
``` 