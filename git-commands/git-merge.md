#git merge
>合并目标分支到当前的分支

##合并目标分支到当前的分支
    git merge <branch_name>
    
*   ###参数
    *   branch_name 分支名

##快进（简单）合并
如果目标分支是从基于当前分支分出去的（当前分支是目标分支的直接祖先），并且当前分支在合并之前没有任何提交，那么 Git 在合并两者时，只会简单地把指针右移，因为这种单线的历史分支不存在任何需要解决的分歧，所以这种合并过程可以称为快进（Fast forward）

```bash
$ git checkout master
$ git merge hotfix
Updating f42c576..3a0874c
Fast-forward
 README | 1 -
 1 file changed, 1 deletion(-)
```

##复杂合并提交
如果当前分支，在合并之前已经有其它提交或者当前分支并不是目标分支的直接祖先。Git会分别找出目标分支与当前分支的**共同祖先**、当前分支最后提交快照、目标分支最后提交快照，进行一次简单的三方合并计算（这里有可能出现冲突解决情况）。最后Git则会打开vi编辑文档，要求你编写提交注释，Git 会额外提交一次合并提交（merge commit）到当前分支上，最后合并完成。这是一个特殊的提交，因为它是来自两个不同的祖先。

另外复杂合并提交还有一种解决方案叫分支变基，详情查看[git rebase命令](git-rebase.md)

```bash
Merge made by the 'recursive' strategy.
 one.js | 4 +++-
 1 file changed, 3 insertions(+), 1 deletion(-)
```

##冲突合并
如果合并的时候遇到冲突情况，不同的分支中都修改了同一个文件的同一部分，只能又人工裁决

```bash
$ git merge iss53
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

Git 作了合并，但没有提交，它会停下来等你解决冲突。要看看哪些文件在合并时发生冲突

当前文件目录如有冲突，git status状态如下

```bash
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:      index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

解决冲突，git status状态如下

```bash
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   index.html
```

如果觉得满意了，并且确认所有冲突都已解决，也就是进入了暂存区，就可以用 git commit 来完成这次合并提交