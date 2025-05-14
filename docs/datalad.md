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
# OR
# Saved changes on a "detached" branch and switching to master "deleted what just saved

git reflog 

git checkout master # or main

git merge --ff-only hash_number_commit_save_in_no_specific_branch 
```

### repo set up

#### change what git-annex should annex (source: github copilot)

To tell git-annex not to annex files ending with .mat, you can configure the .gitattributes file to mark such files as not being large files. Here's how you can do it:

Steps:
1. Open or create the .gitattributes file in your repository.
2. Add the following line to exclude .mat files from being annexed:

```bash
*.mat annex.largefiles=nothing
```

Explanation:
`*.mat`: Matches all files ending with `.mat`.
`annex.largefiles=nothing`: Tells git-annex not to treat these files as large files, so they will be handled by regular Git instead of being annexed.
Example `.gitattributes` File:
Apply the Changes:
After updating the `.gitattributes` file, if `.mat` files have already been annexed, you need to move them back to regular Git:

1. Find the `.mat` files currently annexed:

```bash
git annex find --include="*.mat"
```

2. Unannex the `.mat` files:

```bash
git annex unannex "*.mat"
```

3. Commit the changes:

```bash
git add .gitattributes
git commit -m "Exclude .mat files from git-annex"
```

Now, `.mat` files will be tracked by regular Git instead of being annexed.

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
