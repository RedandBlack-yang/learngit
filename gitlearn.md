# Git使用

## git初始化和文件添加

仓库分为工作区 暂存区 提交区，文件夹即是工作区.

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



