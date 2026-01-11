# NYC-Gentrification-2017
This project explores gentrification in New York City as a capital strategy, its effects on low income &amp; long-term residents, and community-based resistance strategies as an effective buffer. It contains all files used in the analysis of neighborhood change & gentrification inflows across New York City's Sub-borough Areas (SBAs) in 2017.

Data from the New York City Housing and Vacancy Survey (NYCHVS), NYU Furman Center, &amp; individual published ICPSR projects are cleaned &amp; merged into a final SBA-level dataset (SBA.csv). Merged with geographic identfifies, SBA_GEO.geojson is used to produce geographical distributions of key variables. Analysis occurs in two stages (1) a main set of 3 specified OLS models at the SBA-level, and (2) a household-level logit subanalysis of factors that have a theorized effect on the liklelihod of becoming displaced. 

- Data Dictionary.pdf: Contains a comprehensive dictionary of all variables in final datasets.


# Data Processing & Cleaning

- Furman.ipynb: Processes neighborhood indicator data from NYU Furman Center. Cleans and filters data to SBA-level, corrects SBA numerical codes using a custom crosswalk, and creates a finalized dataset along with a separate panel of key pre/post variables for analysis.
  
- NYCHVS.ipynb: Cleans and processes New York City Housing & Vacancy Survey data from three files. Identifies and renames necessary columns, constructs the primary dependent variable (gentrification), and creates aggregated versions for recent movers (5-year and 1-year). Outputs both SBA-level data and a household-level subset for subanalysis.
  
- ICPSR.ipynb: Cleans the 12 ICPSR datasets containing various SBA-level characteristics. Processes each source individually to produce cleaned data files for merging and analysis.
  
- Crosswalk.ipynb: Constructs a crosswalk file to correctly map Sub-Borough Area (SBA) codes to their corresponding Public Use Microdata Area (PUMA) codes, using 2010 Census tract FIPS codes.


# Merging & Geospatial Mapping

- Merged.ipynb: Merges all cleaned data sources (NYCHVS, Furman, ICPSR) into the final SBA dataset on the SBA key. Formats columns and creates a dictionary mapping each SBA to its neighbors, and exports the final dataset used for all primary statistical analysis.
  
- Geodata.ipynb: Prepares geospatial data for mapping. Imports a PUMA-level shapefile and uses the SBA-PUMA crosswalk to assign the correct geometry to each SBA, exporting the final SBA_GEO GeoDataFrame.
  
- Geo_Visuals.ipynb: Generates maps of spatial distribution visualizations for key variables across NYC's Sub-Borough Areas using SBA_GEO GeoJSON data.


# Statistical Analysis

- Regressions.Rmd: Contains the primary econometric analysis. Documents variable summaries, correlation matrices, and performs OLS regressions. Includes robustness checks, tests for heteroskedasticity and multicollinearity, F-tests, and produces regression tables via stargazer.
  
- Regressions.pdf: Knitted PDF output of the main analysis from Regressions.Rmd.
  
- Subanalysis.ipynb: Prepares data for household-level analysis. Loads the NYCHVS household subset, constructs markers for displacement risk and gentrifier status, and creates demographic indicators (race, immigrant status) for logistic regression.
  
- Subanalysis.Rmd: Contains the household-level subanalysis. Provides a correlation heatmap and runs a series of logistic regressions to examine determinants of displacement/gentrification at the individual household level


# Outputs & Results

- table1.html, table2.html, table3.html: Finalized stargazer HTML output tables for the main analysis and subanalysis regressions.

