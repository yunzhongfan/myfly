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

##  撤销操作


- git status 先看一下add 中的文件
在**我未提交之前**，我发现添加文件5555555555555内容有误，所以我得马上恢复以前的版本，现在我可以有如下几种方法可以做修改：

第一：如果我知道要删掉那些内容的话，直接手动更改去掉那些需要的文件，然后add添加到暂存区，最后commit掉。

第二：我可以按以前的方法直接**恢复到上一个版本**。使用 git reset –hard head^ （这意味着必本地的代码回退到上个版本后，需要在重新 pull 一次，才能保证本地库的代码和远程分支的代码版本相同，否则本地的代码版本比远程分支低，容易覆盖远程的代码）

**用命令丢弃本地文件的代码修改**

*  git checkout -- 文件名

eg：$ git checkout -- git操作.md

命令 $ git checkout -- git操作.md 意思就是，把readme.txt文件在工作区做的修改全部撤销，这里有2种情况，如下：

* 1.git操作.mdt自动修改后，还没有放到暂存区，使用 撤销修改就回到和版本库一模一样的状态。

* 2.**另外一种是readme.txt已经放入暂存区了，接着又作了修改，撤销修改就回到添加暂存区后的状态.**
 **其实也就是撤销到最后一次没有放入暂存区的状态**

[效果](https://blog.csdn.net/zch501157081/article/details/51939854)




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


## 解决冲突
[廖雪峰git官网](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840202368c74be33fbd884e71b570f2cc3c0d1dcf000)

在本地合并产冲突的原因 分支1 修改问文件commit后未远程push到远程，然后切换分支到分分之二，再次commit到分支2 ，然后在merge分支1和分支2产生冲突；git merge feature1

打开冲突文件把冲突文件把冲突结局然后在git add -u ;git  commit -m '结局冲突' git push orgin 分支2

Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容，我们修改如下后保存：



