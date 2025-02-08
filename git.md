Read [[git theory]] for terms and definitions.
# Setup
```shell
paru -S git github-cli

gh auth login
```

```shell
git config --global user.name "Arvind Rana"
git config --global user.email "arvindrana6969@gmail.com"
git config --global init.defaultBranch main
```
**NOTE**: This is stored in `~/.gitconfig` file.
# Create remote repository
```shell
# To create public repository
gh repo create <project_name> --public

# To create private repository
gh repo create <project_name> --private
```
**NOTE**: ONLY use one of the above.
# For first time
```shell
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/arv1ndrana/<project_name>.git
git push -u origin main
```
# For updating remote repository
```shell
git add .
git commit -m "<suitable message>"
git push -u origin main
```
**NOTE**: Do this AFTER making changes to local repository.
# For accidental add of file
```shell
git restore --staged <file>
```
NOTE: `<file>`can also be path.
# For changing last commit message
```shell
git commit --amend
```
# For undoing change on file to last commit
```shell
git checkout -- <file>
```
# For undoing change on file to any commit
```shell
git log
```
- Copy desired commit's hash
- Something like "f193ee95bd1a113ae1aa5c2573d0cb68593d4b3b"
```shell
git checkout <hash> -- <file>
```
# For deleting last commit(untested)
```shell
# To undo the last commit, keeping its changes (and any further uncommitted changes) in the filesystem
git reset HEAD~

# To undo the last two commits, adding their changes to the index, i.e. staged for commit
git reset --soft HEAD~2
```
**NOTE**: You can use HEAD~2 (at last) for deleting two commits and so-on.
# For forcefully pushing to github forcefully
```shell
git push -u origin <branch> --force
```
**WARNING**: Only use this IF you don't care about your remote repository.
# For undoing to last commit in local folder (untested) (wtf does undoing mean)
```shell
git revert <commit ID>

git checkout -- .
```
# For commit history
```shell
git log
```
**NOTE**: top -> bottom ==>  new -> old
# For listing branch
```shell
# To list branch from local repository
git branch

# To list branch from remote repository
git branch -r
```
# For deleting branch
```shell
# To delete branch remotely (BE CAREFUL! THE ACTION IS IRREVERSIBLE)
git push origin --delete <branch>

# To delete a local <branch>
git branch -d <branch>
```
**WARNING**: Deleting branch remotely WILL delete the branch completely.
# For changing branch from master to main
Move the source from master to main branch
```shell
git branch -m master main
```
Add and commit your changes
```shell
git add .
git commit -m "Change master branch to main"
```
Set upstream and push changes to remote
```shell
git push -u origin main
```
# Miscellaneous (no clue)
```shell
# To update in github after removing a commit in local folder
git rebase --continue
```

# For visualizing commits
```shell
git log --graph --decorate --oneline $(git rev-list -g --all)
```