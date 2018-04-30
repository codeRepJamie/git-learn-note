#git config
>设置git

##自定义Git 命令
    git config --global alias.<custom_command_name> <commands>
    
*   ###参数
    *   custom_command_name (自定义命令名）
    *   commands (命令行文字）添加!在前，可以使用git以外的命令

可以用 git config 为命令设置别名

````bash
$ git config --global alias.last 'log -1 HEAD'

$ git config --global alias.visual '!gitk'

````