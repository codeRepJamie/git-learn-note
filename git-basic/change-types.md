#修改类型

##changes包含以下动作

*   ###modified(M)
    >修改文件内容，部分或全部
    
*   ###new file(A)
    >添加新文件
    
    上一次提交到版本库没有存在的文件
    
    因为git要通过比对才会有结果，所以此状态只有 stage状态，其他情况，一律都是 untracked
    
*   ###deleted(D)
    >已删除文件,删除上一次提交到版本库的文件
    
    通过调用 git rm <file_path>
    
*   ###renamed(R)
    >已改名文件
    
    更改上一次提交过文件的文件名
    
    通过调用 
    `git mv file_from file_to`
    相当于调用
    
    ```bash
    mv a.js b.js
    git rm a.js
    git add b.js
    ```
    
    因为git要通过比对才会有结果，所以此状态只有 stage状态