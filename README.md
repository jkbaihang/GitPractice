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
