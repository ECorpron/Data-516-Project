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
  For the entire project our goal was to keep it human centered. To do so we focused on easily understood and explainable models, data that protected people’s privacy, and our goal with the research was to improve future responses to pandemics.
  Our research question came in two parts. The first was what was the impact of masking mandates on Covid deaths in El Paso County. The second was the number of Covid related deaths and whether a masking mandate was in effect impacted the number of offenses that occured in El Paso County. Our hypothesis for the first part was that there would be a change point around when masking mandates are enacted and removed, and our null hypothesis for the second part is that there is no relation between covid deaths and masking mandates.
	For the first part we found that change points appeared to appear regardless of when the masking mandates situation changed. However we feel that our model makes a number of untrue assumptions that make possible conclusions here unreliable. On top of that our model for the second part violated several key assumptions. Unfortunately this makes possible conclusions from the model unreliable as well.

For a more complete write up, please look at Data 512 Final Paper.pdf.

## Possible Problems with Analysis
  There are a number of limitations with our research. It only applies to El Paso County from the dates of January 22, 2020 to October 15, 2021. The change point detection research implicitly assumes that the infection rates for covid are constant, and that all masking mandates are the same. Neither of these are true; different Covid variants behave differently and there are a wide range of masking mandates with a wide range of requirements. The multiple linear regression model has a number of key assumptions not held, making the results not reliable. On top of that, the model has a very low R-squared value, meaning it does a poor job actually modeling the data. For all of these reasons our results and conclusions that can be drawn from them are extremely limited and unreliable.
