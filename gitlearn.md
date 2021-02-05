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



