# 需求
- [需求1:小项目放在github上一般流程如下](https://github.com/LinXueyuanStdio/learnGit#需求1小项目放在github上一般流程如下)
- [需求2:参与github开源项目提交pull-request](https://github.com/LinXueyuanStdio/learnGit#需求2参与github开源项目提交pull-request)
- [需求3:撤销与还原commit](https://github.com/LinXueyuanStdio/learnGit#需求3撤销与还原commit)
- [需求4:remote origin already exists](https://github.com/LinXueyuanStdio/learnGit#需求4:remote origin already exists.)
- [需求5:Permission denied (publickey).](https://github.com/LinXueyuanStdio/learnGit#需求5:Permission denied publickey.)
- [需求6:failed to push som refs to](https://github.com/LinXueyuanStdio/learnGit#需求6:failed to push som refs to)
- [需求7:RPC failed](https://github.com/LinXueyuanStdio/learnGit#需求7:RPC failed)
- [需求8](https://github.com/LinXueyuanStdio/learnGit#需求8)
# 目录
- [套路](https://github.com/LinXueyuanStdio/learnGit#套路)
- [最基本的命令](https://github.com/LinXueyuanStdio/learnGit#最基本的命令)
  - [显示信息类命令](https://github.com/LinXueyuanStdio/learnGit#显示信息类命令)
  - [创建类命令](https://github.com/LinXueyuanStdio/learnGit#创建类命令)
  - [撤销类命令](https://github.com/LinXueyuanStdio/learnGit#撤销类命令)
  - [提交类命令](https://github.com/LinXueyuanStdio/learnGit#提交类命令)
  - [删除类命令](https://github.com/LinXueyuanStdio/learnGit#删除类命令)
  - [merge类命令](https://github.com/LinXueyuanStdio/learnGit#merge类命令)
- [Git常用命令](https://github.com/LinXueyuanStdio/learnGit#git-常用命令)
  - [远程仓库相关命令](https://github.com/LinXueyuanStdio/learnGit#远程仓库相关命令)
  - [分支(branch)操作相关命令](https://github.com/LinXueyuanStdio/learnGit#分支branch操作相关命令)
  - [版本(tag)操作相关命令](https://github.com/LinXueyuanStdio/learnGit#版本tag操作相关命令)
  - [子模块(submodule)相关操作命令](https://github.com/LinXueyuanStdio/learnGit#子模块submodule相关操作命令)

# 需求

## 需求1：小项目放在github上，一般流程如下：[ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

1. 新建一个repository

2. 在本地目录下打开命令行，输入`git clone https://github.com/LinXueyuanStdio/learnGit`
以本项目为例，直接在git clone后加上网址即可。clone完成后会得到一个learnGit文件夹

3. 继续输入`cd learnGit`进入项目文件夹

4. 把需要上传的文件粘贴到learnGit文件夹内，使用`git add file`将新文件加入缓存区

5. `echo "ss" >> file`(非必须)该命令意思是给文件名为`ｆｉｌｅ`的文件写入字符串`ss`.

6. `git status`查看git add之后和之前的文件差异状态

7. `git commit -m "new file"`确定提交刚刚add后的文件，`-m "new file"`意思是本次提交所做的修改的简要介绍，m是message的缩写

8. `git push -u origin master`向github服务器推送git commit 后的文件，流程完毕

## 需求2：参与github开源项目，提交pull request：[ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

1. fork原始仓库

以此项目为例：[https://github.com/lzjqsdd/scikit-learn-doc-cn](https://github.com/lzjqsdd/scikit-learn-doc-cn) 右上角有个fork，点击fork到自己的仓库

2. clone 自己的仓库: `git clone https://github.com/LinXueyuanStdio/scikit-learn-doc-cn`　到本地。这个项目就是上面所说的项目拷贝。

3. 在 master 分支添加原始仓库为远程分支:`git remote add upstream https://github.com/lzjqsdd/scikit-learn-doc-cn`.

4. 如果fork的项目有更新怎么办呢？如果重新再fork这个项目的话，自然也是没有问题的，只不过这样是不是有点太low了

解决方式是:

- 拉取远程分支: `git fetch upstream` .

- 切换到想要更新的目录，合并分支: `git merge upstream/master`  // 把远程分支的master分支合并到当前分支，这样远程项目中的修改就合并到了本地。


5. 自己分支开发，如 dev 分支开发：

- `git checkout -b dev`.


6. 本地 dev 提交

- `git add *`.

- `git commit -m "update"`.


7. 切换 master 分支，同步原始仓库：

- `git checkout master`.

- `git pull upstream master`.


8. 切换本地 dev 分支，合并本地 master 分支（已经和原始仓库同步），可能需要解冲突

- `git checkout dev`.

- `git merge master`.


9. 提交本地 dev 分支到自己的远程 dev 仓库

- `git push origin dev`.


10. 现在才是给原始仓库发 pull request 请求,等待原作者回复（接受/拒绝）

到原始仓库页面，这时右边多出一个commit pull request按钮，点击，填写改动信息，完啦。

11. (附)删除分支

- `git push origin :dev`  # 删除远程dev分支，危险命令哦
###### 下面两条是删除本地分支
- `git checkout master`  # 切换到master分支
- `git branch -d dev`  # 删除本地dev分支

12. (附)查看所有分支

- `git branch --all`.

## 需求3：撤销与还原commit：[ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

撤销commit有很多方法，个人比较推荐用 reset 或 rebase -i，底下将会同时介绍 revert 和 reset 的方法。
commit 如下
```shell
A -> B -> C -> D -> E
```
想要还原到 commit C 之后的状态 (也就是把 D 和 E 回退)

1. `revert`
用：
```shell
git revert E
git revert D
```
结果：
```shell
A -> B -> C -> D -> E -> F -> G
```
F 是还原 commit E 修改结果的 commit

G 是还原 commit D 修改结果的 commit

因此，`revert` 只会`让 commit 继续往前`

优点是可以针对某个 commit 进行还原，并且留下还原记录

2. `rebase -i`

假如想要抽掉某个 commit 又不想留下记录, `rebase -i `就很好用了

假如只想要还原 D 变成：
```shell
A -> B -> C -> E
```
则用命令
```shell
git rebase -i C
```
这时候会出现文字编辑
```shell
pick D xxx
pick E ooo
```
把 `pick D xxx` 整列移除后储存就可以了，若中间有遇到冲突，则必须自行修正后再继续
```shell
git add .
git rebase --continue
```
3. reset
用于做整段 commits 的还原

例如希望还原到 B commit 以后的状态变成
```shell
A -> B
```
则
```shell
git reset B
```
那么 git 会将 log 中的 C, D, E 都清除

但档案内容没有任何变动，因此会看到 C, D, E 修改的档案处在 unstaged 阶段

若针对部分档案还原可以用
```shell
git checkout [file path]
```
若要全部还原可用
```shell
git checkout -f
```
4. 结论
还没 `push` 前，个人倾向不产生太多 `commit`。因此我都会用 `rebase -i` 进行编修, 顺便合并或`reword` 一些 `commit`

某个特殊情况, 例如发现某个 `commit` 里面包含了不相干的档案, 欲重新 `commit` 时，就会先用 `rebase -i` 把欲修改的 `commit` 换到后面(较新), 然后再用 `reset` 重新 `stage` + `commit`。

## 需求4:remote origin already exists. [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

如果输入`$ git remote add origin git@github.com:djqiang（github帐号名）/gitdemo（项目名）.git`

提示出错信息：`fatal: remote origin already exists.`

解决办法如下：
1. 先输入`$ git remote rm origin`
2. 再输入`$ git remote add origin git@github.com:djqiang/gitdemo.git` 就不会报错了！
3. 如果输入`$ git remote rm origin` 还是报错的话，`error: Could not remove config section ‘remote.origin’. `我们需要修改`gitconfig`文件的内容
4. 找到你的`github`的安装路径，我的是`C:\Users\ASUS\AppData\Local\GitHub\PortableGit_ca477551eeb4aea0e4ae9fcd3358bd96720bb5c8\etc`
5. 找到一个名为`gitconfig`的文件，打开它把里面的[remote "origin"]那一行删掉就好了！

## 需求5:Permission denied (publickey). [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

如果输入`$ ssh -T git@github.com`

出现错误提示：`Permission denied (publickey).`因为新生成的`key`不能加入`ssh`就会导致连接不上`github`。

解决办法如下：
1. 先输入`$ ssh-agent`，再输入`$ ssh-add ~/.ssh/id_key`，这样就可以了。
2. 如果还是不行的话，输入`ssh-add ~/.ssh/id_key` 命令后出现报错`Could not open a connection to your authentication agent.`
  解决方法是`key`用`Git Gui`的`ssh工具`生成，这样生成的时候`key`就直接保存在`ssh`中了，不需要再`ssh-add`命令加入了，其它的`user`，`token`等配置都用命令行来做。
3. 最好检查一下在你复制`id_rsa.pub`文件的内容时有没有产生多余的空格或空行，有些编辑器会帮你添加这些的。

## 需求6:failed to push som refs to [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

如果输入`$ git push origin master`

提示出错信息：`error:failed to push som refs to …….`

解决办法如下：
1. 先输入`$ git pull origin master` //先把远程服务器github上面的文件拉下来
2. 再输入`$ git push origin master`
3. 如果出现报错 `fatal: Couldn’t find remote ref master`或者`fatal: ‘origin’ does not appear to be a git repository`以及`fatal: Could not read from remote repository.`
4. 则需要重新输入`$ git remote add origingit@github.com:djqiang/gitdemo.git`

## 需求7:RPC failed [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

从 github 执行 `git pull` 的时候提示 `error: RPC failed`，如：

`error: RPC failed; result=52, HTTP code = 0 fatal: The remote end hung up unexpectedly`

应该是pull 内容更新太多，需要设置postBuffer更大些

`git config --global http.postBuffer 524288000`





# 套路 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

`mkdir  ADirectory`#本地随意创建一个文件夹 

`cd ADirectory`#进到该目录

`git clone  git@github.com:username/ADirectory.git`#github创建仓库ADirectory之后,把github上的git下载到本地

`git remote add origin git@github.com:username/ADirectory.git`#github创建hahaha，把本地的库hahaha与github上的git关联

`git config --global user.name "ThisIsUserName"`#配置用户名和邮箱

`git config --global user.email ThisIsUserEmail@email.com `.

`git init`#初始化为本地的仓库 

`touch readme`#新建一个文件

`echo something >> readme`#随便写入什么东西

`git add readme`   #每次更新都要add，添加到缓冲区

`git status`   #查看状态，查看哪些文件改变了但还未commit

`git diff`   #查看文件改变的内容        

`git commit - m '1'`#提交到本地代码库    

`git status`#再次查看文件改变的内容

`git log`#查看git的记录

`git checkout`#撤销操作

`git diff`#这次本地修改和你上次commit的差别

`git status` #会提示你add或者checkout

`git checkout --file` 就能恢复到上次提交的内容.若是add过,`git reset HEAD ThisIsAFile`就能从缓存区删掉

`git push -u origin master`#把本地的文件都推上去

`git pull`#把github的文件都拉下来


# 最基本的命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

`git clone` 拷贝并跟踪远程的master分支。跟踪的好处是以后可以直接通过pull和push命令来提交或者获取远程最新的代码，而不需要指定远程分支名字。

`git submodule init`

`git submodule update`

参考示意图

HEAD 指向当前的commit 对象(可以想象为当前分支的别名)，同时也用来表明我们在哪个branch上工作。所以当我们使用HEAD来操作指针的时候，其实就是不改变当前的commit的指向。


## 显示信息类命令  [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

`git ls-files -u` 显示冲突的文件，-s是显示标记为冲突已解决的文件

`git diff` 对比工作区和stage文件的差异 

`git diff` --cached 对比stage和branch之间的差异

`git branch` 列出当前repository下的所有branch 

`git branch --a` 列出local 和remote下的所有branch

`git ls-files --stage` 检查保存在stage的文件

`git log` 显示到HEAD所指向的commit为止的所有commit记录 。使用reset HEAD~n 命令使HEAD指针向前移动，会导致HEAD之后的commit记录不会被显示。

`git log -g`则会查询reflog去查看最近做了哪些动作，这样可以配合git branch 恢复之前因为移动HEAD指针所丢弃的commit对象。如果reflog丢失则可以通过`git fsck --full`来查看没被引用的commit对象。

`git log -p -2` 对比最新两次的commit对象 

`log -1 HEAD`

`git log --pretty=oneline`

`git log --stat 1a410e` 查看sha1为1a410e的commit对象的记录

`git blame -L 12,22 sth.cs` 如果你发现自己代码中 的一个方法存在缺陷,你可以用git blame来标注文件,查看那个方法的每一行分别是由谁 在哪一天修改的。下面这个例子使用了-L选项来限制输出范围在第12至22行

## 创建类命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

`git brach branchName` 创建名为branchName的branch 

`git checkout branchName` 切换到branchName的branch 

`git checkout -b` 创建并切换，也就是上面两个命令的合并

`git brach branchName ef71` 从commit ef71创建名为branchName的branch

## 撤销类命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

#### 如果是单个文件 

1. use "`git reset HEAD <file>...`" to unstage 

如果已经用add 命令把文件加入stage了，就先需要从stage中撤销，然后再从工作区撤销 

2. use "`git checkout -- <file>...`" to discard changes in working directory

`git checkout a.txt` 撤销a.txt的变动（工作区上的文件） 

#### 如果是多个文件 

1.`git chenkout` 如果已经commit了，则需要 `git commit --amend` 来修改，这个只能修改最近上一次的,也就是用一个新的提交来覆盖上一次的提交。因此如果push以后再做这个动作就会有危险

2.`$ git reset --hard HEAD` 放弃工作区和index的改动,HEAD指针仍然指向当前的commit.这条命令同时还可以用来撤销还没commit的merge,其实原理就是放弃index和工作区的改动，因为没commit的改动只存在于index和工作区中。

`$ git reset --hard HEAD^` 用来撤销已经commit的内容(等价于 git reset --hard HEAD~1) 。原理就是放弃工作区和index的改动，同时HEAD指针指向前一个commit对象。

3.`git revert` 也是撤销命令，区别在于reset是指向原地或者向前移动指针，git revert是创建一个commit来覆盖当前的commit,指针向后移动

## 提交类命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

1. `git add` 跟踪新文件或者已有文件的改动，或者用来解决冲突

2. `git commit` 把文件从stage提交到branch

3. `git commit -a` 把修改的文件先提交到stage,然后再从stash提交到branch

#### add，commit，push的区别 

[（本地工作目录）--add-->（缓存区）--commit-->（本地的git库）] ——-push———>（github）

## 删除类命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

1. `git rm --cached readme.txt` 只从stage中删除，保留物理文件

2. `git rm readme.txt` 不但从stage中删除，同时删除物理文件

3. `git mv a.txt b.txt` 把a.txt改名为b.txt

## Merge类命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

在冲突状态下，需要解决冲突的文件会从index打回到工作区。

1. 用工具或者手工解决冲突 

2. git add 命令来表明冲突已经解决。 

3. 再次commit 已解决冲突的文件。

$ `git reset --hard ORIG_HEAD` 用来撤销已经commit 的merge. 

$ `git reset --hard HEAD` 用来撤销还没commit 的merge,其实原理就是放弃index和工作区的改动。

`git reset --merge ORIG_HEAD`，注意其中的--hard 换成了 --merge，这样就可以避免在回滚时清除working tree。


# Git 常用命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)

## 远程仓库相关命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)
- 检出仓库：   `$ git clone git://github.com/jquery/jquery.git`

- 查看远程仓库：`$ git remote -v`

- 添加远程仓库：`$ git remote add [name] [url]`

- 删除远程仓库：`$ git remote rm [name]`

- 修改远程仓库：`$ git remote set-url --push [name] [newUrl]`

- 拉取远程仓库：`$ git pull [remoteName] [localBranchName]`

- 推送远程仓库：`$ git push [remoteName] [localBranchName]`

*如果想把本地的某个分支test提交到远程仓库，并作为远程仓库的master分支，或者作为另外一个名叫test的分支，如下： 
`$git push origin test:master`         // 提交本地test分支作为远程的master分支

`$git push origin test:test`              // 提交本地test分支作为远程的test分支 

## 分支(branch)操作相关命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)
- 查看本地分支：`$ git branch`

- 查看远程分支：`$ git branch -r`

- 创建本地分支：`$ git branch [name]` ----注意新分支创建后不会自动切换为当前分支

- 切换分支：`$ git checkout [name]`

- 创建新分支并立即切换到新分支：`$ git checkout -b [name]`

- 删除分支：`$ git branch -d [name]` ---- -d选项只能删除已经参与了合并的分支，对于未有合并的分支是无法删除的。如果想强制删除一个分支，可以使用-D选项

- 合并分支：`$ git merge [name]` ----将名称为`[name]`的分支与当前分支合并

- 创建远程分支(本地分支push到远程)：`$ git push origin [name]`

- 删除远程分支：`$ git push origin :heads/[name]` 或 `$ gitpush origin :[name] `


*创建空的分支：(执行命令之前记得先提交你当前分支的修改，否则会被强制删干净没得后悔) 
`$git symbolic-ref HEAD refs/heads/[name]`

`$rm .git/index`

`$git clean -fdx `

## 版本(tag)操作相关命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)
- 查看版本：`$ git tag`

- 创建版本：`$ git tag [name]`

- 删除版本：`$ git tag -d [name]`

- 查看远程版本：`$ git tag -r`

- 创建远程版本(本地版本push到远程)：`$ git push origin [name]`

- 删除远程版本：`$ git push origin :refs/tags/[name]`

- 合并远程仓库的tag到本地：`$ git pull origin --tags`

- 上传本地tag到远程仓库：`$ git push origin --tags`

- 创建带注释的tag：`$ git tag -a [name] -m 'yourMessage'`

 
 
## 子模块(submodule)相关操作命令 [ < Back to 目录](https://github.com/LinXueyuanStdio/learnGit#目录)
- 添加子模块：`$ git submodule add [url] [path]`

如：`$git submodule add git://github.com/soberh/ui-libs.git src/main/webapp/ui-libs`
 
- 初始化子模块：`$ git submodule init`  ----只在首次检出仓库时运行一次就行

- 更新子模块：`$ git submodule update` ----每次更新或切换分支后都需要运行一下

- 删除子模块：（分4步走哦）

1) `$ git rm --cached [path]`

2) 编辑`“.gitmodules”`文件，将子模块的相关配置节点删除掉

3) 编辑`“ .git/config”`文件，将子模块的相关配置节点删除掉

4) 手动删除子模块残留的目录

5）忽略一些文件、文件夹不提交
在仓库根目录下创建名称为“.gitignore”的文件，写入不需要的文件夹名或文件，每个元素占一行即可，如
```
target
bin
*.db
```
