# Git笔记

## git仓库

### 初始空仓库

- git init

## 文件

### 暂存区

- 添加

	- git add 

		- <文件>

			- 可以通配符

		- .

			- 工作区的所有

- 覆盖工作区

	- git checkout --<文件>

- 移出

	- git reset HEAD <文件>

- 工作&暂存

	- 删

		- git rm <文件>

			- 需未修改

	- 重命名

		- git mv <原名> <重命名>

### 储存

- 查

	- git stash list

- 加

	- git stash

- 恢复

	- git stash apply

- 删

	- git stash drop

- 恢复并删

	- git stash pop

### 提交

- git commit

	-  -m "<说明>"
	- 修改提交

		- --amend -m "<说明>"

	- -a

		- modified
		- 无需再add

## 跟踪

### 只有文本

- 非二进制
- 建议UTF-8
- 不用文本文件

### git status

- 简明-s

	- 首列

		- 未跟踪

			- ??

		- 暂存区

			- A
			- MM

				- 修改

		- 修改

			- M

### git diff

- 工作vs暂存

	- 比较所有
	- 单文件

		- <文件>

- 暂存vs最后版本

	- --staged

		- 未改动

## 历史

### git log

- 之前历史
- -<数字>
- 前几次提交

	- -<数字>

- --pretty=oneline

	- 单行

- --graph
- --abbrev-commit
- 遇

	- :

		- 翻页

			- ctrl+d

		- 退出

			- q

### git reflog

- 命令历史

### git reset --hard 

- 返回
- HEAD[<n个^>]

	- ^个数即前几个版本

- <版本号>

## 分支

### 主分支master

### 查

- git branch

	- 描述

		- -v

			- 最新提交

		- -vv所有分支

			- 先更新

				- git fetch --all

			- 显示

				- ahead

					- 未推送数

				- behind

					- 未更新数

	- 是否被合并

		- --merged [<分支名>]
		- --no-merged [<分支名>]

- 冲突

	- git status？

### 建

- git branch <分支名>

### 切

- git switch <分支名>

### 建并切

- git switch [-c] <分支名>

	- -c新建

### 合并

- git merge

	- [模式] [-m ""] 被合并分支名

		- 模式

			- fast forward

				- 默认

					- 父分支

						- 无新提交？
						- head?

							- 指向

								- 子分支提交

				-  log --graph时

					- 忽略分支

			- --no-ff

				- 禁用Fast forward
				-  log

					- merge commit
					- 提交于

						- 和分支

					- --graph时

						- 有分支

				- 必-m

	- --abort

		- 退出

- git rebase

	- 整理成

		- 一个分支的

	- 历史

		-  log --graph时

			- 忽略分支

		- 按分支排序

	- --onto <分支1>，..<分支N>

		- 切换到分支N
		- 1和N合并

			- 没有其他的

- git cherry-pick commit

	- commit

		- commit
		- <较早commit+1>..<较晚commit>
		- ..<commit>

			- 此commit
			- 和之前commit

### 删

- git branch -d <分支名>
- 强删

	- git branch -D 分支名

### 分工

- master

	- 不干活
	- 合并其他分支

		- 稳定

- dev

	- 干活

- feature-名

	- 新功能

- bug-名

	- 修复bug

## 远程

### shh-keygen

- 保证

	- 两端

		- 本地
		- 服务端

	- 相同

		- 用户名
		- email

- 执行

	- ssh-keygen -t rsa -C "<邮箱>"

		- [-o]

			- 防暴力破解

	- 位置

		- 默认

			- 主目录/.ssh目录
			- 有提示

		- 可自定义

- 文件

	- id_rsa
	- id_rsa.pub

- 测试

	- ssh -T git@github.com

### 关联

- git remote

	- 查远程库名
	- 远程库详情

		- -v
		- show <远程仓库名>

	-  add <远程库名> git@<域名>:<用户名>/<库名>.git

		- 空仓库名

			- 默认origin 

	- 重命名

		- rename <原名> <新名>

	- 删

		- rm <远程库名>

- 分支

	- git branch --set-upstream-to <branch-name> <远程库名>/<branch-name>
	- 本地创建

		- git checkout -b <branch-name> <远程库名>/<branch-name>
		- git checkout --track <远程仓库名>/<分支名>

			- 上条的快捷
			- 无需pull

### 克隆

- git clone <链接> [<自定义库名>]
- 其他协议

	- git://

		- git clone git@<域名>:<用户名>/<库名>.git ...
		- 默认
		- ssh

	- https ://

		- 慢
		- 每次推

			- 输指令

### 推送

- 第一次

	-  git push -u <远程库名> <分支名>

		- -u

			- 分支关联

				- 本地
				- 远程

		- [-f]

			- 可解决

				- 删提交

					- 本地reset
					- 然后push

	- 警告

		- yes

- 以后

	- git push
	-  git push <远程库名> <分支名>

- 一般要推

	- master
	- dev

### 下拉

- fetch

	- 只抓取上次提交

		- 不

			- 合并
			- 修改

	- git fetch <remote>

- pull

	- 会

		- 合并
		- 修改

	- git pull <remote> <branch>
	- git pull

- 提示

	- no tracking information

		- 没关联

### 远程库

- 分支

	- 删

		- git push <远程仓库> --delete <分支>

			- 可恢复

## 标签

### 快照

- 提交

### 查

- git tag

	- 全
	- 条件

		- -l "<条件>"

- 单

	- git show <tagname>

### 加

- 轻量级

	- git tag <tagname>

		- 也是提交
		- 默认给最近提交打

	- 可补

		- git tag <tagname> <commit>

- 附录

	- git tag -a <tagname> -m "<描述>"
	- 可补

		- git tag -a <tagname> <commit>

			- -m?

	- 重要场景

		- 如

			- 版本号

### 删

- git tag -d <tagname>

### 远程

- 推

	- git push <远程库名> <tagname>
	- 全部

		- git push <远程库名> --tags

- 删

	- 方式一

		- 删本地
		- git push <远程库名>:refs/tags/<tagname>

	- 方式二

		- git push <远程库名> --delete <tagname>

## 远程引用

### 查

- git ls-remote <remote>
- 详情

	-  git remote show <remote>

## 子模块

### 创

- git submodule init?

### 加

- git submodule add <链接> [<目录>]
- git clone --recurse-submodules <链接>
- 已克隆

	- 忘子模块初始化
	-  git submodule update --init

### 用diff

- git diff --cached <子模块名>
- git diff --cached --submodule

## git服务端

### 裸仓库

- 根目录

	- 既是.git目录

- 创

	- 本地已有

		- git clone --bare <已有仓库> <裸仓库>

	- 本地未有

		- git init --bare --shared

### 协议

- 本地

	- 路径作为 URL|

		- git <命令> <路径>
		- git <命令> file:///<路径>

			- 慢

- HTTP
- SSH

	- 不支持

		-  匿名

- git

	- 守护进程
	- 9418
	- 没权限机制

## 自定义

### 配置

- git config

	- 输出

		- [作用域] --list
		- --list --show-origin

			- 生效的值

		- git config <key>

			- 查单个

	- 设值

		- [作用域] 键 "值"

	- 作用域

		- [--system]

			- 修改权限

				- 管理员
				- 超级用户

			- 位置

				- /etc/gitconfig

		- [--global]

			- 当前用户
			- 位置

				- ~/.gitconfig

		- [--local]

			- 默认
			- 该仓库
			- 位置

				- .git/config

	- 键

		- 用户

			- user.name
			- user.email

		- 醒目

			- color.ui

				- true

	- 别名

		- git config [作用域] alias.<别名> <原命令>

			-  <原命令>

				- 如多单词

					- 单引号

### 忽略文件

- .gitignore

	- 需提交
	- 作用于

		- 当前目录

			- 及子目录

- 格式

	- 注解

		- 行

			- #

	- 文件名
	- 目录

		- 不明

			- /...
			- /.../

	- glob 模式

- 强加

	- git add -f <文件>

## 帮助

### git help <verb>

### git <verb> --help

### man git-<verb>

### 终端简明

- git <verb> -h

## 接下来

### https://git-scm.com/book/zh/v2/%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E7%9A%84-Git-%E9%85%8D%E7%BD%AE%E6%9C%8D%E5%8A%A1%E5%99%A8

*XMind - Trial Version*