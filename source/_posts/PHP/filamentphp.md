---
title: filamentphp
date: 2024-10-20 20:09:31
tags:
---

<!-- more -->

## 环境准备

安装 PHP 8.3

```bash
sudo apt install php8.3-cli php8.3-fpm php8.3-xml php8.3-mbstring php8.3-curl php8.3-gd php8.3-intl php8.3-zip php8.3-mysql
```

创建 laravel 项目

```bash
composer create-project laravel/laravel filament-test
```

切换到项目目录

```
cd filament-test
```

安装 filament

```
composer require filament/filament:"^3.2" -W
```

安装 panels

```
php artisan filament:install --panels
```



```
┌ What is the ID? ─────────────────────────────────────────────┐
│ admin                                                        │
└──────────────────────────────────────────────────────────────┘
```



```
 ┌ All done! Would you like to show some love by starring the Filament repo on GitHub? ┐
 │ ○ Yes / ● No                                                                        │
 └─────────────────────────────────────────────────────────────────────────────────────┘
```



##  配置

修改  **.env** 配置数据库

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=filament-test
DB_USERNAME=demo
DB_PASSWORD=12345678
```

迁移数据库

```
php artisan migrate
```



```
 ┌ Name ────────────────────────────────────────────────────────┐
 │ demo                                                         │
 └──────────────────────────────────────────────────────────────┘
```



```
 ┌ Email address ───────────────────────────────────────────────┐
 │ demo@outlook.com                                             │
 └──────────────────────────────────────────────────────────────┘

```



```
 ┌ Password ────────────────────────────────────────────────────┐
 │ ••••••••                                                     │
 └──────────────────────────────────────────────────────────────┘
```

启动项目

```bash
php artisan serve
```

后台访问地址

```
http://127.0.0.1:8000/admin/login
```

## User

以用户为例， 创建 用户面板

```bash
php artisan make:filament-resource User
```

修改 文件 **UserResource.php**

```
 INFO  Filament resource [app/Filament/Resources/UserResource.php] created successfully.
```

form 方法用来生成表单

```php
public static function form(Form $form): Form
{
    return $form
        ->schema([
            //
        ]);
}
```

table 方法用来生成列表

```php
public static function table(Table $table): Table
{
    return $table
        ->columns([
            //
        ])
        ->filters([
            //
        ])
        ->actions([
            Tables\Actions\EditAction::make(),
        ])
        ->bulkActions([
            Tables\Actions\BulkActionGroup::make([
                Tables\Actions\DeleteBulkAction::make(),
            ]),
        ]);
}
```





### 添加用户

```php
public static function form(Form $form): Form
{
    return $form
        ->schema([
            Forms\Components\TextInput::make('name'),
            Forms\Components\TextInput::make('email'),
            Forms\Components\TextInput::make('password'),
        ]);
}
```

访问添加用户页面

```
http://127.0.0.1:8000/admin/users/create
```

默认使用自动填充数据， 默认模型不允许自动填充， 需要设置允许填充的字段， 修改用户模型 User

```php
class User
{
	protected $fillable = [
        'name',
        'email',
        'password',
    ];
}
```



### 用户列表

```php
public static function table(Table $table): Table
{
    return $table
        ->columns([
            Tables\Columns\TextColumn::make('id'),
            Tables\Columns\TextColumn::make('name'),
            Tables\Columns\TextColumn::make('email'),
            Tables\Columns\TextColumn::make('email_verified_at'),
            Tables\Columns\TextColumn::make('created_at'),
            Tables\Columns\TextColumn::make('updated_at'),
        ])
        ->filters([
            //
        ])
        ->actions([
            Tables\Actions\EditAction::make(),
        ])
        ->bulkActions([
            Tables\Actions\BulkActionGroup::make([
                Tables\Actions\DeleteBulkAction::make(),
            ]),
        ]);
}
```

访问用户列表页面

```
http://127.0.0.1:8000/admin/users
```

