# git-notes

> “Branch early, branch often”

Atomic commits (https://hearrain.com/git-zui-jia-shi-jian-:-yuan-zi-xing-ti-jiao-atomic-commits)

Git best practices

## Terms

* staged: ready to be commited
* hunk: the changed section

## Commands
|command|description|
|-|-|
|`git clone <repo-resource>`|clone a repo|
|`git init`|initialize a git repo|
|`git checkout -b <branch-name>`|create the branch if it doesn't exists, and jump to the branch|
|`git add [file(s)]`|stage the file(s)|
|<code>git add -i&#124;--interactive</code>|interactive mode|
|`git add -p [file]`|partial staging|
|`git reset [file]`|unstage the file(s)|
|<code>git reset \<commit> [--mixed&#124;--soft&#124;--hard]</code>|reset to the specific commit (回到指定的 commit 並取消路徑上所有 commit)|
|`git merge [-m <msg>] <commit>`|merge the specific branch into current one (w/ commit message(in case one is created))|
|git rebase ...|...|
|git push|...|
|git pull|= fetch + merge ...|
|git fetch|...|
|git stash|...|
|`git config [--global] user.email <email>`|set user email|
|`git config [--global] user.name <username>`|set user name|

## References
* *Learn Git Branching https://learngitbranching.js.org* (圖形化 Git 學習資源)
* *Git - Reference https://git-scm.com/docs*