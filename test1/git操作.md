## git add -A 和 git add . 的区别 

git add -A和 git add .   git add -u在功能上看似很相近，但还是存在一点差别

**git add** . ：他会监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。

**git add -u** ：他仅监控已经被add的文件（即tracked file），他会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file）。（git add --update的缩写）

**git add -A** ：是上面两个功能的合集（git add --all的缩写）

- 总结

·  git add -A  **提交所有变化**

·  git add -u  **提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)**

·  git add .  **提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件**

********

## 撤销操作

- git status 先看一下add 中的文件 
- git reset HEAD 如果后面什么都不跟的话 就是上一次add 里面的全部撤销了 
- git reset HEAD XXX/XXX/XXX.java 就是对某个文件进行撤销了



## Git中git commit -m 与git commit -a -m  的区别 

一般仓库中的文件可能存在于这三种状态：

1）**Untracked files** → 文件未被跟踪；

2）**Changes to be committed** → 文件已缓存，这是下次提交的内容；

3）**Changes bu not updated** → 文件被修改，但并没有添加到缓存区。

**git commit -m **  只会提交添加到缓存区的文件**（**只提交添加的**）

**git commit -a -m ** 能提交修改过，但是没有添加到缓存区的文件（**修改过的就能提交**）

**git commit -a**   就是自动去把之前标记过的文件再标记上，包括删除的文件，但是不包括新增的文件。

使用命令：git log  能查看提交历史，后面加上  --pretty=oneline  能使内容单行显示

使用命令：git status  能让我们时刻掌握仓库当前的状态


## git本地检出一个新的分支并推送到远程仓库

git checkout -b 新分支名

+ 推送本地分支到远程仓库

**git push --set-upstream origin**

eg:
git push --set-upstream origin  release

这个只是切换分支如果需要将内容推送上去，还需要执行

+ git add -u 添加修改过的文件
+ git commit -m 'XXX' 提交修改过的文件
+ git push origin release  将修改过的文件推送到远程分支

## 将远程git仓库里的指定分支拉取到本地（本地不存在的分支）

**git checkout -b 本地分支名 origin/远程分支名**
这个将会自动创建一个新的本地分支，并与指定的远程分支关联起来。
例如远程仓库里有个分支develop,我本地没有该分支，我要把develop拉到我本地：

有时候会报错
fatal: Cannot update paths and switch to branch 'dev2' at the same time.
这个时候需要执行

**git fetch**

然后再执行
**git checkout -b 本地分支名 origin/远程分支名**

## git关联本地仓库和远程仓库

我们在本地新建一个叫devtest的分支的时候，我们希望他与git远程上的某个分支进行关联。

假设远程上的那个分支也叫devtest，如果我们直接去pull代码，会报下面的错
提示我们需要用 –set-upstream 去关联这两个分支，命令是

git branch --set-upstream devtest origin/devtest
你执行这句命令之后，他又会提示你–set-upstream要换成–set-upstream-to命令

–set-upstream-to 在新版本git中已经替代了 –set-upstream， 并且后面跟随的两个参数要对调一下，如下面命令

**git branch --set-upstream-to origin/develop develop**

## 分支合并
git的分支合并一般都在本地进行，在分支合并的时候创建一个新的文件夹，然后重新down一份新的代码到这个文件夹中（避免idea等工具生成的文件的影响），然后在这个新的文件夹中进行文件的合并

### 合并分支
#### release分支合并
* 为release新建工作空间，并clone相应的代码到工作空间
* 切换分支到develop_merge
* 执行git pull origin develop_merge
* 切换分支到release
* 执行git merge develop_merge
* 执行git status，查看当前代码状态
* 执行git pull origin release
* 执行git push origin release 

#### master分支合并
* 为master新建工作空间，并clone相应的代码到工作空间
* 切换分支到release
* 执行git pull origin release 
* 切换分支到master
* 执行git merge release 
* 执行git status，查看当前代码状态
* 执行git pull origin master
* 执行git push origin master



 git status -uno 查看冲突文件
  git add  提交文件
  
  git commit  -m'all'   提交加入satge的文件










