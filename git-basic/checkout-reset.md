#理解git checkout与git reset区别
>和 reset 一样，checkout 也操纵三棵树，不过它有一点不同，这取决于你是否传给该命令一个文件路径。

##  不带路径
运行 git checkout \[branch] 与运行 git reset --hard \[branch] 非常相似，
它会更新所有三棵树使其看起来像 \[branch]，不过有两点重要的区别。

1.  首先不同于 reset --hard，checkout 对工作目录是安全的，它会通过检查来确保不会将已更改的文件弄丢，git当检查到暂存区有缓存时候，是会放弃继续执行命令的。 而 reset --hard 则会不做检查就全面地替换所有东西。

1.  第二个重要的区别是如何更新 HEAD。 当版本库多于一个分支的时候，

    reset 会移动当前分支的 HEAD指向，下一次提交时候，会基于这个reset目标分支HEAD指定的提交快照进行比较，这样操作很容易会出现很多奇怪的修改记录，而且不再继承原分支上的所有的提交记录。

    而 checkout 只会移动 HEAD 自身来指向另一个分支。
    
    总的来说，如果切换涉及其他分支的情况下，reset是不会改变当前HEAD处于哪一个分支上，而checkout是会更改当前HEAD，到目标分支上。

1.  第三个分别是reset不会改变HEAD为detached HEAD状态，相反当checkout的目标不是branch，而且该目标的提交快照不是其所属的分支中最后一次提交，HEAD会改为detached HEAD状态。

##  带路径
1.  指定路径的checkout，会像 reset 一样不会移动 HEAD。相当于git reset --hard \[branch] file_path, 那样用该次提交中的那个文件来更新索引，覆盖工作目录中对应的文件，对工作目录并不安全。

##  checkout与reset对三树影响速查表

REF:表示该命令移动了 HEAD 指向的分支引用

HEAD: 则表示只移动了 HEAD 自身

|HEAD影响|索引区|工作目录|对工作目录是否安全?
:----|:----:|:----:|:----:|:----:|:----:
**Commit Level** ||||
reset --soft \[commit]|REF|NO|NO|YES
reset \[commit]|REF|YES|NO|YES
reset --hard \[commit]|REF|YES|YES|NO
checkout \[commit]|HEAD|YES|YES|YES
**File Level** ||||
reset \[commit] \[file]|NO|YES|NO|YES
checkout \[commit] \[file]|NO|YES|YES|NO


