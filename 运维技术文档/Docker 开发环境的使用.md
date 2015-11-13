# Docker 开发环境使用文档



>####  一. 容器分配

| 使用人  | 用户名  | 主机  | 域名  |
| ------------ | ------------ | ------------ | ------------ |
| 大明  | hudm  | 172.17.33.12  |  *.hudm.5usport.cn |
| 建华  | zhangjh  | 172.17.33.13  | *.zhangjh.5usport.cn  |
| 正用  | liuzy  | 172.17.33.14  | *.liuzy.5usport.cn  |
| 许锐  | xurui  | 172.17.33.15  | *.xurui.5usport.cn  |
| 罗竞  | luoj   | 172.17.33.16  | *.luoj.5usport.cn  |
| 陈花  | chenh   | 172.17.33.17  |  *.chenh.5usport.cn  |
| 鹏扬  | young  | 172.17.33.18  | *.young.5usport.cn  |
| 希浩  | chenxihao    | 172.17.33.19  | *.chenxihao.5usport.cn  |
| 测试  | demo  | 172.17.33.20  | *.demo.5usport.cn  |
| 全积  |  xiaoquanji  | 172.17.33.21  | *.xiaoquanji.5usport.cn  |
| 志挺  |  caizhiting  | 172.17.33.22  | *.caizhiting.5usport.cn  |

> #### 二、代码发布基本流程

1、基本的流程规范

```
个人电脑git代码测试===> 复制到容器环境测试===> 提交到gitlab内网develop分支测试 ===>合并到正式服务
```

2、因为每个人的容器环境都是统一的，所以就不会再存在服务环境不一致导致代码不能运行的问题。

3、整个过程就多了容器这一步，如果你觉得麻烦，依然可以按照原来的方式：

```
个人电脑git代码测试===> 提交到gitlab内网develop分支测试 ===>合并到正式服务
```

   或者：

```
个人容器git代码和测试===> 提交到gitlab内网develop分支测试 ===>合并到正式服务
```


> #### 三、使用说明

**1. 代码上传：**

```
开始菜单，运行（win+R）===>输入：\\172.17.33.8 ===>打开共享，输入用户名和密码===>
把代码复制到相应的项目目录即可。
```

提示：用户和密码，与gitlab帐户或公司文件共享服务器一致。


**2. 网站测试浏览**

浏览器输入： 
```
http://子域名前缀.用户名.5usport.cn

如:
http://www.demo.5usport.cn , http://static2.demo.5usport.cn`
```
**3. 容器SSH登陆**

 IP为上面表格中为各自分配的主机IP，端口默认22 。用户名 root , 密码：    5udockerTest(登陆后请及时修改)。可以使用的工具：
 - secureCRT
 - putty
 - xshell

**4. 容器数据目录**

  容器是一个随时创建和销毁一个东西（由于升级或更新），所以这里规定个人修改的重要数据  要保存在 /data 目录下。
  
/daa/mysql 数据库目录

/daa/www 网站项目目录(通过共享上传的代码文件就是放在这里)


**5. 容器的服务**

  安装了 Tengine/1.5.2 (nginx/1.2.9) + mysql5.6 + PHP 5.5.21  的web服务.

 主要目录和文件：
```
nginx： /usr/local/webserver/tengine/conf

mysql：/etc/my.cnf、/var/lib/mysql、 /data/mysql/data

php: /usr/local/webserver/php5
```

服务启动、停止、重启

```
nginx :   /etc/init.d/nginx   start|stop|restart ， 如重启nginx，/etc/init.d/nginx restart

mysql:   /etc/init.d/mysql    start|stop|restart 
php:   /etc/init.d/php-fpm  start|stop|restart 
```

**6.关于数据库**

个人容器数据库访问方式：
```
http://db.用户名.5usport.cn
```

自己的数据库可以随意更改，但如果想使用最新，可以修改代码连接到测试服务器(192.168.2.12，这里定期会同步一次正式服的数据), 或联系我下载导入一份。

**7.关于需求**

如果有其他配置的需求，如为php添加扩展、rewrite规则、添加虚拟主机，可以联系我批量更新内容。
目前容器只添加了3个虚拟主机：
```
- http://www.用户名.5usport.cn
- http://static2.用户名.5usport.cn
- http://db.用户名.5usport.cn
```

**8.关于域名**


域名使用的是泛域名的形式，比如，你的域名是： 
```
*.demo.5usport.cn ，IP指向 172.17.33.20,
```
那么，www.demo.5usport.cn、 abc.demo.5usport.cn、...等，只要前缀是任意合法的字符，都会指向 172.17.33.20


