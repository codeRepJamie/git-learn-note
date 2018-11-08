#git stash
>当你在项目的一部分上已经工作一段时间后，所有东西都进入了混乱的状态，而这时你想要切换到另一个分支做一点别的事情。 问题是，你不想仅仅因为过会儿回到这一点而为做了一半的工作创建一次提交。 针对这个问题的答案是 git stash 命令

##储藏修改
    git stash
当前状态:
````bash
$ git status
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   index.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   lib/simplegit.rb
````

````bash
git stash
Saved working directory and index state WIP on master: 84dfd50 this is change at github master
````
再次查看目录是工作目录是干净的了：
````bash
git status
# On branch master
nothing to commit, working directory clean
````
在这时，你能够轻易地切换分支并在其他地方工作；你的修改被存储在栈上。 要查看储藏的东西，可以使用 git stash list：
````bash
$ git stash list
stash@{0}: WIP on master: 84dfd50 added the index file
stash@{1}: WIP on master: c264051 Revert "added file_size"
stash@{2}: WIP on master: 21d80a5 added number to log
````

##取回修改
    git stash apply [<stash_name>]
    
*   ###参数   
    *   stash_name (储存名称)    
    
在本例中，有两个之前做的储藏，所以你接触到了三个不同的储藏工作。 可以通过原来 stash 命令的帮助提示中的命令将你刚刚储藏的工作重新应用：git stash apply。
````bash
git stash apply
# On branch master
# Changed but not updated:
#   (use "git add <file>..." to update what will be committed)
#
#      modified:   index.html
#      modified:   lib/simplegit.rb
#
````
这样之前的修改就会重回工作区。
##注意事项
如果想要应用其中一个更旧的储藏，可以通过名字指定它，像这样：git stash apply stash@{2}。 如果不指定一个储藏，Git 认为指定的是最近的储藏

##删除储藏修改
    git stash drop [<stash_name>]
    
*   ###参数   
    *   stash_name (储存名称)     
    
应用选项只会尝试应用暂存的工作 - 在堆栈上还有它。 可以运行 git stash drop 加上将要移除的储藏的名字来移除它： 

````bash
git stash list
stash@{0}: WIP on master: 049d078 added the index file
stash@{1}: WIP on master: c264051 Revert "added file_size"
stash@{2}: WIP on master: 21d80a5 added number to log
$ git stash drop stash@{0}
Dropped stash@{0} (364e91f3f268f0900bc3ee613f9f733e82aaed43)
````