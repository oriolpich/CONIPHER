# CONIPHER

## CONIPHER phylogenetic tree building 
### R package

This is the official github repository for the R package to perform tumour phylogenetic tree building using CONIPHER. For details on how to run mutation clustering and phylogenetic tree builing consecutively with one wrapper script, please refer to the github repository [CONIPHER-wrapper](https://github.com/McGranahanLab/CONIPHER-wrapper). For full details of all the inputs into CONIPHER clustering and tree building, refer to our protocol (https://doi.org/10.21203/rs.3.pex-2158/v1).

#### Software
The current implementation of CONIPHER tree building is written in `R=3.6.1` and is distributed as an R package.

---
### Quick start

To get start quickly, you can install CONIPHER tree building and perform phylogenetic tree reconstruction on the example data provided using the following instructions.

#### CONIPHER installation and run instructions
To install and be able to run CONIPHER tree building, you must have R package `devtools >= 2.4.1` installed. 

**Step 1.** Start R and install the 'CONIPHER' R package from this github repository using the following command:
```
devtools::install_github("McGranahanLab/CONIPHER")
library(CONIPHER)
```

**Step 2.** Specify your input data. To run CONIPHER treebuilding successfully, we require an input table, a sample and tumour case prefix and a desired output directory. For example:
```
input_table <- read.delim2('data/input_table.tsv')
prefix <- 'CRUK'
out_dir <- 'data/results'
```

**Step 3.** Run data preprocessing:
```
input_list <- treebuilding_preprocess(input_table, prefix, out_dir)
```

**Step 4.** Run the main tree building function:
```
tree_output_list <- treebuilding_run(input_list)
```


**Step 5.** Plot tree output, if desired:
```
treebuilding_plot(tree_output_list)
```
--- 

### Anticipated results

The tree building will return 3 output files (examples are in data/results):
- <CASE_ID>.tree.RDS: an R list object containing tree building output information
- pytree_and_bar.pdf: a plot of the default reconstructed tree and barplot
- pytree_multipletrees.pdf: a plot showing all possible alternative phylogenetic trees found by CONIPHER



