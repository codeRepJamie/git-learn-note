#术语表

##  untracked
未跟踪状态，未暂存状态一种

##  unmodified
未更改状态

##  modified
已更改，未暂存状态一种

##  staged
已暂存状态

##  unstaged
未暂存状态，有可能是未跟踪（untracked），或者是已更改（modified）

## file_path
## file_from
## file_to
该参数使用标准的[glob 模式][1]匹配

例如:
*   "."代表整个项目库
*   "*"匹配零个或多个任意字符
*   "**"表示匹配任意中间目录

## HEAD
HEAD 是当前分支引用的指针，它总是指向该分支上的最后一次提交。 这表示 HEAD 将是下一次提交的父结点。 通常，理解 HEAD 的最简方式，就是将它看做 你的上一次提交 的快照。
HEAD 只是一个指针或者只是一个引用，不负责储存或更改任何数据文档

## --soft
添加此选项，Git会检索指定的提交快照提取数据，更改当前的HEAD在分支的指向，此操作会更改当前分支的最近一次提交记录为HEAD所在的位置

## --mixed
添加此选项，Git会检索指定的提交快照提取数据，更改当前的HEAD分支指向（单个文件模式会跳过此步骤），更改索引树（即暂存区staged的文件）

## --hard
添加此选项，Git会检索指定的提交快照提取数据，更改当前的HEAD分支指向（单个文件模式不能使用此选项，请使用checkout命令），更改索引树（即暂存区staged的文件），以及工作目录树（当前受影响的文件），
此命令操作后，该文件在git的三个工作区（树）是保持一致的。
此选项为危险操作，撤销后的文件数据一般不能恢复

## --merge
## --keep

##跟踪分支
##tracking branch
从远程分支 checkout 出来的本地分支，称为 跟踪分支 (tracking branch)。跟踪分支是一种和某个远程分支有直接联系的本地分支。在跟踪分支里输入 git push，Git 会自行推断应该向哪个服务器的哪个分支推送数据。同样，在这些分支里运行 git pull 会获取所有远程索引，并把它们的数据都合并到本地分支中来。


[1]: https://baidu.com/q?glob