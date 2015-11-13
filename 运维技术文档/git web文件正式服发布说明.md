# git web文件正式服发布说明 #


> **一、 使用git 发布web文件的基本流程**

![](https://gitlab.usport.cc/technology/document/raw/2ef55844d7f2185f6c668002e4a64b08aad85d61/images/web%E5%8F%91%E5%B8%83.png)

> **二、 网站发布流程（操作相关）**

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E7%BD%91%E7%AB%99%E5%8F%91%E5%B8%83%E6%B5%81%E7%A8%8B%EF%BC%88%E6%93%8D%E4%BD%9C%E7%9B%B8%E5%85%B3%EF%BC%89.png)

> **三、使用git 发布web文件的操作过程****

![](https://gitlab.usport.cc/technology/document/raw/master/images/git%20web%E6%96%87%E4%BB%B6%E5%90%8C%E6%AD%A5%E6%93%8D%E4%BD%9C%E6%B5%81%E7%A8%8B.png)


> **四、具体操作说明****


**1. gitlab 合并请求**

1）进入需要合并的库

![](https://gitlab.usport.cc/technology/document/raw/master/images/1.%E8%BF%9B%E5%85%A5%E5%BA%93.png)

2）提交合并请求

![](https://gitlab.usport.cc/technology/document/raw/master/images/2.%E5%90%88%E5%B9%B6%E8%AF%B7%E6%B1%82.png)

![](https://gitlab.usport.cc/technology/document/raw/master/images/2.%E5%90%88%E5%B9%B6%E8%AF%B7%E6%B1%822.png)

![](https://gitlab.usport.cc/technology/document/raw/master/images/2.%E5%90%88%E5%B9%B6%E8%AF%B7%E6%B1%823.png)

3）接受请求（项目管理员操作）

![](https://gitlab.usport.cc/technology/document/raw/master/images/3.%E6%8E%A5%E5%8F%97%E8%AF%B7%E6%B1%82.png)


**2. sourceTree 推送操作**

1). 建立master分支

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E5%88%9B%E5%BB%BA%E5%88%86%E6%94%AF20150128162548.png)

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E5%88%9B%E5%BB%BA%E5%88%86%E6%94%AF20150128162630.png)

2). 进入develop分支，拉取数据。


3). 切换到master分支，拉取数据。


4). 合并develop 分支到master  

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E5%90%88%E5%B9%B6%E5%88%86%E6%94%AF20150128163339.png)

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E5%90%88%E5%B9%B6%E5%88%86%E6%94%AF20150128163415.png)

5). 处理合并的冲突

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E5%87%BA%E7%8E%B0%E5%86%B2%E7%AA%8120150128163523.png)

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E8%A7%A3%E5%86%B3%E5%86%B2%E7%AA%8120150128163632.png)

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E8%A7%A3%E5%86%B3%E5%86%B2%E7%AA%8120150128163705.png)


![](https://gitlab.usport.cc/technology/document/raw/master/images/%E6%8F%90%E4%BA%A4%E5%86%B2%E7%AA%8120150128163931.png)

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E6%8F%90%E4%BA%A4%E5%86%B2%E7%AA%8120150128164037.png)


6). 推送合并后的master分支到远程

![](https://gitlab.usport.cc/technology/document/raw/master/images/%E6%8E%A8%E9%80%8120150128164145.png)



**3. GIT rsync 服务器操作**


ssh 192.168.11.28 服务器

- 自动操作

以newtest为例

    1）gitsync newtest
    
    2) cd /data/www/newtest   
    
    3) git log  ##查看是否最新，
    
    4) git status  ##查看库目录是否干净 

 
- 手工操作


    

以newtest为例


    1）cd /data/www/newtest

    2）git checkout master 

    3）git fetch origin && git reset --hard origin/master

    4）git checkout production

    5）git merge master


- 冲突问题的处理

![](https://gitlab.usport.cc/technology/document/raw/master/images/git%20server%E5%86%B2%E7%AA%81%E5%A4%84%E7%90%8620150128172247.png)

![](https://gitlab.usport.cc/technology/document/raw/master/images/git%20server%E5%86%B2%E7%AA%8120150128172428.png)


![](https://gitlab.usport.cc/technology/document/raw/master/images/git%20server%20%E5%86%B2%E7%AA%8120150128172501.png)


![](https://gitlab.usport.cc/technology/document/raw/master/images/%E8%A7%A3%E5%86%B3%E5%86%B2%E7%AA%8120150128172706.png)

