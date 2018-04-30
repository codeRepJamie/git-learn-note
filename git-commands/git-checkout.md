#git checkout
>切换不同的分支或者索引树与工作目录文件

##commit模式
>**注意**
commit模式下git checkout，因为只切换HEAD位置，不会影响索引区与工作目录。所以请调用git status查看当前git三树状态。如果索引树或工作目录有修改，git是会终止操作。

###查看当前分支的HEAD信息
    git checkout [HEAD]
*   ###参数
    *   HEAD (当前HEAD指针，默认值）
    
```bash
M       one.js
M       work.js
Your branch is up to date with 'origin/checkTag'.
```    

###切换HEAD到某个分支上
    git checkout <branch_name>
    
*   ###参数
    *   branch_name (分支名)

操作HEAD切换到某个分支，HEAD默认是目标分支的最后一次提交快照

###新建一个分支，切换HEAD该分支上
    git checkout -b <branch_name> [<remote_name/branch_name>]
    
*   ###参数
    *   branch_name (分支名)
    *   remote_name/branch_name (创建跟踪分支)
    
>如果想拉取一个，在本地分支没有跟踪分支的远程分支，可以先执行git fetch然后再 git checkout -b <branch_name> <remote_name/branch_name>
    
````bash
$ git checkout -b iss53
Switched to a new branch 'iss53'
````

这相当于执行下面这两条命令：

```bash
$ git branch iss53
$ git checkout iss53
```
    
###切换HEAD到某个提交快照上
    git checkout (<tree-ish>|<tag_name>)
    
*   ###参数
    *   HEAD (HEAD指针，默认值）
    *   tree-ish (提交索引哈希）
    *   tag_name (标签版本）
    
切换HEAD到某个提交快照

**注意**
1.  如果该目标的提交快照不是其所属的分支中最后一次提交，HEAD的状态是detached HEAD，git会建议你使用git checkout -b <branch_name>在这个快照上新建一个分支。

##file模式
>**注意**
file模式下git checkout，不会更改HEAD，但是会修改目标文件的索引树与工作目录，保持它们与HEAD一致

###切换某个文件到某个分支/提交快照上
    git checkout (<branch_name>|HEAD|<tree-ish>|<tag_name>) [--] <file_path>
    
*   ###参数
    *   branch_name (分支名)
    *   HEAD (HEAD指针，默认值）
    *   tree-ish (提交索引哈希）
    *   tag_name (标签版本）
    *   file_path (文件路径）
    
还原git三树，与HEAD保持一致，返回到初次提交的状态，**文件上原有修改会被丢弃**

**注意**
前提是目标分支/提交快照是存在目标文件，否则git会拒绝执行

###强制撤销修改
    git checkout [--] <file_path>
    
*   ###参数
    *   file_path (文件路径）
    
更改索引树与工作目录，强制回滚到最近一次提交的状态，**文件上原有修改会被丢弃**

git checkout . 与 git reset --hard效果大致相同，但是前者可以控制撤销某个文件夹（更改.为其它路径），后者不能。