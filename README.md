# git-study


## 我的

* 基本

```shell
# 工作区 -> 暂存区
git add 
# 暂存区 -> 工作区
git restore
# 暂存区 -> 本地仓库
git commit -m ''
# 本地仓库 -> 暂存区
git restore --unstaged
```

* 删除远程分支

```shell
git push -u origin --delete wuyq54517
```

* 展示远程仓库信息

```shell
git remote show origin
```

* git gui

```shell
gitk --all

git log --graph --oneline --all
```

* 合并

```shell
# 将分支合并到当前HEAD中
git merge <branch>
```

* 克隆

```shell
git clone git@github.com:wuyq54517/git-study.git
```

* 拉取

```shell
git pull git@github.com:wuyq54517/git-study.git
```

* 更新最近提交信息

```shell
git commit --amend
```

* 修改旧提交或多个提交的消息

使用 `git rebase -i HEAD~n` 命令在默认文本编辑器中显示最后一次 `n` 提交的列表。

```shell
git rebase -i HEAD~n
```

* remote

```shell
# 添加
git remote add origon git@github.com:wuyq54517/git-study.git
```

* 查看信息

```shell
git status
```

* 查看不同

```shell
git diff
```

* 草稿

```shell
# 将此草稿保存
git stash 
# 查看
git stash list
# 读取
git stash apply stash@{0}
# 删除
git stash drop stash@{0}
```

* 分支

```shell
# 新建分支
git checkout <branch>
# 新建并且切换分支
git checkout -b <branch>
```

* 标签

```shell
# 给当前版本打标签
git tag <tag-name>
# 给当前版本打标签并且附加消息
git tag -a <tag-name>
# 推送
git push -u origon --tags
```



## Git 分支开发

Git 是目前最流行的源代码管理工具。为规范开发，保持代码提交记录以及 git 分支结构清晰，方便后续维护，现规范 git 的相关操作。

### 分支命名

1、master 分支

master 为主分支，也是用于部署生产环境的分支，确保master分支稳定性， master 分支一般由develop以及hotfix分支合并，任何时间都不能直接修改代码

2、develop 分支

develop 为开发分支，始终保持最新完成以及bug修复后的代码，一般开发的新功能时，feature分支都是基于develop分支下创建的。

- feature 分支

开发新功能时，以develop为基础创建feature分支。 分支命名: feature/ 开头的为特性分支， 命名规则: feature/user_module、 feature/cart_module

- release分支

release 为预上线分支，发布提测阶段，会release分支代码为基准提测。当有一组feature开发完成，首先会合并到develop分支，进入提测时会创建release分支。如果测试过程中若存在bug需要修复，则直接由开发者在release分支修复并提交。当测试完成之后，合并release分支到master和develop分支，此时master为最新代码，用作上线。

- hotfix 分支

分支命名: hotfix/ 开头的为修复分支，它的命名规则与feature分支类似。线上出现紧急问题时，需要及时修复，以master分支为基线，创建hotfix分支，修复完成后，需要合并到master分支和develop分支

更多开发规范请参阅：[全网最全的 Git 分支开发规范手册](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzI0MDQ4MTM5NQ%3D%3D%26mid%3D2247501314%26idx%3D2%26sn%3Daefe2614bf85f7035a445e59fe9df84f%26chksm%3De918a31ede6f2a084d39e68721928a416a6a447a0876b74630a4d65011e80e0b1ce65b3ca8a2%26token%3D1267489950%26lang%3Dzh_CN%23rd) | [掌握这10条规范，轻松搞定Git！](https://mp.weixin.qq.com/s?__biz=MzI0MDQ4MTM5NQ==&mid=2247486125&idx=1&sn=ce871dd581b847ce8d6418f616d208ef&chksm=e91b6fb1de6ce6a7129022c167e46b780a0a4a91d7e54c6c3de63b1121c3f487bf561f9c13c5&token=1267489950&lang=zh_CN#rd)