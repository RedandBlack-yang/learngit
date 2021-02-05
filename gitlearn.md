# Git使用

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

