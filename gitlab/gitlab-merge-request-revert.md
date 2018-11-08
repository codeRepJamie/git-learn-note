#如何撤销 Merge Request？
>GitLab 组合了 Git的强大功能可以撤销任何的commit提交。当你需要撤销你之前merge request过的代码，以下就介绍在GitLab上是如何操作

##撤销一个Merge Request
1.  当一个 Merge Request 已经合并了，会出现一个名为 Revert 按钮，让你撤回当前的Merge Request。
![image](src/cherry_pick_changes_mr.png)
1.  按下按钮后，一个弹出会出现，GitLab会让你选择两种不同的方法，方法1：直接撤销该分支（不建议），方法2：新建一个新的merge request[^1]用来提交撤销操作（建议）。
1.  如果上一步选择了新的merge request来执行撤销操作，只需要合并该merge request就完成操作。
### 注意
1.  一旦撤销成功，Revert 按钮就不可再点击
1.  如果目标分支是保护分支（protected branch）直接在目标分支做撤销操作通常是不起作用[^2]

##如何重新提交
1.  由于被撤销合并的分支已经在目标分支合并过，所以继续在被撤销的分支上再提交mr不会引起

[^1]: Git此时会自动生成一个新的revert分支
[^2]: 此处未经过任何验证，建议使用方法2