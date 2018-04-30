#git status
>让git发起一次提交到版本库

##提交代码到版本库
    git commit [<file_path>]
    
*   ###无参数
git会提交所有在暂存区内的代码

*   ###参数
    *   file_path (文件路径）
git会提交在暂存区自定文件路径下的代码  

git一般会启动vim作为编辑软件，让你编写提交commit comment（提交注解）

##快捷添加备注信息
    git commit -m
    
直接将提交信息comment与命令放在同一行

##跳过暂存步骤
    git commit -a
    
Git 就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add . 步骤，相当于帮你执行多一步 git add .

##修改上一次提交
    git commit --amend
    
Git会修改上一次提交，包括提交注释

##修改提交默认使用上一次提交的注释
    git commit --amend --no-edit
    
提交代码并默认使用上一次提交的注释

##相关知识
每次提交后 HEAD 都会自动随着分支一起向前移动