###########################################
#      SF6-MBW GAMLSS reference values    #
###########################################

GAMLSS models for predicting SF6-MBW reference values as described in 

  "Multiple breath washout (MBW) testing using sulfur hexafluoride: reference values and influence of anthropometric parameters"
  Trinkmann F, Maros M, Roth K, Hermanns A, Schäfer J, Gawlitza J, Saur J, Akin I, Borggrefe M, Herth FJF, Ganslandt T.
  Thorax. 2021 Feb 16:thoraxjnl-2020-214717. doi: 10.1136/thoraxjnl-2020-214717. Epub ahead of print. PMID: 33593931.

Models are provided as .rds files for LCI, LCI5, Sacin and Scond. For technical reasons and data protection, these were created based 
on simulated data representative of the original values.

# Contact
#######################

  Please contact for any questions and support:

  Dr. Frederik Trinkmann, MD
  Thoraxklinik at Heidelberg University
  Röntgenstraße 1
  69126 Heidelberg / Germany

  frederik.trinkmann@med.uni-heidelberg.de


# Example (R-Markdown)
#######################

  R-Version 3.5.1
  GAMLSS version 5.1-4

  Calculate predicted LCI for specific age (56 years).
  Calculate z-score for for specific age (56 years) and specific LCI (12.31)

  ```{r}
   library(gamlss)

   #import data
    imported_file <- readRDS("lci_gamlss.rds")   
    imported_data <- imported_file$data

   #predict LLN, mean and ULN for specific age
    centiles.pred(imported_file$model, xname="age", xvalues=c(56), cent=c(5,50,95))

   #predict z-score for specific age and specific LCI
    centiles.pred(imported_file$model, xname="age", xvalues=c(56), yval=c(12.31), type="z-scores")

```
