
1.https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000(廖雪峰的官方网站)<br>
2.https://juejin.im/post/5c33f49de51d45523070f7bb(git操作)
### # 0.分支:feature_short_message上操作
git add .--->git commit -m "update" -->git pull --rebase origin release2-2(远程分支) -->git push -u origin feature_short_message 
ping 域名查对应的 ip地址: ping + weimob.com

#### # 1. git add 添加 多余文件 
这样的错误是由于， 有的时候 可能

git add . （空格+ 点） 表示当前目录所有文件，不小心就会提交其他文件

git add 如果添加了错误的文件的话

撤销操作

git status 先看一下add 中的文件 
git reset HEAD 如果后面什么都不跟的话 就是上一次add 里面的全部撤销了 
git reset --hard e20abc6  回退指定的版本代码
git reset HEAD 如果后面什么都不跟的话 就是上一次add  
git reset HEAD XXX.js 就是对某个文件进行撤销了

#### 2. git commit 错误

如果不小心 弄错了 git add后 ， 又 git commit 了。 
先使用 
git log 查看节点 
commit xxxxxxxxxxxxxxxxxxxxxxxxxx 
Merge: 
Author: 
Date:

然后 
git reset commit_id

git reset commit_id （回退到上一个 提交的节点 代码还是原来你修改的） 

git reset –hard commit_id （回退到上一个commit节点， 代码也发生了改变，变成上一次的）

#### 3.如果要是 提交(commit)了以后，可以使用 git revert

还原已经提交的修改 
此次操作之前和之后的commit和history都会保留，并且把这次撤销作为一次最新的提交 
git revert HEAD 撤销前一次 commit 
git revert HEAD^ 撤销前前一次 commit 
git revert commit-id (撤销指定的版本，撤销也会作为一次提交进行保存） 
git revert是提交一个新的版本，将需要revert的版本的内容再反向修改回去，版本会递增，不影响之前提交的内容
4.git merge --abort 撤销上一次的合并分支

5.将本地新建的项目部署到 远程仓库:<br>
a.进入项目所在目录执行 git init 命令把Project变成git可以管理的仓库
git init <br>

b.把本地仓库与Coding远程仓库关联

git remote add origin 地址 <br>
例子:git remote add origin
ssh://git@stash.weimob.com:7999/mdda/weimob-sms.git

c.在本地新建一个 分支

git checkout -b release3-3

d.把文件添加到仓库
git add .

e.把文件放到仓库

git commit -m "add all files"

f.把本地库的所有内容推送到Coding远程库上

git push -u origin release3-3

g.如果推送失败，很可能是远程仓库创建了README.md文件，而这个文件不在本地方库中
代码合并
git pull --rebase origin master

执行完之后会看到本地仓库项目中多了个README.md文件

再次将本地库中所有内容推送到Coding远程库上
git push -u origin master <br/>
<br><br>6.将当前分支(feature/v1.0.0)代码**合并**到另一个分支(feature/v1.0.1)==:<br/> a.先 git checkout feature/v1.0.0--> git add .-->git commit -m "提交"-->git pull-->git push <br/>b.git checkout feature/v1.0.1--->git merge feature/v1.0.0(或者git rebase -i feature/v1.0.0,如果有conflict,解决冲突,git rebase --abort  退出 git rebase)-->git add .-->git commit -m '合并'-->git pull-->git push 
<br><br>7.webstorm 在==远程develop分支==新建一个 develop-picture-compress分支:<br>a.git checkout develop(切换到develop分支) <br>b.git branch -b develop-picture-compress(创建新分支并切换到 develop-picture-compress分支)<br>c.git pull(拉取最新代码)<br>d.git add . -->git commit-->git push (将新建分支及代码推送到远程,此时在develop分支上,本地和远程都建了新的develop-picture-compress分支)
<br><br>8.git fetch(webstorm-->vcs-->git fetch) 获取远程所有分支
<br><br>9.webstorm 合并远程 feature/v1.0.1和feature/v1.0.0(远程)两个分支:
<br>a.a.git checkout feature/v1.0.0-->git add .-->git commit -->git pull -->git push
<br>b.git checkout feature/v1.0.1-->git add .-->git commit -->git pull -->git push -->鼠标点击选中 远程分支 feature/v1.0.0(远程和本地代码同步最新)-->点击 Merge into Current -->如果有冲突,解决conflict-->git add .-->git commit -->git push 
<br><br>10.git stash 使用
<br><1>git stash会把所有未提交的修改（包括暂存的和非暂存的）都保存起来，用于后续恢复当前工作目录
<br><2>git stash list 查看 stash缓存列表
<br><3>git stash pop 取出 所有stash缓存列表
<br><4>git stash pop stash@{0} 取出 stash指定的 stash@{0}缓存列表
<br><5>git stash clear  注意这是清空所有的stash缓存列表
<br><6>git stash drop stash@{0}  这是删除指定的第一个队列