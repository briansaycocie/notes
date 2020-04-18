# Git Commands

## Start project from scratch
```bash
mkdir /path/to/your/project
cd /path/to/your/project
git init
git remote add origin git@github.com:briansaycocie/project_name.git
```

## Add existing project
```bash
cd /path/to/my/repo
git init
git remote add origin git@github.com:briansaycocie/project_name.git
git push -u origin --all # pushes up the repo and its refs for the first time
git push -u origin --tags # pushes up any tags
```

## Clone in existing folder
```bash
cd /path/to/my/repo
git init
git remote add origin git@github.com:briansaycocie/project_name.git
git fetch origin
git checkout -b master --track origin/master
```

## Ignore committed files
```bash
git update-index --assume-unchanged path/to/file.txt
git update-index --no-assume-unchanged path/to/file.txt
```

## Undo local commit
```bash
git reset HEAD~1
```

## Remove local untracked files from working tree
```bash
git clean -n (shows what will be deleted)
git clean -f (deletes files)
git clean -fd (deletes files and directories)
git clean -fX (deletes ignored files)
git clean -fx (deletes ignored and non-ignored files)
```

## Merge feature_branch to master
```bash
commit changes in feature_branch
git co master
git merge --no-ff feature_branch
(if push failed) git reset --hard origin/master
git push
```

## Revert merge
```bash
git reset --merge ORIG_HEAD
git reset --hard HEAD
```

## Create new branch
```bash
git checkout -b new_branch
```

## Checkout new branch
```bash
git fetch && git checkout new_branch
```

## Clone specific branch
```bash
git clone git@github.com:briansaycocie/project_name.git -b branch_name
```

## Tag and archive branch
```bash
git co feature_branch
git tag archive/feature_branch
git push origin archive/feature_branch
git co master
git branch -d feature_branch
git push origin --delete feature_branch
```

## Remove local branch
```bash
git branch -D local_branch
```

## Remove remote branch
```bash
git push origin :remote_branch
```

## Configure upstream, git pull short command
```bash
git branch --set-upstream-to=origin/<branch>
```

## Fix “your branch is ahead of x by x commits”##
```bash
git reset --hard origin/master
```

## Replace local branch with remote branch entirely
```bash
git reset --hard origin/master
```

## Bring old feature branch up-to-date with master
```bash
git co feature/branch
git rebase master
```

## Change repo url
```bash
git remote -v
git remote set-url origin git@bitbucket.org:user_name/project_name.git (or git remote rm origin, then git remote add origin git@bitbucket...)
git remote -v
```

## Remove file from repo
```bash
git rm --cached file.js
```

## Sync forked repo with master repo
```bash
git pull upstream master
```