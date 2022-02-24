# 1.创建GitHub仓库

# 2.安装Git

## 2.1 window下安装git bash

## 2.2 账号配置

本地库配置账号和邮箱

```bash
git config --global user.email <qq986793091@gmail.com>
git config --global user.name <Diandian>
```

配置账号和邮箱后，才能通过 git commit 命令提交到仓库。

# 3.上传项目

当以后需要更新项目的时候有四步需要走
第一步：执行`git pull`命令将GitHub上的代码当下来合并代码，防止提交新代码的时候起冲突
第二步：执行`git add`命令将代码添加到仓库
第三步：执行`git commit`命令将代码提交到仓库
第四步：执行`git push`命令将代码提交到GitHub

## 3.1 创建项目

第一步：进入项目目录

```bash
cd D:
cd project
```

第二步 初始化项目仓库

```bash
git init
```

完成之后，项目目录下会多一个.git文件目录，用于Git管理版本库。

第三步：项目仓库添加内容

```bash
git add .
```

. 表示添加当前目录下所有文件，也可以单独添加文件，. 改为文件名即可。

第四步：将文件提交到仓库

```bash
git commit -m "this is a test."
```

-m 输入项目说明

## 3.2 将本地仓库上传到GitHub

```bash
# 本地仓库关联GitHub地址
git remote add origin https://github.com/Diandian-ops/handbook/
# 上传
git push -u origin master
```

如果没有异常，会等待几秒，然后跳出一个让你输入Username和Password 的窗口，你只要输人github的登录账号和密码就行了，好了上你的GitHub上看看项目有没有传上去吧。

# 4.常见问题

## 4.1 timeout（windows下）

修改hosts文件，重新获取最新的IP地址进行修改。

第一步：windows端 C:\Windows\System32\drivers\etc\hosts

第二步：访问 http://github.global.ssl.fastly.net.ipaddress.com/#ipinfo 记录IP地址

```bash
199.232.69.* github.global.ssl.fastly.net
```

第三步：访问 http://github.com.ipaddress.com/#ipinfo 记录IP地址

```bash
140.82.114.* github.com
```

第四步：终端输入 

```bash
ipconfig /flushdns
```



## 4.2 远程库和本地库不一致

问题描述：

 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/Diandian-ops/handbook'

问题原因：

远程库与本地库不一致造成的，在hint中也有提示把远程库同步到本地库就可以了。

解决办法：

该命令的意思是把远程库中的**\*更新合并\***到（**pull=fetch+merge**）本地库中，**–-rebase**的作用是取消掉本地库中刚刚的commit，并把他们**接到**更新后的版本库之中。

```bash
git pull --rebase origin master
```

