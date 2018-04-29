#文件状态

*   ###Untracked: 未跟踪文件

    >定义：没有被git跟踪的文件，通常是新添加的文件，上一个commit不存在的文件
    
    git status 显示内容
    
    缩写：<font color=red>??</font> (<font color=red>红色</font>)
    
    ```bash
    Untracked files:
    (use "git add <file>..." to include in what will be committed)

        new.js
    ```
    
    git status -s 显示内容
    
    ```bash
    ??  new.js
    ```
    
*   ###*Unstage*: 修改未在暂存区
        
    >定义：所有的更改未提交到暂存区的文件集合（未使用 git add 命令）
    
    缩写：<font color=red>`M `</font> <font color=red>`D `</font> (<font color=red>红色</font>，右面)
    
    ```bash
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)
    
            modified:   new.js
            modified:   README.md
    ```
    
    git status -s 显示内容
    
    ```bash
     M new.js
     D edit.js
    ```
    
*   ###Stage: 修改已在暂存区状态
    
    >定义：所有的更改已提交暂存区且准备提交到库的文件集合：更改包括以下动作
    
    缩写：<font color=green>`M `</font> <font color=green>`A `</font> <font color=green>`D `</font> <font color=green>`R `</font> (<font color=green>绿色</font>，左面)
    
    ```bash
    Untracked files:
    (use "git add <file>..." to include in what will be committed)

        new.js
    ```
    
    git status -s 显示内容
    
    ```bash
    M  new.js
    D  edit.js
    ```