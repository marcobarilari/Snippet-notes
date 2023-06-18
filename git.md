# Git

## git flow in brief

```
git add .
git status # Lists all new or modified files to be committed
git commit -m "Second commit"
git push -u origin master
```

## 101

```
# Adds all the files in the local repository and stages them for commit
git add .

# OR add a specific file
git add README.md 

# Lists all new or modified files to be committed
git status

# The message in the " " is given so that the other users can read the message and see what changes you made
git commit -m "First commit"

# Remove the most recent commit
git reset HEAD~1

# Push changes to origin
git push -u origin master

# To show the files changes not yet staged
git diff 

# Revert back to the last committed version to the Git Repo
git checkout .

# view commit history 
git log
```

- Clone and update submodelues

```
git clone git://github.com/foo/bar.git path-where-to-clone

cd bar

git submodule update --init --recursive
```

- The commands to discard all local changes in Git are:

```
git reset –hard
git clean -fxd
```

- Reset a specific file

```
git checkout -- path/to/file

# if staged

git reset HEAD path/to/file

git checkout -- path/to/file
```
