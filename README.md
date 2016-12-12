# Amanda Wang
# ps239T-final-project

## Short Description
  The code in this project repo begins with a CSV file containing raw data from a Qualtrics survey, which participants from Amazon's Mechanical Turk completed. A total of 209 responses were collected. Broadly, the survey asked that participants think of a romantic couple they know well, and to name the individuals within that couple. From there, participants provided three sets of personality trait ratings, one set for each target: individual A, individual B, and the couple as a unit. Each set consisted of 27 traits that participants rated as either describing the target (0) or not describing the target (1). 

  This code first cleans the data. This involves, for example:  
1. filtering out participants who did not pass attention checks (an a priori criterion for exclusion)  
2. creating subject ID numbers  
3. subsetting the variables into separate dataframes containing key analysis variables and background/demographic variables  
4. renaming variables.

The next portion of this code involves further data-processing to transform the data into an analyzable format. Namely, the code contains user-defined functions for labeling the eight different types of trait rating combinations for each of the 27 traits. Then, it computes frequencies for the types of trait rating combinations that are of interest to the research project as a whole (a total of 3 "types", reduced from the original 8 possibilities). 

In the data analysis portion of this code, I employ statistical resampling procedures to obtain significance statistics regarding each frequency type. Specifically, the code performs bootstrap analyses that sample from the original data 10,000 times, and then creates 95% confidence intervals around the mean of each frequency type. The main goal here is to show that the frequencies of the rating type that we are interested in (i.e., emergence -- the rating type that corresponds to the couple being viewed differently from the individual couple members) is significantly non-zero. Furthermore, the data analysis code also performs various correlational and regression analyses of interest.

Finally, the last portion of this code produces univariate plots that visualize the frequencies of each rating type, as well as bivariate plots to visualize the corresponding regression analyses.

## Dependencies
The code in this project uses the following dependencies:  
1. R version 3.3.2  
2. RStudio version 0.99.903  
3. Various R packages, including:

  +  dplyr  
  +  tidyr  
  +  ggplot2 
  +  gridExtra
  +  stats 
  +  xlsx
  +  Hmisc

## Files
### Data  
1. **OthCoup_DragDrop_bothbatches.csv**:  Contains raw data exported from Qualtrics, in its 'legacy format' option. This includes all trait ratings, attention checks, data assurance questions, demographic variables, and suspicion probes. To protect participant confidentiality, and to remain in compliance with CPHS protocol, MTurk worker IDs and location information have been removed from the raw data file.
2. **OthCoup_DragDrop_culleddata.xlsx**: Cleaned and culled data spreadsheet obtained from the raw data (above). This contains the frequencies of trait ratings, classified by the unique types of combinations for the three targets in the study: OtherA, OtherB, and the Couple (as a single dyad).

###Code
1. 01_CleanData.Rmd:  Loads the raw data from a CSV file that was downloaded from the Qualtrics survey site. Cleans the data to transform it into analyzable format. Exports key variables to the file OthCoup_DragDrop_culleddata.xlsx.
2. 02_AnalyzeData.Rmd: Conducts exploratory, descriptive, regression, and bootstrap analyses of the data.
3. 03_VisualizeData.Rmd: Produces univariate and bivariate plots of the analyses performed in the 02 file. Also exports a PDF of the plots that are key to addressing the project hypotheses.

###Results  
1. OthCoup_DragDrop_results.xlsx: Correlation table showing relationships among key trait rating variables and various demographic and relationship-background variables. The third sheet contains means for three rating combination types, and 95% confidence intervals from bootstrap analyses.  
2. plots.pdf: Contains two graphs: First is an overlapping histogram comparing the frequencies of ratings for three different types of trait rating combinations. Second is a graph of the 95% confidence intervals around the mean of each type of rating combination, obtained from bootstrap analyses.
