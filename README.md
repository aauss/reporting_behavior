# Understanding COVID-19 reporting behavior to support political decision-making: An analysis of COVID-19 data reported to the world health organization 

## Install

If you want to run the code yourself and you have conda, just run `conda env create -f env.yml` and you are good to go.

### Packages

For the analyses, I used matplotlib and altair for plotting. For data processing, I used pandas, for data scraping requests, and for data modelling scikit-learn and ts-learn. My analyses are conducted and visible in the reporting_behavior.ipynb for which I used JupyterLab.

## Motivation

WHO provides data on COVID-19 based on all its partner countries. This makes it intriguing to just compare different countries. However, reporting quality might heavily vary between countries which makes comparison between countries difficult.

## Files

This repo contains the main findings as plots in the figures folder. The env.yml contains information which packages need to be installed to run the notebook, and the notebook itself which contains all the analysis on reporting quality based on the scraped data from [WHO](https://covid19.who.int/table).

## Content

I analyzed the data based on two different aspects: whether countries made a report stratified by weekday (binary reporting rate) and how the sum of reported cases per week are distributed per weekday (relative reporting behavior). Also, I  developed a metric - simply named reporting score - to analyze the expected reporting frequency based on the number of reported cases. Countries that report frequently although they don't have many cases receive a positive score and countries that don't report frequently and have a high incidence receive a negative score. Finally, I applied clustering to find salient patterns in binary reporting rates and relative reporting behavior. Since the size of a country may negatively influences  scores, I offer an imputation approach to counter balance alleged low reporting that may very well be due to no COVID-19 infections happening in these small (and mostly isolated) countries. 

Exact results and approach can be found the in the notebook.

## Acknowledgements

I thank WHO for making their data publicly available.
