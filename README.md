# Final Project, Data science Nanodegree

## Install

If you want to run the code yourself and you have conda, just run `conda env create -f env.yml` and you are good to go.

### Packages

For the analyses, I used matplotlib and altair for plotting. For data processing, I used pandas, for data scraping requests, and for data modelling scikit-learn and ts-learn. My analyses are shown as .ipynb for which I used JupyterLab.

## Motivation

WHO provides data on COVID-19 based on all its patner countries. This makes it intriguing to just compare different countries. However, reporting quality might heavily vary between countries which makes comparison between countries difficult.

## Files

This repo contains the main findings as plots in the figures folder. The env.yml contains information which packages need to be installed to run the notebook, and the notebook itself which contains all the analysis on reporting quality based on the scraped data from [WHO](https://covid19.who.int/table).

## Content

I analyzed the data based on two different aspects: whether countries made a report stratified by weekday (binary reporting behavior) and how the sum of reported cases per week are distributed per weekday (relative reporting behavior). Also, I also developed a metric to analyze the expected reporting frequency based on the number of reported cases. Countries that report frequently although they don't have many cases receive a positve score and countries that don't report frequently and have a high incidence receive a negative score. Finally, I applied clustering to find salient patterns in reporting. This yields good results for the relative reporting behavior and mixed results for the binary reporting behavior. The latter seems to exhibit a bias towards large countries that seem to more frequently make reports than smaller countries (measured by population).

Exact results and approach can be found the in the notebook.

## Acknowledgements

I thank WHO for making their data publically available.
