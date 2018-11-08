#git add -i
>交互式暂存，如果希望一些改动能放到若干提交而不是混杂在一起成为一个提交时，希望这些改动能放到若干提交而不是混杂在一起成为一个提交时,这几个工具会非常有用。并且可以撤销一些暂存提交。

##推送数据
    git add -i
    
*   ###参数
    *   -i/--interactive Git 将会进入一个交互式终端模式
   
````bash
           staged     unstaged path
  1:        +6/-0      nothing base.js
  2:        +2/-0        +1/-0 one.js
  3:        +5/-0      nothing work.js

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
What now> 
````