# 使用Github

## 1. 目的

借助GitHub托管项目代码

****



## 2.基本概念

1. Repository：仓库

   仓库用来存放项目代码，每个项目对于一个仓库，多个开源项目对应多个仓库

2. Star：收藏

   收藏项目，方便下次查看

3. Fork：复制克隆项目

   该fork的项目是独立存在的

4. Pull Request：发起请求

   请求原作者更新文件，如果原作者同意，就合并新文件和原文件。

5. Watch：社交网站关注

   关注了一个项目，只要这个项目有任何更新，就会收到通知。

6. Issue：问题

   发现代码Bug，可以发一条消息，一起讨论

7. Github主页

   左侧是关注用户的动态以及关注仓库的动态，右侧是所有的仓库

8. 仓库主页

   项目代码，版本，收藏关注信息

9. 个人主页

   个人简介，关注的人等	

****



## 3. 使用git创建仓库

```linux
git config --global user.name '用户名'
git config --global user.email '邮箱'
```



### 初始化一个新的git仓库

1. 创建文件夹

2. `mkdir test`在文件内初始化git(创建git仓库)，名字叫test

   通过

   ```linux
   cd test
   git init
   ```

   生成一个隐藏的.git文件，用来存放所有仓库信息的



### 添加文件

1. 生成一个新文件

   ```linux
   touch a1.php
   ```

   生成a1.php文件

   ```linux
   git status
   ```

   查看文件状态



2. 提交文件到暂存区

   ```linux
   git add a1.php
   ```

   查看文件状态

   ```linux
   git status
   ```



3. 提交文件到仓库

   ```linux
   git commit -m 'add a1.php'
   ```

   引号里面的内容是描述

   ```linux
   git status
   ```



### 修改文件

1. 修改文件

   ```linux
   vi a1.php
   ```

   使用vi命令修改文件

   ```linux
   wq
   ```

   保存

   ```linux
   cat a1.php
   ```

   查看文件

   ```linux
   git status
   ```

   查看文件状态，发现是红色的modified，修改过的。需要添加



2. 添加文件到暂存区

   ```linux
   git add a1.php
   git status
   ```

   变成绿色的，代表已经到暂存区了



3. 添加文件到仓库

   ```linux
   git commit -m '第一次通过git修改文件并提交到仓库'
   git status
   ```

   提交成功



### 删除文件

1. 通过rm命令删除文件

   ```linux
   rm -rf a1.php
   ```



2. 从git中删除文件

   ```linux
   git rm a1.php
   ```



3. 提交操作

   ```linux
   git commit -m '第一次通过git删除仓库文件'
   git status
   ```

****



## 4. Git管理远程仓库

 作用：备份，实现代码的共享

同步本地仓库同步到git远程仓库中，push操作`git push`

需要先将远程仓库（github对应的项目）复制到本地

```linux
git clone 仓库地址
```

仓库地址：复制github网页上的clone部分的链接

打开一个文件夹。

确认已经init过

```linux
git config --list
```

如果有email和用户名信息就说明已经初始化过了

克隆仓库

```linux
git clone 链接
```

等待下载完成，完成后，可以进行修改操作test文件夹里的文件

```linux
cd test
vi a1.php
wq
```

将工作区的文件添加到暂存区

```linux
git add a1.php
```

将暂存区文件添加到仓库

```linux
git commit -m '第二次通过git添加到仓库'
git status
```

同步到远程仓库

```linux
git push
```

等待上传

可能报错：没有权限

```linux
vi .git/config
#将
[remote "origin"]
	url = https://github.com/用户名/仓库名.git
#修改为：
[remote "origin"]
	url = https://用户名:密码@github.com/用户名/仓库名.git
```

****



## 5. 搭建个人网站

**个人网站**的访问：

`https://用户名.github.io`

搭建个人主页步骤：

1. 创建个人站点：新建仓库（仓库名必须是：<font color = Red>用户名.github.io </font> ）
2. 在仓库下新建index.html的文件即可（网站首页）
3. 注意：github pages仅支持静态网页，仓库里面只能是.html文件



**项目站点**的访问：

`https://用户名.github.io/仓库名`

搭建步骤：

1. 进入项目主页，点击setting
2. 在setting界面，点launch automatic generator，来自动生成主题页面（在source的none那里改成master branch）
3. 修改页面

