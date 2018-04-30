#git status
>查看git工作区文件状态报告

##状态输出
    git status
    
*   ###无参数

详细的状态输出

````bash
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        README

nothing added to commit but untracked files present (use "git add" to track)
````

##紧凑的格式输出
    git status --short|-s
    
*   ###参数
    *   file_path (文件路径）

紧凑的格式输出

````bash
$ git status
M new.js
D edit.js
````