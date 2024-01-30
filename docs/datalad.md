# datalad

## Routine checks

```
# faster status check when there are big subadatasets (what it truly does is not clear yet))
datalad status -e commit

# list which files are where
git anex list

```

## Things are fucked up

```
# go back to last commit
git reset --mixed 11b4c2711602b6020df90eec438c09bb22e8567f

# drop last changes only for untracked files
git clean -df && git checkout -- .

# drop any modification
git reset --hard

# reset a file to last saved changes
git reset -- path_to_file

# restore a speciic delete file 
git restore path/to/file

# There is no active branch, cannot determine remote branch
git reflog 

git checkout master

git merge --ff-only last-commit-hash-number-from-git reflog
```

### specific errors

### pushing

```bash
Update availability for 'origin':  75%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████                                                 | 3.00/4.00 [00:00<00:00, 2.02k Steps/sCommandError: 'git -c diff.ignoreSubmodules=none -c core.quotepath=false push --progress --porcelain origin main:main git-annex:git-annex' failed with exitcode 128 under /Volumes/JOE/Datalad/2023_Liege_BLAM_MB_raw/sourcedata                                                    
CommandError: 'ssh -o ControlPath=/Users/barilari/Library/Caches/datalad/sockets/30c2438d git@gin.g-node.org 'git-receive-pack '"'"'/cpp-lln-lab/2023_Liege_BLAM_MB_source.git'"'"''' failed with exitcode 255
send-pack: unexpected disconnect while reading sideband packet
Delta compression using up to 4 threads
fatal: the remote end hung up unexpectedly
```

`git gc --aggressive`

## clean up

```
# get rid of data that have no active link within the current commit
git annex unused

git annex dropunused all

# datalad is stuper slow
# it cpould be a problem of indexing especially if moving from one OC to another. This routing command might initiate a re-indexing
git status
```

## Other source of snippet codes

- [jadecci.github.io Datalad Cheatsheet](https://jadecci.github.io/notes/Datalad.html)

## Quick tutorials
