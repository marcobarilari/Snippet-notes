# Data management

## Datalad

```
datalad create -c text2git mydataset

datalad clone git@gin.g-node.org:/RemiGau/V5_high-res_pilot-1_source.git

# submodules
datalad clone -d git@gin.g-node.org:/RemiGau/V5_high-res_pilot-1_source.git

datalad siblings add --name gin --url

datalad save -m 'add mri data'

datalad push --to gin

datalad drop .

datalad get .

datalad subdatasets --set-property url git@gin.g-node.org:/marcobarilari/analysis_high-res_pilot001_ses-006_derivatives-cpp_spm-stats.git cpp_spm-stats/
```

to get information about the size of a given repo

```
datalad status --annex all

# output example:

24155 annex'd files (6.1 GB/50.9 GB present/total size)
nothing to save, working tree clean
```

## Terminal

Copy a simulink files

grab annex content:

`cp -L file file-to`

copy a folder:

`cp -L -R -f folder folder-to`

make a file 'writable'
`chmod +w file`

----------------------------------
from Tomas(?) to order

Make your life easier and create an alias for datalad (if you put it into ~/.bashrc it will be executed every time you launch terminal)

```
alias dl="datalad"
```


First make a new empty directory:

```
mkdir PitchFT_raw
```

Then create a dl dataset inside:

```
dl create --description "raw data for PitchFT" -c text2git PitchFT_raw/

```

Then copy recursively all the data into the dl folder.  

```
cp -r my_raw_folder/* PitchFT_raw/
```

Navigate to the newly created dl folder and check the status.

```
cd PitchFT_raw

dl status
```

Commit the changes. This will make all the big files annexed (they become symbolic links)

```
dl save -m "adding some data"
```

Check that the data has been committed.

```
dl status
git log
```

<br>
---
<br>

Now go to GIN website, log it, create a new repo. Make sure you create it without ANY files (no README no licence none of that crap!).

Then copy the ssh url of the repo and add it in your terminal as a dl sibling.

```
dl siblings add -d . --name gin --url git@gin.g-node.org:/TomasLenc/PitchFT_raw.git
```

You will probably get a warning that dl doesn't know it the sibling can handle annex. We will fix this!

Now, push the data. Use either of these in arbtrary order. Do'nt give up.

```
datalad push --to gin --data anything

datalad push --to gin --force all
```

Done.
