# Snippet Terminal code

check this https://medium.com/macoclock/9-mac-homebrew-tools-youve-never-thought-you-needed-96ff07291592

``` bash
# monitor cpu usage and ongoing command
#  inputs while running:
#  - `o` order by eg `cpu`
#  - `s` refresh interval eg `5` for every 4 seconds
top

# ADVANCED monitor cpu usage and ongoing command, it can be used through the mouse
htop

# list files and get info about: size; permission; etc
ls -lrths

#change file and folder permission recursively
chmod -R 777 /path/to/directory

# list the hard drives and the size
df -h

# directories size
# get the size of the folders without recursion and the time of last modification
du -h --max-depth=1 --time
# on mac --max-depth does not work
du -hd1 
# get the size of a folder recursively
du -h /directory-name

# tree command for folder structure with depth  limit eg 3
tree -d -L 3

# tree command that sort of print how many files per folder
tree --filelimit=15

# remove not empty directories
rm -rf /directory-name

# list pip packages installed
pip list

# check internet speed 
networkQuality

# file copying preserving subfolder structure
cd  path/where/tree-to-copy/starts
cp -v --parents */*/*/*pattern*.nii destiantion

```

## ffmpreg video compression
```bash
ffmpeg \
    -i input.mov \
    -vcodec libx265 \
    -crf 22 \
    -preset slow \
    output.mp4
```

### ffmpeg video trimming
```bash
ffmpeg -i part_2_talk_2_talk_3_compressed.mp4 -ss 00:41:05 -to 01:13:32 -c copy part_3_talk_3_compressed.mp4
```

### .bash_profile

```bash_profile
alias matlab='open /Applications/MATLAB_R2017b.app'
alias rstudio='open /Applications/RStudio.app'
alias matlabter='/Applications/MATLAB_R2017b.app/bin/matlab -nodesktop -nosplash $*'

export PATH=$PATH:/Users/barilari/Library/Python/3.7/bin
export FREESURFER_HOME=/Applications/freesurfer
export FS_LICENSE=$FREESURFER_HOME/license.txt

# FSL Setup
FSLDIR=/usr/local/fsl
PATH=${FSLDIR}/bin:${PATH}
export FSLDIR PATH
. ${FSLDIR}/etc/fslconf/fsl.sh

# GitHub patch for autocomplition
if [ -f ~/.git-completion.bash ]; then
  . ~/.git-completion.bash
fi
```
