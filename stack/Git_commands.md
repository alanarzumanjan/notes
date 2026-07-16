**Rule #1 -** `Always check git status to see what has been changed , added, or removed.`
**Rule #2 -** `Always check git branch --all to make sure you are on the correct branch`

Git configuration
```shell
git config --global user.name "Username"
```

```shell
git config --global user.email "email@email.com"
```

Folder add git visibale and controll
```shell
git init
```

```shell
git remote add origin https://github.com/alanarzumanjan/Project_one.git
```

Clone repository
```shell
git clone (link repository)
```

Push first commit on branch
```shell
git push origin master
```

```shell
git checkout (commit hash)
```

```shell
git pull origin master
```

Check branchs
```shell
git branch
```

Add branch
```shell
git branch <branch-name>
```

Go to branch
```shell
git checkout <branch-name>
```

Public push new-branch
```shell
git push origin <branch-name>
```

Merge branches
```shell
git merge <branch-name>
```

Rebase branch
```shell
git rebase <branch-name>
```

=======

Check the status of the directory
```shell
git status
```
Add files to tracking (staging)
```shell
git add .
```
Reset tracked files (staged files)
```shell
git reset
```
Show history of committed changes (log history)
```shell
git log
```
Commit (Save) staged changes in history 
```shell
git commit -m "Commit  message"
```

```shell
git commit -m "
- Deleted by ...
- ...
"
```
Push changes of repository (to bitbucket)
```shell
git push
```
Check branches
```shell
git branch --all
```
Pull the latest changes from BitBucket dashboard
```shell
git pull
```
Switch to a branch
```shell
git checkout <branch name>
```
Show difference between changes
```shell
git diff
```

```shell
git diff --staged
```

Revert all uncommitted changes:
```shell
git checkout -- .
```

Absolutely reset commits and clear files from staged
```bash
git reset --mixed HEAD~1
```

Backup commit
```shell
git revert HEAD
```

Clean new files (`-f` all)
```shell
git clean <files-name>
```

```shell
git push origin --delete <branch name>
```
