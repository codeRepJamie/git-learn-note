#git branch
>git分支操作

##查询当前分支清单
    git branch [<--remote|--merged|--no-merged>]
    
*   ###无参数无选项
查询当前版本库所有分支清单

*   ###选项
    *   remote (显示远程分支)
    *   merged (只显示已经与当前分支合并)
    *   no-merged (只显示未与当前分支合并)

```bash
$ git branch
  iss53
* master
  testing
```

##新建分支
    git branch <branch_name>
    
*   ###参数
    *   branch_name (分支名)

创建一个新的分支，仅仅是建立了一个新的分支，但HEAD不会自动切换到这个分支中去，请使用[git checkout命令][1]或者[git checkout -b命令][2]

##删除分支
    git branch -d|-D <branch_name>

*   ###参数
    *   branch_name (分支名)
*   ###选项
    *   -d (安全删除)    
    *   -D (强制删除)
    
Git可删除其它非当前分支（HEAD所在的分支）的分支，-d是限定了只能删除与其它分支有合并过的分支，原因很简单，既然已经把它们所包含的工作整合到了其他分支，删掉也不会损失什么。

[1]: git-checkout.md#让HEAD切换到某个分支 "让HEAD切换到某个分支"
[2]: git-checkout.md#新建一个分支，并让HEAD切换到这个分支上 "新建一个分支，并让HEAD切换到这个分支上"