

## Routine checks

```
# list which files are where
git anex list
```

## Things are fucked up

```
# go back to last commit
git reset --mixed 11b4c2711602b6020df90eec438c09bb22e8567f

# drop last changes (untracked)
git clean -df && git checkout -- .

# reset a file to last saved changes
git reset -- path_to_file
```

## clean up

```
# get rid of data that have no active link within the current commit
git annex unused

git annex dropunused all
```

## Other source of snippet codes

- [jadecci.github.io Datalad Cheatsheet](https://jadecci.github.io/notes/Datalad.html)

## Quick tutorials
