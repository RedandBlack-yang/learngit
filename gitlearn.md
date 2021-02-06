# Git使用

仓库分为工作区 暂存区 提交区

工作区:learngit文件夹就是工作区

版本库:工作区中有一个隐藏目录.git,是Git的版本库

暂存区(stage或index):使用git add 把文件放到暂存区

提交区:git commit一次性把暂存区的所有修改提交到分支

## git初始化和文件添加

```linux
mkdir learngit	# 创建名为learngit的目录
cd learngit		#跳转到learngit目录
git init		#将该目录初始化为git仓库
ls -ah			#查看learngit下的文件(包括隐藏文件)
git add readme.txt	#添加一个readme.txt的文件
git commit -m "注释1"	#记录操作注释
# 使用notepade++修改文件
git status		#查看工作区,输出结果告诉,readme文件被修改过,但还没准备提交
git diff readme.txt	#查看readme前后不同
git add readme.txt	#将文件加到提交区
git status 		#查看当前仓库的状态
git commit -m "注释2"	#提交代码并注释
git status		#仓库变干净了
```

**git add .**：他会监控工作区的状态树，使用它会把工作时的**所有变化提交**到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。

**git add -u** ：他仅监控**已经被add的文件**（即tracked file），他会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file）。（git add --update的缩写）

**git add -A** ：是上面两个功能的合集（git add --all的缩写）

### commit 使用命令修改注释：

```
git commit --amend		# 进入vim模式修改注释
```

## 版本回退

### git log查看历史记录

### git reflog 记录所有命令

### git reset 版本回退

在Git中，用`HEAD`表示当前版本，也就是最新的提交`1094adb...`（注意我的提交ID和你的肯定不一样），上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。

```
git reset --hard HEAD^	#恢复到上一个版本
git reset --hard 版本号	#根据版本号恢复,版本号使用几位即可
```

### git cheakout  --file 恢复到上次git add 或 git commit之后的状态

### git reset HEAD  file 把暂存区的修改回退到工作区

使用此命令之后通常可以使用git cheakout  --file 将刚刚回退到工作区的内容再清空

### 小结

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

## 删除文件

```
rm test.txt
git rm test.txt
git commit -m "remove test.txt"

rm text.txt  #之后如果发现误删,由于版本库中还有
git checkout --test.txt	#用版本库中的替换工作区的 
```



## 远程仓库

### 创建SSH Key

```
ssh-keygen -t rsa -C "github的邮件地址"	#创建SSH Key
cd ~/.ssh		#到用户主目录
ls				#查看是否存在id_rsa  id_rsa.pub
cat	id_rsa.pub 			#打开文件查看密钥
```

将密钥添加到GitHub

### 添加远程仓库

```
 git remote add origin 仓库的ssh地址		#GitHub的用户名最好仅由字母数字组成
 git push -u origin master		#
```

由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

从此,提交本地仓库,只需如下命令

```
git push origin master
```

注:如果出现Are you sure you want to continue connecting (yes/no)?  输入yes即可

### 从远程库克隆

#### 在github创建新的仓库

勾选Initialize this repository with a README

#### 使用git clone 克隆一个本地库

即GitHub仓库中的ssh下的命令

## 分支管理

### 创建合并分支

```
git checkout -b dev	#创建dev分支  -b表示创建并切换
git branch     		#查看分支,当前分支前有*
git checkout master	#切换回master,发现在branch中的修改没有改变
# git merge	dev		#将dev分支的工作合并到master
```

git checkout master 与 git switch master 等价

### 分支命令

查看分支：`git branch`

创建分支：`git branch <name>`

切换分支：`git checkout <name>`或者`git switch <name>`

创建+切换分支：`git checkout -b <name>`或者`git switch -c <name>`

合并某分支到当前分支：`git merge <name>`

删除分支：`git branch -d <name>`

### 合并分支冲突

当使用两个分支修改同一文件后同提交会出现冲突,需手动解决冲突



