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
