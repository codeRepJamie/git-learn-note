#git cherry-pick
>可以让你从在已提交的commit中提取多个commit作为当前分支新的修改commit。例如可以实现把分支A的更改在分支B重新提交一遍。前提条件是你的工作树必须为空的无修改（干净的）状态。

##推送数据
    git cherry-pick [-e] [-n] [<branch_name>|<tree-ish>]
    
*   ###参数
    *   branch_name (分支名,默认当前HEAD所在分支的跟踪分支)
    *   tree-ish (提交索引哈希，可以使用多个，用空格隔开）
    
*   ###选项
    *   -e|--edit 修改上一次commit提交的信息
    *   -n|--no-commit 只是在当前分支上apply这些commits的改变，但是不提交到当前分支
    
````bash
F:\mac\WebstormProjects\WebstormProjects\gitLearn>git cherry-pick d318fc6
[checkTag 999f510] :
 Date: Mon Nov 12 21:54:04 2018 +0800
 1 file changed, 1 insertion(+), 1 deletion(-)    
````    
    
当提交了一个cherry-pick会出现下列步骤：

1.  当前分支盒HEAD头会保持在最后一次成功commit
1.  CHERRY_PICK_HEAD 引用会设定在提取目标的提交commit
1.  那些已经提交完成的更改，它们的文件路径会在暂存区和工作树这两个工作区更新
1.  对于那些存在冲突的文件，暂存区会把该文件记录成3个版本，称之为“可信的合并”，原理与[git merge合并](git-merge.md)相同。工作树的文件在冲突的地方注释不常用到的冲突符号<<<<<<< 和 >>>>>>>
1.  没有任何修改