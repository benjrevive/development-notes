# git-notes

> “Branch early, branch often”

Atomic commits (https://hearrain.com/git-zui-jia-shi-jian-:-yuan-zi-xing-ti-jiao-atomic-commits)

Git best practices

## Terms

* staged: ready to be committed
* hunk: the changed section

## Commands
|command|description|
|---|---|
|`git clone <repo-resource>`|clone a repo|
|`git init`|initialize a git repo|
|`git checkout -b <branch-name>`|create the branch if it doesn't exists, and jump to the branch|
|`git checkout <file>`|discard the file change|
|`git checkout <branch> -- <file>`|checkout the file in the specific branch|
|`git add [file(s)]`|stage the file(s)|
|<code>git add -i&#124;--interactive</code>|interactive mode|
|`git add -p [file]`|partial staging|
|`git commit [-m "<message>"]`|commit the added files [with the message]|
|`git commit -am "<message>"`|add all tracked files and commit with message|
|`git reset [file]`|unstage the file(s)|
|<code>git reset \<commit> [--mixed&#124;--soft&#124;--hard]</code>|reset to the specific commit (回到指定的 commit 並取消路徑上所有 commit)|
|`git merge [-m <msg>] <commit>`|merge the specific branch into current one (w/ commit message(in case one is created))|
|git rebase ...|...|
|git push|...|
|git pull|= fetch + merge ...|
|git fetch|...|
|git stash|...|
|`git difftool [--cached] [<file-in-another-branch>] [<local-file>]`|show file differences using external tool|
|`git branch -d <branch>`|delete the branch|
|`git log [-<number>] [--oneline]`|show [number] commit logs [in the form of one line per log]|
|`git remote -v`|show the remote names and urls|
|`git remote set-url <remote-name> <new-url>`|set the remote url|
|<code>git config [--local&#124;--global&#124;--system] user.name&#124;user.email <email></code>|set [local/global/system] user name/email|

## Settings 
* local ignore rule: `.git/info/exclude`
* git global configurations like user, editor, tools, etc.: `~/.gitconfig`

## References
* *Learn Git Branching https://learngitbranching.js.org* (圖形化 Git 學習資源)
* *Git - Reference https://git-scm.com/docs*
* *Git - Interactive Staging https://git-scm.com/book/zh-tw/v2/Git-Tools-Interactive-Staging*
