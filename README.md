# 太初有道-原创圣经短歌

## 介绍

专注于原创圣经短歌、原创圣经故事的网站，并向微信小程序、APP等提供接口。

本程序基于[Laminas](https://getlaminas.org/)的MVC Skeleton，

## 运行
```bash
$ cd path/to/install
$ php -S 0.0.0.0:8080 -t public
# OR use the composer alias:
$ composer run --timeout 0 serve
```

此命令将启动cli-server，端口为8080，测试网址为http://localhost:8080/

**注意:** 此运行方式*仅限于开发模式*。

## 开发模式

请参考[laminas-development-mode](https://github.com/laminas/laminas-development-mode)

```bash
$ composer development-enable  # enable development mode
$ composer development-disable # disable development mode
$ composer development-status  # whether or not development mode is enabled
```

亦可通过配置文件来切换开发模式
`config/development.config.php.dist`，或`config/autoload/development.local.php.dist`. 使用时，需将“.dist”从文件名中删除。

## 单元测试
单元测试基于[laminas-test](https://docs.laminas.dev/laminas-test/):

  ```bash
  $ composer require --dev laminas/laminas-test
  ```

单元测试依赖安装之后，可以通过下方的命令执行测试:

```bash
$ ./vendor/bin/phpunit
```

亦可通过配置文件`phpunit.xml.dist`来使用单元测试，使用时需将“.dist”去掉。

## 使用Vagrant

可使用Laminas自带的`Vagrantfile`.

```bash
$ vagrant up
```

### 安装依赖
```bash
$ vagrant ssh -c 'composer install'
```

### 更新依赖

```bash
$ vagrant ssh -c 'composer update'
```

启动之后，Vagrant将会在8080端口启动服务器，地址为http://localhost:8080/

## 服务器配置

### Apache配置

配置Virtual Host:

```apache
<VirtualHost *:80>
    ServerName laminasapp.localhost
    DocumentRoot /path/to/laminasapp/public
    <Directory /path/to/laminasapp/public>
        DirectoryIndex index.php
        AllowOverride All
        Order allow,deny
        Allow from all
        <IfModule mod_authz_core.c>
        Require all granted
        </IfModule>
    </Directory>
</VirtualHost>
```

## QA工具

- [phpcs](https://github.com/squizlabs/php_codesniffer)
- [phpunit](https://phpunit.de)

可通过下方命令安装:

```bash
$ composer require --dev phpunit/phpunit squizlabs/php_codesniffer laminas/laminas-test
```

配置Composer:

```bash
# Run CS checks:
$ composer cs-check
# Fix CS errors:
$ composer cs-fix
# Run PHPUnit tests:
$ composer test
```
