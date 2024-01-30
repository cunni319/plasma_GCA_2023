# plasma_GCA_2023
Analysis of plasma proteins in Giant Cell Arteritis (GCA) patients compared with healthy controls.
===================================================

This repository includes Jupyter lab notebooks to run for the analysis for this project. 
The input data is included in the repository; no editing is required to run the scripts. 
Each script has local data that is read in, and all output for the figures is automatically 
put into the corresponding output directory.

The scripts included are the following:

>quantile_normalization.ipynb

This script takes the raw RFU data from SomaLogic, and quantile normalizes the samples.
A box plot of all samples is provided at the end of the script to illustrate that all samples
have the same distribution and median after quantile normalization. The quantile normalized 
data is saved in the data directory for all downstream analysis.

>PCA.ipynb

This script takes the quantile normalized data and makes a PCA plot in R. Additionally, this
script makes box plots of the distribution of PC1 and PC2 values for all three study groups
(Active GCA, Inactive GCA, and Healthy controls). A Mann–Whitney *U* test was used to compare 
the PC1 and PC2 distributions between all three study groups, the *P*-values are provided and
denoted between each group.

>linear_modeling_between_PC1_and_demographic_variables.ipynb

This script uses the quantile normalized data to make do a PCA analysis. The PC1 values for all
three study groups are saved for linear modeling. Linear regression models were constructed between
clinical and demographic variables for all three study groups. This includes: Study group, age,
prednisone use, BMI, aspirin use, sex, PGA, Smoking status, and CRP. Each clinical and demographic
variable had an individual linear regression model constructed. The *P*-value and the R<sup>2</sup> for the 
variable of interest are saved to make a lollipop plot with the lenth of the line representing the linear
regression model *P*-value and the size of the point representing the R<sup>2</sup> value.

>linear_modeling_active_and_controls.ipynb

This script uses the quantile normalized data as well as the clinical and demographic data to build linear
regression models between Active GCA patients and Healthy controls. Marginal linear regression models were
run on six clinical and demographic variables between Active GCA and Healthy controls. Variables with linear
regression model *P*-values < 0.05 were identified as significant confounders and included in the full multiple linear 
regression models. In the full multiple linear regression models, the *P*-value from the study group variable was used 
to identify differentially abundant proteins between Active GCA and Healthy controls. A threshold of *P* < 0.01 
was applied to all plasma proteins for significance.





The Physician's Global Assessment (PGA) is a commonly used GCA measurement for disease severity in patients.

# Installation

There are a few R libraries that need to be installed to run these scripts.
They are:

```
library(dplyr)
library(reshape2)
library(ggpubr)
library(Hmisc)
library(preprocessCore)
library(effsize)
library(pheatmap)
library(FactoMineR)
library(stats)
library(factoextra)
library(ggfortify)
```

