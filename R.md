# R snippet code

```R
# set script folder as working dir
setwd(dirname(rstudioapi::getActiveDocumentContext()$path))

# Load and install (if missing) the recquired packages
list.of.packages <- c("dplyr", "ggplot2", "knitr", "reshape2")
new.packages <- list.of.packages[!(list.of.packages %in% installed.packages()[,"Package"])]
if(length(new.packages)) install.packages(new.packages)

lapply(list.of.packages, library, character.only = TRUE)
```
