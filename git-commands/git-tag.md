#git tag
>对某一时间点上的版本打上标签

##列显已有的标签
    git tag
    
*   ###无参数

列出现有标签的命令非常简单，直接运行 git tag 即可：

````bash
$ git tag
v0.1
v1.3
````

##列出符合条件的标签
    git tag -l <version>

*   ###选项
    *   -l|--list (列表）查询标签列表   
*   ###参数
    *   version (版本号）如v1.4.2.*

用特定的搜索模式列出符合条件的标签

````bash
$ git tag -l 'v1.4.2.*'
v1.4.2.1
v1.4.2.2
v1.4.2.3
v1.4.2.4
````

##新建标签

>Git 使用的标签有两种类型：轻量级的（lightweight）和含附注的（annotated）

###轻量级（lightweight）
    git tag <version>
    
*   ###参数
    *   version (版本号）

直接给出标签名字即可


###含附注的标签（annotated）
    git tag -a <version> -m <tag_msg>
    
*   ###参数
    *   version (版本号）
    *   tag_msg (附注内容）

含附注标签实际上是存储在仓库中的一个独立对象，它有自身的校验和信息，包含着标签的名字，电子邮件地址和日期，以及标签说明，标签本身也允许使用 GNU Privacy Guard (GPG) 来签署或验证。

##补打标签
    git tag -a <version> <tree-ish>
    
*   ###参数
    *   version (版本号）
    *   tree-ish (提交索引哈希）

可以在后期对早先的某次提交加注标签

***

#git show
>查看相应标签的版本信息

##查看标签的版本信息
    git show <version>
    
*   ###参数
    *   version (版本号）

````bash
$ git show v1.4
tag v1.4
Tagger: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Feb 9 14:45:11 2009 -0800

my version 1.4

commit 15027957951b64cf874c3557a0f3547bd83b3ff6
Merge: 4a447f7... a6b4c97...
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sun Feb 8 19:02:46 2009 -0800

    Merge branch 'experiment'
````    
列出了此标签的提交者和提交时间，以及相应的标签说明。

***

##关于远程分享标签
默认情况下，git push 并不会把标签传送到远端服务器上，只有通过显式命令才能分享标签到远端仓库。其命令格式如同推送分支
请查看[push命令-推送标签传送到远端服务器上](git-push.md#推送标签传送到远端服务器上)