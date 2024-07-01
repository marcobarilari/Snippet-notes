# bash

`chmod u+x YourScriptFileName.sh`

## declare an array variable
declare -a database=("one" "two" "three")

# get length of an array
arraydatabaselength=${#array[@]}

database=( 'Item1' 'Item2' 'Item3' )

for databaseName in ${database[*]} ; 
do
  echo $databaseName
done 

## Parallel computing with limited n of cpu cores

!!! To add