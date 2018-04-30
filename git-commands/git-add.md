#git add
>git开始跟踪一个文件

##开始跟踪某个文件
    git add <file_path>
    
*   ###参数
    *   file_path (文件路径）

监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区,包括文件内容修改(modified)以及新文件(untracked file),但不包括删除(deleted)文件

##仅监控已经被追踪过的
    git add --update / -u
    
*   ###选项
    *   --update / -u (仅监控已经被追踪过的文件）

仅监控已经被追踪过的文件（即tracked file），他会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file)