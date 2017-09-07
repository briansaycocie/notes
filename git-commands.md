# Git Commands #

## Git workflow ##
1. branch off master
2. edit feature branch
3. merge feature branch to staging
4. fix .scss conflicts manually
5. run "grunt css"
6. add conflicted files back
7. git commit
8. git push

## Start project from scratch ##
```bash
mkdir /path/to/your/project
cd /path/to/your/project
git init
git remote add origin git@bitbucket.org:user_name/project_name.git
```

## Add existing project ##
```bash
cd /path/to/my/repo
git init
git remote add origin git@bitbucket.org:user_name/project_name.git
git push -u origin --all # pushes up the repo and its refs for the first time
git push -u origin --tags # pushes up any tags
```

## Clone in existing folder ##
```bash
cd /path/to/my/repo
git init
git remote add origin git@bitbucket.org:user_name/project_name.git
git fetch
git checkout -t origin/master
```

## Ignore committed files ##
```bash
git update-index --assume-unchanged path/to/file.txt
git update-index --no-assume-unchanged path/to/file.txt
```

## Undo local commit ##
```bash
git reset HEAD~1
```

## Merge feature_branch to master ##
```bash
commit changes in feature_branch
git co master
git merge --no-ff feature_branch
(if push failed) git reset --hard origin/master
git push
```

## Revert merge ##
```bash
git reset --merge ORIG_HEAD
git reset --hard HEAD
```

## Create new branch ##
```bash
git branch new_branch
```

## Checkout new branch ##
```bash
git fetch && git checkout blog
```

## Clone specific branch ##
```bash
git clone git@bitbucket.org:user_name/project_name.git -b branch_name
```

## Tag and archive branch ##
```bash
git co feature_branch
git tag archive/feature_branch
git push origin archive/feature_branch
git co master
git branch -d feature_branch
git push origin --delete feature_branch
```

## Remove local branch ##
```bash
git branch -D local_branch
```

## Remove remote branch ##
```bash
git push origin :remote_branch
```

## Configure upstream, git pull short command ##
```bash
git branch --set-upstream-to=origin/<branch>
```

## Fix “your branch is ahead of x by x commits”##
```bash
git reset --hard origin/master
```

## Replace local branch with remote branch entirely ##
```bash
git reset --hard origin/master
```

## Bring old feature branch up-to-date with master ##
```bash
git co feature/branch
git rebase master
```

## Remove local untracked files from working tree ##
```bash
git clean -n (shows what will be deleted)
git clean -f (deletes files)
git clean -fd (deletes files and directories)
git clean -fX (deletes ignored files)
git clean -fx (deletes ignored and non-ignored files)
```

## Change repo url ##
```bash
git remote -v
git remote set-url origin git@bitbucket.org:user_name/project_name.git (or git remote rm origin, then git remote add origin git@bitbucket...)
git remote -v
```

## Remove file from repo ##
```bash
git rm --cached file.php
```

## Sync forked repo with master repo ##
```bash
git pull upstream master
```

## Fix “repository access denied” ##
```bash
ssh-add ~/.ssh/id_rsa
```

## Deployment config ##
### Setup ###
```bash
git config git-ftp.url sftp://host_ip:port/wp-content/themes/theme
git config git-ftp.user ftp-user
git config git-ftp.password ‘secr3t’
git config git-ftp.key ~/.ssh/id_rsa
```

### Upload all files, initial deploy ###
```bash
git ftp init
```

### Push to FTP again ###
```bash
git ftp push
```

### If the files are already there ###
```bash
git ftp catchup
```

### Add scope ###
```bash
git ftp add-scope production sftp://ftpuser:secr3t@host_ip/wp-content/themes/theme (or)
git config git-ftp.production.url host_ip/path/to/theme
git config git-ftp.production.user ftpuser
git config git-ftp.production.password ‘secr3t'
```

### After add scope ###
```bash
git ftp init -s production
git ftp push -s production
```