#git push
>推送数据到远程仓库

##推送数据
    git push [<remote_name>] [<remote_branch_name>]
    
*   ###参数
    *   remote_name (远程库名称,默认当前)
    *   remote_branch_name (远程库分支名,默认当前HEAD所在分支的跟踪分支)
   
项目进行到一个阶段，要同别人分享目前的成果，可以将本地仓库中的数据推送到远程仓库。

##推送标签传送到远端服务器上
    git push <remote_name> <version> [--tags]
    
*   ###参数
    *   remote_name (远程库名称,默认当前)
    *   version (版本号)
   
通过显式命令分享标签到远端仓库。

````bash
$ git push origin v1.5
Counting objects: 50, done.
Compressing objects: 100% (38/38), done.
Writing objects: 100% (44/44), 4.56 KiB, done.
Total 44 (delta 18), reused 8 (delta 1)
To git@github.com:schacon/simplegit.git
* [new tag]         v1.5 -> v1.5
````

*   ###选项    
    *   --tags (一次推送所有本地标签上去)
    
````bash
$ git push origin --tags
Counting objects: 50, done.
Compressing objects: 100% (38/38), done.
Writing objects: 100% (44/44), 4.56 KiB, done.
Total 44 (delta 18), reused 8 (delta 1)
To git@github.com:schacon/simplegit.git
 * [new tag]         v0.1 -> v0.1
 * [new tag]         v1.2 -> v1.2
 * [new tag]         v1.4 -> v1.4
 * [new tag]         v1.4-lw -> v1.4-lw
 * [new tag]         v1.5 -> v1.5
````

##删除远程分支
    git push <remote_name> :<remote_branch_name>
    
*   ###参数   
    *   remote_name (远程版本库名称)
    *   remote_branch_name (远程分支名)

***
##注意事项
只有在所克隆的服务器上有写权限，或者同一时刻没有其他人在推数据，这条命令才会如期完成任务。如果在你推数据前，已经有其他人推送了若干更新，那你的推送操作就会被驳回。

你必须先把他们的更新抓取到本地，合并到自己的项目中，然后才可以再次推送。

***
##git fetch命令与git pull命令区别
fetch 命令只是将远端的数据拉到本地仓库，
并不自动合并到当前工作分支,只有当你确实准备好了，才能手工合并。

如果设置了某个分支用于跟踪某个远端仓库的分支
，可以使用 git pull 命令自动抓取数据下来，
然后将远端分支自动合并到本地仓库中当前分支。