# 介绍

Git是一个分布式版本控制软件

[GitHub](https://github.com/)是通过Git进行版本控制的软件源代码托管服务，是全球最大的[同性交友](https://github.com/)平台。

# 目的
### 为什么要学习Git和GitHub呢？
##### 工作需要
工作中需要我们需要对项目代码进行管理，目前用的最多的就是Git，这是开发人员的必备技能。
##### 学习需要
优秀的第三方库基本都托管于GitHub上，要想安装这些库就必须使用Git和GitHub,我们可以学习上面大神们的优秀代码和编程技巧思想。
##### [个人名片](https://github.com/laibinzhi)
将你自己工作中的一些项目和代码放到GitHub上面进行管理。这无疑是对个人能力最好的展示。

# Git基础命令
### Git配置
```bash
//查看git的版本信息
$ git --version 
//获取当前登录的用户
$ git config --global user.name 
//获取当前登录用户的邮箱
$ git config --global user.email "email@example.com"
//获取当前配置的所有信息
$ git config --list
```
### 登录Git
```bash
//设置git账户，userName为你的git账号
$ git config --global user.name 'laibinzhi' 
$ git config --global user.email 'laibinzhi@gmail.com'
```

### 创建一个文件夹
```bash
//创建文件夹Android
$ mkdir Android 
//切换到Android目录下
$ cd Android
```

### 创建一个文件
```bash
//方法一，单纯创建文件
$ touch hello.txt 
//方法二，创建文件并写入内容，单个>箭头表示写入， >>表示追加
$ echo > laibinzhi.html
$ echo >> android.md
echo "这是写入，会覆盖" > laibinzhi.html 
echo "这是追加" >> laibinzhi.html 
```

### 初始化Git仓库
```bash
//在Android文件夹下初始化一个仓库，此时文件里会到一个.git的隐藏文件夹
$ git init
```

### 创建忽略文件
```bash
//需要服务器端提交的内容可以写到忽略文件里
$ touch .gitignore
 /*
        .git
        .idea
 */
```


### 查看目录
```bash
//查看所有目录（包括.开头的文件）
$ ls -al
//查看所有目录（不包括.开头的文件）
$ ls 
```

### 查看文件内容
```bash
$ cat laibinzhi.html
```

### 增加到暂存区中
```bash
//添加单个文件到暂存区
$ git add laibinzhi.html
//添加所有文件到暂存区
$ git add --all
$ git add -A
```

### 添加到版本库中
```bash
$ git commit -m '备注信息'
```

### 查看版本
```bash
$ git log --oneline
```

### 比较差异
- 暂存区和工作区的差异
```bash
$ git diff 
```
- 暂存区和历史区的差异
```bash
$ ggit diff --cached
```
- 历史区和工作区的差异（修改）
```bash
$ git diff master
```

### 撤销内容
- 用暂存区中的内容或者版本库中的内容覆盖掉工作区
```bash
$ git checkout laibinzhi.html
```
- 取消增加到暂存区的内容（添加时）
```bash
$ git reset HEAD laibinzhi.html
```

### 删除本地文件
```bash
$ rm fileName
```

### 删除暂存区
```bash
//保证当前工作区中没有laibinzhi.html,使用--cached 表示只删除缓存区中的内容
$ git rm laibinzhi.html --cached
```

### 回滚版本
```bash
//回滚最近的一个版本 git log
$ git reset --hard HEAD/commit_id
```


### 分支管理
- 创建分支
```bash
$ git branch dev
```

- 切换分支
```bash
$ git checkout dev
```

- 创建分支并切换分支
```bash
$ git checkout -b dev
```

- 删除分支
```bash
$ git branch -d dev
```


- 在分支上提交新的版本
```bash
$ git commit -a -m 'dev1'
```

- 合并分支
```bash
$ git merge dev
```

- 分支的合并后显示log
```bash
$ git log --oneline --graph --decorate
```

### 工作现场
- 保留工作现场
```bash
$ git stash
```
- 查看工作现场
```bash
$ git stash list
```

- 恢复工作现场
```bash
$ git stash pop
```

### 添加远程的仓库
- 查看远程库信息
```bash
$ git reote -v
```
- 在本地创建和远程分支对应的分支
```bash
//本地和远程分支的名称最好一致；
$ git checkout -b branch-name origin/branch-name
```
- 建立本地分支和远程分支的关联
```bash
$ git branch --set-upstream branch-name origin/branch-name
```

- 从本地推送分支
```bash
//如果推送失败，先用git pull抓取远程的新提交
$ git push origin branch-name
```

- 从远程抓取分支
```bash
//如果有冲突，要先处理冲突。
$ git pull
```


### 标签
tag就是一个让人容易记住的有意义的名字，它跟某个commit绑在一起。
#### 新建一个标签
```bash
$ git tag <tagname>
```
命令`git tag <tagname>`用于新建一个标签，默认为HEAD，也可以指定一个commit id。
#### 指定标签信息
```bash
$ git tag -a <tagname> -m <description> <branchname> or commit_id
```
`git tag -a <tagname> -m "blablabla..."`可以指定标签信息。
#### PGP签名标签
```bash
$ git tag -s <tagname> -m <description> <branchname> or commit_id
```
`git tag -s <tagname> -m "blablabla..."`可以用PGP签名标签。
#### 查看所有标签
```bash
$ git tag
```
#### 推送一个本地标签
```bash
$ git push origin <tagname>
```
#### 推送全部未推送过的本地标签
```bash
$ git push origin --tags
```
#### 删除一个本地标签
```bash
$ git tag -d <tagname>
```
#### 删除一个远程标签
```bash
$ git push origin :refs/tags/<tagname>
```

# Git常见问题
### 大小写问题
如果`git`版本中把一个`A.txt`文件改为`a.txt`，`git`是不会记录这次更改的，因为`git`不区分同名文件的大小写，很郁闷，只有强制重命名该文件:

```git
git mv --force A.txt a.txt
```
### gitignore文件无法忽略某些文件
想要`.gitignore`起作用，这些文件不能在暂存区中，`.gitignore`文件只是忽略没有被暂存的文件，对于已经处于暂存区的文件，加入`gitignore`文件时一定要先从暂存区移除，才可以忽略。 

### commit时message备注信息写错了如何修改
```bash
$ git commit -m "错误的提交信息"
$ git commit --amend -m "正确的提交信息"
```

### 每次push提交是要输入密码，如何解决？
关联远程库的时候，用的是https协议，需要换成ssh,如下git@github.com:XXXXXX就是你的仓库地址 
第一次提交会出现验证的警告，输入yes回车就行
```bash
$ git remote rm origin
$ git remote add origin git@github.com:XXXXXX
$ git push -u origin master
```

# Git工作情形
## dev分支开发还没完成，突然要修改一个紧急bug
1. 保存工作现场
 ```bash
$ git stash
```
2. 切换到主分支master，并创建并切换到修改bug的分支fix_bug_001
 ```bash
$ git checkout master
$ git checkout -b "fix_bug_001"
```
3. 在fix_bug_001分支上修改bug并提交
 ```bash
$ git add fix_bug.java
$ git commit -m "finish fix_bug_001"
```

3. 修复完bug后，切回到master分支，并完成合并，最后删除fix_bug_001分支
 ```bash
$ git checkout master
$ git merge fix_bug_001
$ git branch -d fix_bug_001
```
4.接着回到dev分支继续干活并查看保存的工作现场
 ```bash
$ git checkout dev
$ git stash list
```
5.恢复工作现场

 ```bash
 //方法一，先恢复再删除stash内容
$ git stash apply
$ git stash drop
 //方法二，恢复的同时也删除stash
$ git stash pop
```
6.可以多次stash内容，先查看stash列表，再恢复指定的stash
 ```bash
$ git stash list
$ git stash apply stash@{0}
```

# Git终极大福利
![Git常见命令行](http://lbz-blog.test.upcdn.net/post/git_total.png)

