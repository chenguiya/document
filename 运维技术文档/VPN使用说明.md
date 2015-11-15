## VPN 客户端使用说明

------------



#### VPN主要用途

1. 远程连到公司内网进行开发。
2. 故障处理与维护。

#### vpn 客户端安装

到共享服务器下载工具，并安装：

    \\192.168.2.110\公共文件夹\tools\网络工具\SSLVPNClient-v2.0.10.exe

#### 配置连接到VPN服务器

#### 一、连接到服务器需要两个认证：
-  密钥证书，由服务端颁布不同的客户端证书。由运维人员提供。请勿丢失或泄露。
-  用户的密码，即LDAP用户密码，与gitlab、共享服务等通用。

#### 二、步骤：

1、 启动客户端程序，双击任务栏的图示，新建连接：

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106105656.jpg)

2、下一步，输入配置名称：

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106105929.jpg)

3、 输入添加远程服务器的地址和端口，如：

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106110147.jpg)


![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106110634.jpg)


4、配置选项：

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106110712.jpg)



![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106110744.jpg)




5、 编辑配置文件，

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106110843.jpg)


6、 记下路径，添加一行：tls-auth "ta.key" 1

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106120414.jpg)



7、 将复制文件到："C:\Users\用户名\AppData\Roaming\Securepoint SSL VPN\config\5u_VPN"

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106124207.jpg)

8、点击连接：

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106140846.jpg)


9、用户名和密码：

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106140913.jpg)


![](https://github.com/chenguiya/document/blob/master/images/vpn_20151106140933.jpg)

10、点击连接

![](https://github.com/chenguiya/document/blob/master/images/vpn_20151107121209.png)

11、测试

ping  192.168.2.254
