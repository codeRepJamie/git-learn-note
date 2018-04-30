#git diff
>查看git工作区文件具体修改哪些地方

##查看版本差异详情
    git diff

比较的是工作目录中当前文件和暂存区域快照之间的差异， 也就是修改之后还没有暂存起来的变化内容

##查看已暂存的内容
    git diff <--cached|--staged>
    
*   ###参数
    *   --cached| --staged (已暂存)

查看已暂存的将要添加到下次提交里的内容（排除了还没暂存的内容）

#git difftool
>使用第三方软件查看git diff 例如用vimdiff

##使用第三方软件查看版本差异详情
    git difftool