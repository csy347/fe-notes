
mac内置了PHP的apache环境以及php开发语言；唯独缺少mysql数据库。

检查Mac中的apache以及php版本信息

``` shell
apachectl -v
# 显示为：
Server version: Apache/2.4.34 (Unix)
Server built:   Aug 17 2018 18:35:43

php -v
# 显示为：
PHP 7.1.19 (cli) (built: Aug 17 2018 20:10:18) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies
```

apache下httpd.conf配置文件

httpd.conf文件所在的位置\etc\apache2目录下
``` shell 
# 你的apache软件安装的位置。其它指定的目录如果没有指定绝对路径，则目录是相对于该目录，mac原装的apache可以不用改；
ServerRoot "/usr"

# 监听端口
<IfDefine SERVER_APP_HAS_DEFAULT_PORTS>
    Listen 8080
</IfDefine>
<IfDefine !SERVER_APP_HAS_DEFAULT_PORTS>
    Listen 80
</IfDefine>

# 加载的相关模块
LoadModule authn_file_module libexec/apache2/mod_authn_file.so
#LoadModule authn_dbm_module libexec/apache2/mod_authn_dbm.so
#LoadModule authn_anon_module libexec/apache2/mod_authn_anon.so
#LoadModule authn_dbd_module libexec/apache2/mod_authn_dbd.so
#LoadModule authn_socache_module libexec/apache2/mod_authn_socache.so
LoadModule authn_core_module libexec/apache2/mod_authn_core.so
LoadModule authz_host_module libexec/apache2/mod_authz_host.so
#......
LoadModule hfs_apple_module libexec/apache2/mod_hfs_apple.so

# 加载的php版本
LoadModule php7_module libexec/apache2/libphp7.so

<IfModule unixd_module>
# 伪用户
    User _www
# 伪用户组
    Group _www
</IfModule>

#管理员的邮箱
ServerAdmin you@example.com

# 站点名称(域名)
ServerName www.example.com:80

# 这里是全局目录默认规则，拒绝所有
<Directory />
    AllowOverride none
    Require all denied
</Directory>

# 这个是源码包安装后，网站主目录位置这个是源码包安装后，网站主目录位置，mac默认站点文件，可以改成你需要的文件名称
# --- Options 目录权限
#  None ：没有任何额外权限
#   All ：所有权限
#   Indexs ：没有找到默认文章（如：index.php）就会返回当前文件夹下的所以文件列表

# --- MultiviewsMatch
#

# --- AllowOverride子权限文件开关
# 定义是否允许目录下.htaccess文件中的权限生效，这里只列举以下两种常见的选项
#   None：.htaccess中权限不生效
#   All： .htaccess文件中所有权限都生效

# --- Require访问控制管理
# Require all granted允许所有访问
# Require all denied拒绝所有访问
# Require ip 192.168.1.0/24 仅允许192.168.1.0/24网络的主机访问
# Require not ip 192.168.1.2 禁止192.168.1.2的主机访问，其它都可以
DocumentRoot "/Library/WebServer/Documents"
<Directory "/Library/WebServer/Documents">
    Options FollowSymLinks Multiviews
    MultiviewsMatch Any
    AllowOverride None
    Require all granted
</Directory>

# 设置默认目录的默认文档
<IfModule dir_module>
    DirectoryIndex index.html index.php
</IfModule>

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
# 防止 .htaccess 和 .htpasswd 文件被从Web上访问
<FilesMatch "^\.([Hh][Tt]|[Dd][Ss]_[Ss])">
    Require all denied
</FilesMatch>

# Apple specific filesystem protection.
# 苹果特定文件系统保护，全是拒绝访问，所以可以不用管
<Files "rsrc">
    Require all denied
</Files>
<DirectoryMatch ".*\.\.namedfork">
    Require all denied
</DirectoryMatch>

# apache错误日志记录 记录文件的路径，可以修改
ErrorLog "/private/var/log/apache2/error_log"

# 记录日志的等级，
LogLevel warn

<IfModule log_config_module>
    # 日志格式
    # The following directives define some format nicknames for use with
    # a CustomLog directive (see below).
    #
    LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
    LogFormat "%h %l %u %t \"%r\" %>s %b" common

    <IfModule logio_module>
      # You need to enable mod_logio.c to use %I and %O
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
    </IfModule>

    # 访问 apache 访问日志
    CustomLog "/private/var/log/apache2/access_log" common

    #
    # If you prefer a logfile with access, agent, and referer information
    # (Combined Logfile Format) you can use the following directive.
    #
    #CustomLog "/private/var/log/apache2/access_log" combined
</IfModule>

# 读取其他的配置
Include /private/etc/apache2/other/*.conf
```

配置完成后重启apache服务，打开浏览器输入localhost
``` shell
sudo httpd -v # 检查配置文件是否正确
sudo apachectl start # 启动 apache 服务
sudo apachectl stop # 关闭 appache 服务
sudo apachectl restart # 重启 apache 服务
```

安装数据库
``` shell
brew install mysql
```

安装完成后，执行下面语句：
``` bash
brew info mysql #下面一大段信息都是所安装的数据库的信息，以及如何开启数据库服务
mysql: stable 8.0.13 (bottled) # 数据库版本
Open source relational database management system
https://dev.mysql.com/doc/refman/8.0/en/
Conflicts with:
  mariadb (because mysql, mariadb, and percona install the same binaries.)
  mariadb-connector-c (because both install plugins)
  mysql-cluster (because mysql, mariadb, and percona install the same binaries.)
  mysql-connector-c (because both install MySQL client libraries)
  percona-server (because mysql, mariadb, and percona install the same binaries.)
/usr/local/Cellar/mysql/8.0.13 (267 files, 236.6MB) * # 安装的地址
  Poured from bottle on 2019-02-05 at 21:20:59
From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/mysql.rb
==> Dependencies
Build: cmake ✘
Required: openssl ✔
==> Requirements
Required: macOS >= 10.10 ✔
==> Caveats
We've installed your MySQL database without a root password. To secure it run:
    mysql_secure_installation #这个是执行数据库初始配置的语句

MySQL is configured to only allow connections from localhost by default

To connect run:
    mysql -uroot

To have launchd start mysql now and restart at login:
# 如果你要数据库在开机的时候就启动呢，就执行下面的语句；
  brew services start mysql
Or, if you don't want/need a background service you can just run:
# 如果你不要开机的时候启动数据库服务，就执行下面的语句即可；按需启动数据库服务
  mysql.server start
==> Analytics
install: 69,087 (30 days), 186,292 (90 days), 867,912 (365 days)
install_on_request: 63,446 (30 days), 173,599 (90 days), 781,056 (365 days)
build_error: 0 (30 days)
```

``` shell
mysql --help
# 你可以看到一大段数据库帮助信息，这个时候你锁定一句
Default options are read from the following files in the given order:
/etc/my.cnf /etc/mysql/my.cnf /usr/local/etc/my.cnf ~/.my.cnf
#这句话，就是告诉你，数据库配置的加载顺序，所以你需要新建my.cnf文件，写入你的配置即可；当然，完成后，记得重启数据库服务；

```

查看版本信息
``` shell
mysql --version
mysql  Ver 8.0.13 for osx10.14 on x86_64 (Homebrew)
```

利用安装MySQL时，给出的用户和密码登录服务，在终端输入如下命令
``` shell
mysql -u root -pe
```

退出命令
``` shell
exit
```
