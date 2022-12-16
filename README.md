# Understanding COVID-19 reporting behavior to support political decision-making: A retrospective cross-sectional study of COVID-19 data reported to the World Health Organization

## Install

If you want to run the code yourself and you have conda, just run `conda env create -f env.yml` and you are good to go. If you do not have conda, you can read `env.yml` to find out which Python version and which external packages were used to run the experiments found in the respective paper.

### Packages

For plotting, we used matplotlib and altair. For data processing, we used pandas, for data scraping requests, and for data modelling scikit-learn and ts-learn. Our analyses are conducted and documented in the reporting_behavior.ipynb for which we used Jupyter Lab. You can either use Jupyter Lab, Jupyter Notebook, Visual Studio Code with a compatible plug-in, or any other software that allows you to run .ipynb files.

## Motivation

WHO provides data on COVID-19 based on all its partner countries. This makes it intriguing to just compare different countries. However, reporting quality might heavily vary between countries which makes comparison between countries difficult. We looked into quantifying the reliability of reporting and used clustering to identity countries with highly unusual reporting patterns.

## Files

This repo contains the main findings as plots in the figures folder. The env.yml contains information which packages need to be installed to run the notebook, and the notebook itself which contains all the analysis on reporting quality based on the scraped data from [WHO](https://covid19.who.int/table).

### WHO COVID-19 Data

This data set is mainly consisting of data from [WHO](https://covid19.who.int/table) on official COVId-19 reports. It is a CSV table with information of confirmed COVID-19 infections and COVID-19 related deaths for all UN countries and covers data from January 2020 until June 2021. To add the full country names to the two-letter abbreviated country names natively provided by WHO, this table has been extended by another [data set](https://raw.githubusercontent.com/lukes/ISO-3166-Countries-with-Regional-Codes/master/all/all.csv) that maps country names to their two-letter abbreviation. This data set is named `data_20210614.csv`.

This data set was used to explore reporting behavior, define and apply self-developed metrics, and perform clustering on timeseries in the data set to find irregular reporting.

### Description of the Data and file structure

The file named `data_20210614.csv` and stored in the `data` folder contains the data used for this work. Each column is complete except for the `population` column. It contains some missing values indicated with a `NULL`. Values are missing when there were no reported COVID-19 cases to calculate the population from the columns `WkCasePop`and `Cases Last 7 Days`. In the following table, you can see a description for each variable in the data set:

| Field name                  | Type    | Description                                                                                                                                                      |
| --------------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| day                         | String  | Date of observations using yyyy-mm-dd                                                                                                                            |
| ISO2                        | String  | Country, territory, area name abbreviated according to ISO 3166 ALPHA-2 from the WHO data set                                                                    |
| Region                      | String  | WHO Region                                                                                                                                                       |
| Cumulative Confirmed        | Integer | Cumulative confirmed cases reported to WHO to date.                                                                                                              |
| Cases Per Hundred Thousand  | Decimal | Cumulative confirmed cases reported to WHO to date per 100,000 population.                                                                                       |
| Cases Last 7 Days           | Integer | New confirmed cases reported in the last 7 days. Calculated by subtracting previous cumulative case count (8 days prior) from current cumulative cases count.    |
| WkCasePop                   | Decimal | New confirmed cases reported in the last 7 days per 100,000 population.                                                                                          |
| Confirmed                   | Integer | New confirmed cases reported in the last 24 hours. Calculated by subtracting previous cumulative case count from current cumulative cases count.                 |
| Cumulative Deaths           | Integer | Cumulative confirmed deaths reported to WHO to date.                                                                                                             |
| Deaths Per Hundred Thousand | Decimal | Cumulative confirmed deaths reported to WHO to date per 100,000 population.                                                                                      |
| Deaths Last 7 Days          | Integer | New confirmed deaths reported in the last 7 days. Calculated by subtracting previous cumulative death count (8 days prior) from current cumulative deaths count. |
| WkDeathPop                  | Decimal | New confirmed deaths reported in the last 7 days per 100,000 population.                                                                                         |
| Deaths                      | Integer | New confirmed deaths reported in the last 24 hours. Calculated by subtracting previous cumulative death count from current cumulative deaths count.              |
| name                        | String  | Country, territory, area name                                                                                                                                    |
| alpha-2                     | String  | Country ,territory, area name abbreviated according to ISO 3166 ALPHA-2 from the publicly available GitHub repository of lukes                                   |
| population                  | Float   | Population calculated using the WkCasePop and Cases Last 7 Days. If  columns                                                                                          |

### Sharing/access Information

The WHO COVID-19 data was taken from <https://covid19.who.int/table>
The mapping from the two-letter country abbreviation to its full name was taken from <https://raw.githubusercontent.com/lukes/ISO-3166-Countries-with-Regional-Codes/master/all/all.csv>

## Content

We analyzed the data based on two different aspects: whether countries made a report stratified by weekday (binary reporting rate) and how the sum of reported cases per week are distributed per weekday (relative reporting behavior). Also, we developed a metric - simply named reporting score - to analyze the expected reporting frequency based on the number of reported cases. Countries that report frequently although they don't have many cases receive a positive score and countries that don't report frequently and have a high incidence receive a negative score. Finally, we applied clustering to find salient patterns in binary reporting rates and relative reporting behavior. Since the size of a country may negatively influences scores, we offer an imputation approach to counter balance alleged low reporting that may very well be due to no COVID-19 infections happening in these small (and mostly isolated) countries.

Exact results and approach can be found the in the jupyter notebook.

## Acknowledgements

We thank WHO for making their data publicly available.
