#git reset
>操作HEAD指针，实现版本库全部或部分文件可以回退到某次提交

##commit模式

###回退HEAD到某个分支/提交快照
    git reset (<branch_name>|HEAD|<tree-ish>|<tag_name>) [--mixed | --soft | --hard | --merge | --keep]
    
*   ###参数
    *   branch_name (分支名）
    *   HEAD (当前HEAD指针，默认值）
    *   tree-ish (提交索引哈希）
    *   tag_name (标签版本）
*   ###选项
    *   \[--mixed | --soft | --hard | --merge | --keep] （修改模式，默认是--mixed）

git根据不同的修改模式，操作三个树回退任意一个提交快照，默认状态下，当前所有更改回退到unstaged状态

**注意**
当涉及其它分支的reset，git会移动当前分支的 HEAD指向，详情请看[理解git checkout与git reset区别](../git-basic/checkout-reset.md))

###回退整个暂存区的修改
    git reset
git会撤销当前整个暂存区的更改，当前所有更改回退到unstaged状态

###清空所有更改
    git reset --hard
git会撤销当前三个树所有更改，包括工作目录文件，此时working tree 是干净的。

所以git checkout . 与 git reset --hard效果大致相同，但是前者可以控制撤销某个文件夹（更改.为其它路径），后者不能。

##file模式
###回退某个文件/文件夹的索引树，到某个分支/提交快照
    git reset (<branch_name>|HEAD|<tree-ish>|<tag_name>) [--] <file_path>
    
*   ###参数
    *   branch_name (分支名）
    *   HEAD (HEAD指针，默认值）
    *   tree-ish (提交索引哈希）
    *   tag_name (标签版本）
    *   file_path (文件路径）

回退某个文件，到某个提交快照，由于reset是带路径模式，reset会跳过更改HEAD指向这步骤，保持原有的HEAD指向，更改目标文件在staged状态下的修改，工作目录不改变。假如需要修改工作目录，请使用[checkout命令](git-checkout.md)

###撤销暂存修改
    git reset [HEAD] <file_path>
    
*   ###参数
    *   HEAD (当前HEAD指针，默认值）
    *   file_path (文件路径）

撤销某个文件staged修改，回退到unstaged状态

###注意事项
如果reset的提交快照是另外一个分支下的，git是会移动当前分支的 HEAD指向，改变其HEAD parent commit tree修改为目标分支下的commit tree。详情查看，[checkout与reset的区别](../git-basic/checkout-reset.md)