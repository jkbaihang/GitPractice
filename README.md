# GitPractice
Git practice note

### 配置别名
```
$ git config --global alias.co checkout
```
具体设置文件位置
```
$ cd ~ | cat .gitconfig
[user]
	name = jkbaihang
	email = 909920027@qq.com
[alias]
	lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
	st = status
	co = checkout
	ci = commit
	br = branch
```


### 查看提交历史
```
$ git log
```
 - -p:用来显示每次提交的内容差异
 - -数字n:-2显示两次提交
 - -stat:简略的统计信息
 - --pretty=one:每个提交放在一行显示
 - --prrtty=format 参数:定制纪录格式
 - --decorate 查看分支所指对象
 - --graph 查看分支交叉情况

##### 提交区间
```
  A <- B <- E <- F -< **master**
         \
	  <- C <- D <- **experiment**
```

 - 双点:Git 选出在一个分支中而不在另一个分支中的提交。
```
$ git log master..experiment
D
C
```

 - 多点:查看哪些提交是被包含在 某些分支中的一个,但是不在你当前的分支上.￼Git 允许你在任意引用前加上 ^ 字符或者 --not 来指明你不希望 提交被包含其中的分支。因此下列3个命令是等价的:
```
$ git log refA..refB
$ git log ^refA refB
$ git log refB --not refA
```
想查看所有被 refA 或 refB 包含的但是不被 refC 包含的提交
```
$ git log refA refB ^refC
$ git log refA refB --not refC

```
 - 三点：想查看所有被 refA 或 refB 包含的但是不被 refC 包含的提交。
```
$ git log master...experiment
F
E
D
C
```

### 取消暂存的文件
`git reset HEAD <file>`

### 撤销对文件的修改
`git checkout -- <fie>`

### 远程仓库
 - 查看远程仓库
```
$ git remote #-v参数显示地址
```

 - 添加远程仓库
```
$ git remote add <shortname> <url>
```
可以使用字符串pb来代替整个URL

```
$ git remote add pb https://github.com/paulboone/ticgit
$ git fetch pb
```
 - 从远程仓库中抓取与拉取 
```
$ git fetch [remote-name]
```
 - 推送到远程仓库
```
$ git push [remote-name] [branch- name]
```
 - 查看远程仓库
```
$ remote show [remote-name]
```
 - 远程仓库移除和重命名
```
git remote rename [old-remoteName] [newname]
git remote rm [remoteName]
```

### 标签
 - 创建标签
```
$ git tag -a v1.0 -m 'version 1.4' #附注标签
$ git tag v1.1 #轻量标签
```

 - 查看
`git show v1.0`
附注便签显示标签信息和提交信息，轻量标签只显示提交信息

 - 共享标签
```
git push origin [tagname]。
```
将标签也传到远程仓库服务器
```
git push origin --tags
```
将所有不在远程仓库服务器上的标签上传

### 分支
 - master:maste并不是一个特殊的分支，只是系统默认创建。
 - HEAD指针:指向当前所在的本地分支，可以将HEAD想象为当前分支的别名。
 - 创建分支并切换`git checkou -b [branchName]`
 - 删除分支`git branch -d [branchName]`
 - 查看每个分支的最后一次提交 `git branch -v`
 - 查看哪些分支合并到当前分支 `git branch --merged`
 - 查看哪些分支未合并到当前分支 `git branch --no-merged`

### 远程分支
 - 远程跟踪分支:远程分支状态的引用，不能在本地移动。在做网络通信操作时，会自动根据远程库的状态而移动.远程仓库名字一般为origin。以`(remote)/(branch)`形式命名，比如`origin/master`。
 - 跟踪分支：从一个远程跟踪分支checout的一个本地分支(也叫上游分支)。跟 踪分支是与远程分支有直接关系的本地分支。
```
git checkout -b [branch] [remotename]/[branch]
git checkout --track [remotename]/[branch]

```
设置已有的本地分支跟踪一个刚刚拉取下来的远程分支,或者想要修改正在跟踪的上游分支
```   
$ git branch -u origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.
```
 - 查看已设置的跟踪分支
```
$ git branch -vv
```

### 变基
 - 变基:寻找两个分支的最近共同祖先，然后对比当前分支相对于该祖先的历史提交，提取相应的修改并存为临时文件，然后将当前分支指向目标基底，然后将之前另存为临时文件的修改依序应用。
 - 变基的特点:实际的开发工作是并行的，但是看起来提交历史是是串行的。
 - 变基的使用：只对尚未推送或分享给别人的本地修改执行变基操作清理历史,从不对已推送至别处的提交执行变基操作。
