---
title: SpringBootSecurity
date: 2022-05-09 13:37:22
tags: 
    - SpringBoot
---

SpringBootSecurity 自动登录、自动鉴权

<!-- more -->


## 依赖

```
<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

## 初次体验

默认路由

- `/login`
- `/logout`

默认账号

- 用户名 `user`
- 用户临时密码 在标准输出中可以找到

```
Using generated security password: 2effbc5f-ca7c-4417-b4d0-b303c6984d8b
```

## 接入登录


### 自定义 User

AdminUser

```java

```


### 用户名、密码校验


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

### 自定义 UserDetails


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
## 自定义加密方式

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

## Token






