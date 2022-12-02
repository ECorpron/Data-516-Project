# Data-516-Project

## Goal
The Goal of this project is to do some analyzation of Covid data. My project is to attempt and find how big of an impact masking and masking mandates had on the number of Covid related deaths in El Paso, Colorado.

## The Data
The data is pulled from three locations.
* Covid death data is from John Hopkins: https://www.kaggle.com/datasets/antgoldbloom/covid19-data-from-john-hopkins-university
under the Creative Commons license (https://creativecommons.org/licenses/by/4.0/)
* Mask mandate data is from the CDC: https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i
(Unspecified License)
* Mask mandate compliance data is from the New York Times: https://github.com/nytimes/covid-19-data/tree/master/mask-use
Link to the New York Times license (https://github.com/nytimes/covid-19-data/blob/master/LICENSE)

## Structure of the Data
### Covid Death Data
* Province_State: The state
* Admin2: The county
* FIPS: Uniquely identifying code for the county
* Rows 13 On: Column header is the date in "yyyy-mm-dd" form, with the row value being the cumulative total of deaths

## Mask Mandate Compliance Data
* COUNTYFP: The county FIPS code
* NEVER: Percent of people in the county who never follow mandates
* RARELY: Percent of people who rarely follow mandates
* SOMETIMES: Percent of people who sometimes follow mandates
* FREQUENTLY: Percent of people who frequently follow mandates
* ALWAYS: Percent of people who always follow mandates
Not currenty used in the analysis code, and only contains a single row for the El Paso county.

## Mask Mandate Data
* State_Tribe_Territory: The state code (Colorado is 'CO')
* County_Name: The county name, includes 'county' (El Paso is 'El Paso County')
* date: The date for the date, in the form "mm/dd/yyyy"
* Face_Masks_Required_in_Public: If there was a mandate in effect. Is either "Yes", "No" or NaN

## Code Instructions
To run the code and get the outputs found in the repository run the Project Part 1 notebook file. Currently all outputs are made within the notebook.

## Folders
### Figures
This folder contains figures I find interesting. Currently all figures are made within the Project Part 1 file.

### Write-ups
Contains reports written for the project

### data
contains the raw data used in the analysis. I currently don't save any intermediate data files.

## Research Implications
It is currently still very early on to make any hard statements, but the figures I have made so far seem to imply that masking mandates in El Paso had little to no effect on the rates of death in El Paso.

## Possible Problems with Analysis
There are a number of potential problems. The major one is that we treat all mask mandates as the same, even though who was required to where a mask and where they were required changed from mandate to mandate. We have not done the necessary research yet in to the mandates enacted in El Paso.
