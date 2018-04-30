#git fetch
>从远程仓库抓取数据，合并到跟踪分支，此命令对本地同名分支不会有任何操作，与之对应请查看[git pull命令](git-pull.md)

##从远程仓库抓取数据
###拉取所有远程分支数据
    git fetch
    
*   ###无参数
此命令会到（上次 fetch 以来别人提交的更新的）
远程仓库中拉取**所有**你本地仓库中还没有的数据，合并到本地远程分支，同名的本地分支不会受此影响。

````bash    
    git fetch [<remote_name>] <remote_branch_name>
````    
    
*   ###参数
    *   remote_name (指定远程版本库名，默认gei config中的默认远程版本库）
    *   remote_branch_name (指定分支名，默认当前分支）
    
指定/默认远程仓库中拉取指定的远程分支，合并到跟踪分支，同名的本地分支不会受此影响。

````bash
$ git fetch pb
remote: Counting objects: 58, done.
remote: Compressing objects: 100% (41/41), done.
remote: Total 44 (delta 24), reused 1 (delta 0)
Unpacking objects: 100% (44/44), done.
From git://github.com/paulboone/ticgit
 * [new branch]      master     -> pb/master
 * [new branch]      ticgit     -> pb/ticgit
````

##git fetch命令与git pull命令区别
fetch 命令只是将远端的数据拉到跟踪分支，
并不自动合并到当前同名本地分支,只有当你确实准备好了，才能手工合并，调用git merge合并同名本地分支。

如果设置了某个分支用于跟踪某个远端仓库的分支
，可以使用 [git pull](git-pull.md) 命令自动抓取数据下来，
然后将远端分支自动合并到本地仓库中当前分支。

如果目标的远程分支，在本地分支没有跟踪分支,可以使用[git checkout -b](git-checkout.md#新建一个分支，切换HEAD该分支上)