# Snippet Terminal code

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

# directories size
# get the size of the folders without recursion and the time of last modification
du -h --max-depth=1 --time
# get the size of a folder recursively
du -h folder-name

# list pip packages installed
pip list
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
