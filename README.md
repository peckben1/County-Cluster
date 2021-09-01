README

Problem Statement: 
Regionalization of the United States is omnipresent and informs thinking and decision-making. Are regions as we know it purely cultural, or do they have any basis in statistics? 

Guide to files:
- code folder: There are two Jupyter notebooks - "Original" contains the code for the project as first completed in early 2020, while "Revisited" contains the updated code from summer 2021. 
- data folder: the raw data used for the project, as well as revisited.csv (the partially processed data) and processed2.csv (the final state of the data). processed.csv is an outdated version of the final output which is retained as a counterpart to the "Original" notebook, and workable.csv is similarly the partially processed data from "Original."

Methods:

The data was downloaded from USDA's Economic Research Service, which collected it from the various federal agencies that originated it. There were separate .csv files containing FIPS-coded county-level data on education, population, poverty, and unemployment. An additional shape file containing the most recent US county boundaries was obtained from data.gov. The files were read into pandas (through geopandas for the shape file) and joined on the FIPS codes. The data was cleaned (which eventually led to the complete removal of Alaska, Hawaii, and Puerto Rico) and a smaller number of features were selected, with a few features engineered to represent change over time. The data was scaled using StandardScaler and a Multiple Linear Regression was run predicting poverty, garnering an R2 score of 70% on the test data. Coefficients were dumped from the model to better examine correlations, and the model was used to generate predictions on the entire dataset and then calculate the error. The error was mapped to reveal geographic patterns in the model's performance. A second model was run using polynomial features (interactions only) and improved the R2 on test to 79%. KMeans was then run on the data to generate clusters, which were also mapped. The clusters were noncontiguous, as predicted, but showed significant regional patters. When cluster labels were introduced to the poly MLR, R2 on test data improved again to 82%. 

Conclusions:

Regionalization was apparent in the data and roughly aligned to familiar US regions, but with notable and consistent variations. More work is needed, especially to define contiguous regions and search over more potential parameters. I would especially like to bring in more demographic and economic data, for instance, the Economic Research Service's classifications of counties as retirement destinations. Another potential improvement would involve using commuter flow data from the Census Bureau to enhance regionalization. 

Maps and charts for this project are accessible through [a Tableau Public workbook tied to the output data](https://public.tableau.com/views/CountyClusterUpdate/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link)