#git remote
>设置远程仓库命令

##查看当前的远程库
    git remote [-v]
    
*   ###选项
    *   -v | --verbose; (显示对应的克隆地址）

要查看当前配置有哪些远程仓库，一般默认是origin

````bash
$ git remote
origin

$ git remote -v
origin  git://github.com/schacon/ticgit.git (fetch)
origin  git://github.com/schacon/ticgit.git (push)

````

##添加远程仓库
    git remote add <remote_name> <git_path>
    
*   ###参数
    *   remote_name (远程版本库名）
    *   git_path (远程版本库地址）

要添加一个新的远程仓库，可以指定一个简单的名字，以便将来引用

````bash
$ git remote
origin
$ git remote add pb git://github.com/paulboone/ticgit.git
$ git remote -v
origin  git://github.com/schacon/ticgit.git
pb  git://github.com/paulboone/ticgit.git
````

##查看远程仓库信息
    git remote show <remote-name>
    
*   ###参数
    *   remote_name (远程版本库名）

它友善地告诉你如果是在 master 分支，就可以用 git pull 命令抓取数据合并到本地。另外还列出了所有处于跟踪状态中的远端分支。
上面的例子非常简单，而随着使用 Git 的深入，git remote show 给出的信息可能会像这样：

````bash
$ git remote show origin
* remote origin
  URL: git@github.com:defunkt/github.git
  Remote branch merged with 'git pull' while on branch issues
    issues
  Remote branch merged with 'git pull' while on branch master
    master
  New remote branches (next fetch will store in remotes/origin)
    caching
  Stale tracking branches (use 'git remote prune')
    libwalker
    walker2
  Tracked remote branches
    acl
    apiv2
    dashboard2
    issues
    master
    postgres
  Local branch pushed with 'git push'
    master:master
````

它告诉我们，运行 git push 时缺省推送的分支是什么（译注：最后两行）。
它还显示了有哪些远端分支还没有同步到本地（译注：第六行的 caching 分支），
哪些已同步到本地的远端分支在远端服务器上已被删除（译注：Stale tracking branches 下面的两个分支），以及运行 git pull 时将自动合并哪些分支（译注：前四行中列出的 issues 和 master 分支）。

##远程仓库重命名
    git remote rename <remote_old_name> <remote_new_name>
    
*   ###参数
    *   remote_old_name (原远程版本库名）
    *   remote_new_name (新远程版本库名）

在新版 Git 中可以用 git remote rename 命令修改某个远程仓库在本地的简称，比如想把 pb 改成 paul，可以这么运行：

````bash
$ git remote rename pb paul
$ git remote
origin
paul
````

注意，对远程仓库的重命名，也会使对应的分支名称发生变化，原来的 pb/master 分支现在成了 paul/master。

##远程仓库的删除
    git remote rm <remote_name>
    
*   ###参数
    *   remote_name (远程版本库名）

碰到远端仓库服务器迁移，或者原来的克隆镜像不再使用，又或者某个参与者不再贡献代码，那么需要移除对应的远端仓库，可以运行 git remote rm 命令：
