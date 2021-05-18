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
|`git clone [-b <branch>] <repo-resource>`|clone a repo [pointed to the specified branch]|
|`git init`|initialize a git repo|
|`git status --ignored`|show the working tree status include the ignored files|
|`git checkout -b <branch-name>`|create the branch if it doesn't exists, and jump to the branch|
|`git checkout [-p] <file>...`|discard [some parts of] the file changes|
|`git checkout <branch> -- <file>...`|checkout the file(s) in the specific branch|
|`git add [-i] <file>...`|stage the file(s) [interactively]|
|`git add -e <file>...`|stage the file(s) by using editor|
|`git add -p [<file>...]`|partial staging|
|`git add -N <file>...`|stage the file(s) with no content|
|`git add -n <file>...`|don't actually add the file(s), just show the ones which will be added|
|`git commit [-m <message>]`|commit the added files [with the message]|
|`git commit -am <message>`|add all tracked files and commit with message|
|`git reset [<file>...]`|unstage the file(s)|
|<code>git reset \<commit> [--soft&#124;--mixed&#124;--hard]</code>|reset to the specific commit, cancel the commits in the path and restore the files into index/workspace/recycle bin (`--mixed` is the default mode if not specified)|
|`git clean -n [-d] [-i] [<file-or-path>...]`|show the untracked file(s) [and directories] which will be removed from the working tree [interactively]|
|<code>git clean -n -x &#124; -X [<file-or-path>...]</code>|show the untracked and ignored/only the ignored file(s) which will be removed from the working tree|
|`git clean -f [...]`|execute `git clean` actually|
|`git merge [-m <msg>] <commit>`|merge the specific branch into current one (w/ commit message(in case one is created))|
|`git mv [-f] [-n] <file-or-directory> <destination>`|move or rename the file or directory [even if the destination exists] [w/o actual execution but just showing the expected result]|
|`git rm [--cached] [<file>...]`|remove tracked file(s) [and keep them in workspace]|
|`git ls-files`|show information about files in the index and the working tree|
|`git ls-tree -r --name-only <commit>`|list all files in the commit tree|
|<code>git push -u&#124;--set-upstream \<remote></code>|set the remote repo of the current branch and push it|
|`git push <remote> --delete <branch>`|delete the remote branch|
|git pull|= fetch + merge ...|
|git fetch|...|
|`git stash`|stash all changed files except the untracked ones|
|`git stash push [<file>...] [-m <message>]`|stash files [with custom message]|
|`git stash push -k [<file>...]`|keep the staged files and stash all(include staged)[/specific] changed ones|
|`git stash apply [--index]`|apply the stash entry to the current working tree [with keeping the stashed stage state]|
|`git stash pop ...`|like apply, but remove the entry from stash list|
|`git stash list [--date=local]`|show the stash list [with the time of creating]|
|`git diff [--cached] [<file>...]`|show the file differences [with the staged one]|
|`git diff -- <file-A> <file-B>`|show the differences between the files|
|`git diff <branch-A> <branch-B> -- <file>`|show the file differences with the one in another branch|
|`git diff <branch-A>:<file-A> <branch-B>:<file-B>`|show the file differences with another file in another branch|
|`git diff --name-status [<branch-A>] <branch-B>`|show only names and status of changed files between the branches|
|`git difftool ... [-y] [&]`|`git diff` using external tool [without prompting] [in the background]|
|`git branch <branch>`|create a new branch|
|`git branch -m [<old-branch>] <new-branch>`|rename the branch|
|`git branch -d <branch>`|delete the branch|
|`git branch --unset-upstream [<local-branch>]`|stop current[/specific] branch tracking the remote one|
|`git describe --tags --abbrev=0`|show the most recent tag|
|`git log [-<number>] [--branches] [--oneline]`|show [number] commit logs [in all branches] [in the form of one line per log]|
|`git rebase -i <commit>`|rebase the commits after the specified one|
|`git cherry-pick [-e] <commit>...`|apply the change(s) to current commit [with editing the commit message(s)]|
|`git revert [--no-edit] <commit>...`|revert the commit(s) [without editing the commit message]|
|`git reflog`|show the operating logs|
|`git remote -v`|show the remote names and urls|
|`git remote set-url <remote-name> <new-url>`|set the remote url|
|<code>git config [--local&#124;--global&#124;--system] user.name&#124;user.email \<value></code>|set [local/global/system] user name/email|

## Patch mode options
|option|description|
|---|---|
|y|stage this hunk|
|n|do not stage this hunk|
|q|quit; do not stage this hunk or any of the remaining ones|
|a|stage this hunk and all later hunks in the file|
|d|do not stage this hunk or any of the later hunks in the file|
|g|select a hunk to go to|
|/|search for a hunk matching the given regex|
|j|leave this hunk undecided, see next undecided hunk|
|J|leave this hunk undecided, see next hunk|
|k|leave this hunk undecided, see previous undecided hunk|
|K|leave this hunk undecided, see previous hunk|
|s|split the current hunk into smaller hunks|
|e|manually edit the current hunk|
|?|print help|

## Settings 
* local ignore rule: `.git/info/exclude`
* git global configurations like user, editor, tools, etc.: `~/.gitconfig`

## Notes
* `@{-N}` syntax refer to the N-th last branch/commit checked out using "git checkout/switch" operation. `-` is synonymous to `@{-1}`.

## References
* *Learn Git Branching https://learngitbranching.js.org* (圖形化 Git 學習資源)
* *Git - Reference https://git-scm.com/docs*
* *Git - Interactive Staging https://git-scm.com/book/zh-tw/v2/Git-Tools-Interactive-Staging*
