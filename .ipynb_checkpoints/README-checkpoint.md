README

Problem Statement: 
Regionalization of the United States is omnipresent and informs thinking and decision-making. Are regions as we know it purely cultural, or do they have any basis in statistics? 

Guide to files:
- code folder: All relevant code is actually in the Jupyter Notebook called "EDA" due to issues with reading data back from csv files
- data folder: the raw data used for the project, as well as "workable" (the partially processed data) and "processed" (the final state of the data)

Methods:

The data was downloaded from USDA's Economic Research Service, which collected it from the various federal agencies that originated it. There were separate .csv files containing FIPS-coded county-level data on education, population, poverty, and unemployment. An additional shape file containing the most recent US county boundaries was obtained from data.gov. The files were read into pandas (through geopandas for the shape file) and joined on the FIPS codes. The data was cleaned (which eventually led to the complete removal of Alaska, Hawaii, and Puerto Rico) and a smaller number of features were selected, with a few features engineered to represent change over time. The data was scaled using StandardScaler and a Multiple Linear Regression was run predicting poverty, garnering an R2 score of 72% on the test data. Coefficients were dumped from the model to better examine correlations, and the model was used to generate predictions on the entire dataset and then calculate the error. The error was mapped to reveal geographic patterns in the model's performance. KMeans was then run on the data to generate clusters, which were also mapped. The clusters were noncontiguous, as predicted, and showed only weak regional patters. The region library was used to attempt contiguous clustering, but this could not be completed with the present hardware. 

Conclusions:

Regionalization was apparent in the data and roughly aligned to familiar US regions, but with notable and consistent variations. Regional discrepancy from the model was noted, indicating some other factors in play. More work is needed, especially to generate contiguous clusters and search over more potential parameters. I would especially like to bring in more demographic and economic data, for instance, the Economic Research Service's classifications of counties as retirement destinations. 