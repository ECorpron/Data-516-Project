# Data-516-Project

## Goal
There are two goals for this project. The first is to attempt and find how big of an impact masking and masking mandates had on the number of Covid related deaths. The second is to see if I can predict the number of crimes committed using Covid death rates and masking mandate data. Both of these parts will be focused in El Paso, Colorado.

## The Data
The data is pulled from four locations.
* Covid death data is from John Hopkins: https://www.kaggle.com/datasets/antgoldbloom/covid19-data-from-john-hopkins-university
under the Creative Commons license (https://creativecommons.org/licenses/by/4.0/)
* Mask mandate data is from the CDC: https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i
(Unspecified License)
* Mask mandate compliance data is from the New York Times: https://github.com/nytimes/covid-19-data/tree/master/mask-use
Link to the New York Times license (https://github.com/nytimes/covid-19-data/blob/master/LICENSE)
* El Paso Crime Data is from the Colorado Crime Statistics: https://coloradocrimestats.state.co.us/tops
(Unspecified License)

## Structure of the Data
### Covid Death Data
* Province_State: The state
* Admin2: The county
* FIPS: Uniquely identifying code for the county
* Rows 13 On: Column header is the date in "yyyy-mm-dd" form, with the row value being the cumulative total of deaths
File name: RAW_us_deaths.csv

### Mask Mandate Compliance Data
* COUNTYFP: The county FIPS code
* NEVER: Percent of people in the county who never follow mandates
* RARELY: Percent of people who rarely follow mandates
* SOMETIMES: Percent of people who sometimes follow mandates
* FREQUENTLY: Percent of people who frequently follow mandates
* ALWAYS: Percent of people who always follow mandates
Not used in the analysis code, and only contains a single row for the El Paso county.
File name: mask-use-by-county.csv

### Mask Mandate Data
* State_Tribe_Territory: The state code (Colorado is 'CO')
* County_Name: The county name, includes 'county' (El Paso is 'El Paso County')
* date: The date, in the form "mm/dd/yyyy"
* Face_Masks_Required_in_Public: If there was a mandate in effect. Is either "Yes", "No" or NaN
File name: U.S._State_and_Territorial_Public_Mask_Mandates_From_April_10__2020_through_August_15__2021_by_County_by_Day.csv

### El Paso Crime Data
* "date": The date, in the form "mon day, yyyy"
* "Number of Incidents": The number of all offenses that occured on that day.
Raw data: El Paso Crimes By Day for 2020 and 2021.csv
Used file: edited El Paso Crimes By Day for 2020 and 2021.csv
Removed filler rows at the top of the file.

## Code Instructions
First unzip U.S._State_and_Territorial_Public_Mask_Mandates_From_April_10__2020_through_August_15__2021_by_County_by_Day.zip, keep in the data file unnested.

First run Project Part 1.ipynb. Note that this uses the ruptures package for using the PELT method. Ruptures is for up to Python 3.9, and as such the script doesn't work for newer python versions currently. This creates an intermediary file cleanedElPasoData.csv that is the cleaned covid death data and masking mandate data. The figure with change points is created in here.

Next run El Paso Crime Data Cleaning.ipynb. This cleans the crime data, and combines it into one dataframe. This is saved into the intermediary file ElPasoCovidAndCrimeData.csv.

Lastly run Covid and Crime Analysis.ipynb. This creates a number of analysis figures and results for a multiple linear regression model attempting to predict crime with Covid deaths and masking mandates.

## Folders
### Figures
This folder contains figures I find interesting. Currently all figures are made within the Project Part 1 file.

### Write-ups
Contains reports written for the project

### data
contains the raw data and intermediary files used in the analysis.

## Research Implications
It is currently still very early on to make any hard statements, but the figures I have made so far seem to imply that masking mandates in El Paso had little to no effect on the rates of death in El Paso.

## Possible Problems with Analysis
There are a number of potential problems. The major one is that we treat all mask mandates as the same, even though who was required to where a mask and where they were required changed from mandate to mandate. We have not done the necessary research yet in to the mandates enacted in El Paso.
