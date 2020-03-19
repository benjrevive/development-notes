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
|`git status --ignored`|show the ignored files|
|`git checkout -b <branch-name>`|create the branch if it doesn't exists, and jump to the branch|
|`git checkout [-p] <file>`|discard [some parts of] the file change|
|`git checkout <branch> -- <file>`|checkout the file in the specific branch|
|`git add [file(s)]`|stage the file(s)|
|<code>git add -i&#124;--interactive</code>|stage the file(s) interactively|
|`git add -p [file]`|partial staging|
|`git commit [-m "<message>"]`|commit the added files [with the message]|
|`git commit -am "<message>"`|add all tracked files and commit with message|
|`git reset [file]`|unstage the file(s)|
|<code>git reset \<commit> [--mixed&#124;--soft&#124;--hard]</code>|reset to the specific commit (回到指定的 commit 並取消路徑上所有 commit)|
|`git clean -n [file]`|show the files which will be removed from the working tree|
|`git clean -f [file]`|removed the untracked file(s) from the working tree|
|`git clean -i [file]`|removed the untracked file(s) from the working tree interactively|
|`git merge [-m <msg>] <commit>`|merge the specific branch into current one (w/ commit message(in case one is created))|
|`git rm [--cached] [file1] [file2] ...`|remove tracked file(s) [and keep them in workspace]|
|`git ls-files`|show information about files in the index and the working tree|
|git rebase ...|...|
|git push|...|
|git pull|= fetch + merge ...|
|git fetch|...|
|git stash|...|
|`git diff [--cached] [<file>]`|show the [specific] file differences [with the staged one]|
|`git diff -- <file-A> <file-B>`|show the differences between the files|
|`git diff <branch-A> <branch-B> -- <file>`|show the file differences with the one in another branch|
|`git diff <branch-A>:<file-A> <branch-B>:<file-B>`|show the file differences with another file in another branch|
|`git diff --name-status [<branch-A>] <branch-B>`|show only names and status of changed files between the branches|
|`git difftool ...`|`git diff` using external tool|
|`git branch <branch>`|create a new branch|
|`git branch -m [<old-branch>] <new-branch>`|rename the branch|
|`git branch -d <branch>`|delete the branch|
|`git push <remote> --delete <branch>`|delete the remote branch|
|`git log [-<number>] [--branches] [--oneline]`|show [number] commit logs [in all branches] [in the form of one line per log]|
|`git remote -v`|show the remote names and urls|
|`git remote set-url <remote-name> <new-url>`|set the remote url|
|<code>git config [--local&#124;--global&#124;--system] user.name&#124;user.email <email></code>|set [local/global/system] user name/email|

## Settings 
* local ignore rule: `.git/info/exclude`
* git global configurations like user, editor, tools, etc.: `~/.gitconfig`

## Notes
* `@{-N}` syntax refer to the N-th last branch/commit checked out using "git checkout/switch" operation. `-` is synonymous to `@{-1}`.

## References
* *Learn Git Branching https://learngitbranching.js.org* (圖形化 Git 學習資源)
* *Git - Reference https://git-scm.com/docs*
* *Git - Interactive Staging https://git-scm.com/book/zh-tw/v2/Git-Tools-Interactive-Staging*
