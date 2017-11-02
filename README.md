# Investigating Bias in Wikipedia Article Counts by Country

This project was performed for **Assignment 2: Bias in Data** in my Human-Centered Data Science course (DATA 512, University of Washington, Autumn 2017). The assignment description can be found here (as of November 2017): https://wiki.communitydata.cc/HCDS_(Fall_2017)/Assignments#A2:_Bias_in_data

## Overview

For this assignment I investigate bias in English Wikipedia politician coverage by country. I look at two different metrics regarding the proportion of articles about politicians by country:

* **Total Coverage:** proportion of articles compared to the country's population
* **High-Quality Coverage:** proportion of high-quality articles compared to the total number of articles for the country

I report on the extremes of both of these metrics, i.e. countries with the highest and lowest proportions of each metric. The full analysis and results, as well as a short reflection on the task, can be found in the Jupyter Notebook ([link](hcds-a2-bias.ipynb)).

### Results

TODO: Consider adding summary tables/plots here...?

### Reflection

TODO: Consider adding reflection here, if you don't want to bury it in the notebook. Might make more sense here.

## Data Source and Licensing

Data for this project was obtained from three different sources, as described below. License information for each source is also described below.

### Population data

Population data for 210 countries was made available by the Population Reference Bureau (PRB). The specific dataset used in this analysis represents world populations by country as of Mid-2015. It is sourced from the *2015 World Population Data Sheet*, which is described in detail here:  
http://www.prb.org/Publications/Datasheets/2015/2015-world-population-data-sheet.aspx

The actual data used in this analysis can be found here:  
http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14  

The raw data includes six columns:

* **Location**
* Location Type
* TimeFrame
* Data Type
* **Data**
* Footnotes

For this analysis I only use data from the columns bolded above (i.e. `Location` and `Data`).

The population data is copyrighted by PRB and therefore is not included within this repository. See the [Reproducibility](#reproducibility) section below for specifics on how to retrieve this data if you wish to duplicate or expand upon the analysis in this repository.

### Page Data

You'll find the wikipedia politician article dataset on Figshare here:  
https://figshare.com/articles/Untitled_Item/5513449


### Page Ratings (Wikipedia ORES)



Alyssa [1:00 PM]  
I am having trouble finding licensing or terms of use information for ORES. Can we assume it has the same licensing as Wikimedia pages? https://creativecommons.org/licenses/by-sa/3.0/

ironholds [1:09 PM]  
@Alyssa good assumption to work with! Personally I would make the argument that it shouldn’t have copyright at all - but CC-BY-SA is otherwise a solid way to go.

Also from Oliver: "I’d explicitly Cc-0 it"



## Output Data

The cleaned data table can be found in `population_and_article_quality_data.csv` ([link](data/population_and_article_quality_data.csv)). It consists of country populations and article ratings by country monthly. The schema is as follows:

| Column        		| Value 					| Type		|
|-----------------------|---------------------------|-----------|
| **country**			| country name 				| string 	|
| **population**		| country population		| integer	|
| **article_name**		| article name (str)		| string	|
| **revision_id**		| article revision ID 		| integer	|
| **article_quality**	| article quality			| string	|

Data notes:

* Article quality is a string but may only consist of one of several different ratings.
* Two rev_id's returned invalid results in ORES....list them here and mention how they were handled.
* Talk about data merge and how some countries fell off the map...


## Reproducibility

This work is intended to be fully reproducible. This means that any user should be able to run my code and produce the exact same result as presented here.

To test this out, simply `git clone` this repository, and open and run `hcds-a2-bias.ipynb`. The results should be exactly reproduced.

TODO: talk about PRB data and how it's not included in repo, but can be downloaded, or the code will pull it straight from the website.

-----

However, note that the code is configured to refer to local data files if they exist. This was done for two reasons:

* to create checkpoints (with reproducibility in mind)
* to prevent redundant API calls

To truly duplicate this analysis from scratch, delete all the data in `/data` and `/data/raw`, and then run the notebook. The data will be re-retrieved from Wikimedia, and new .csv files will be written. The final visualization is always regenerated regardless of whether new or existing source data is used.

If differences are found in results between code run with a clean slate vs. otherwise, they should be able to be traced to differences in the source data itself, or in modules upon which the code was written. Hopefully the "data checkpoints" will help with troubleshooting if this is ever found to be the case.







------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------

## NOTES

Alyssa [1:00 PM]  
I am having trouble finding licensing or terms of use information for ORES. Can we assume it has the same licensing as Wikimedia pages? https://creativecommons.org/licenses/by-sa/3.0/

ironholds [1:09 PM]  
@Alyssa good assumption to work with! Personally I would make the argument that it shouldn’t have copyright at all - but CC-BY-SA is otherwise a solid way to go.

-------

Libby Montague [8:31 PM]  
I'm not able to find the licensing information for the ORES or the Population Reference Bureau data. It looks like above Alyssa asked about the ORES data and said that we could make an assumption about the license for the data. (1) Can we use the data is no license is provided? (2) Should we mention that no license was provided? (3) Am I missing the license of the Population Reference Bureau?

ironholds [8:42 PM]  
In sequence: (1) I’d explicitly Cc-0 it, (2) if you’d like! In fact you can ask the lead developer on Thursday! (3) it doesn’t in fact have one - the data is copyrighted and shouldn’t be incorporated into the repo. Do the instructions say it should be? :/. But either way I’d just note that it’s copyrighted by the PRB

--------

Mike Browne [3:53 PM]  
Regarding the visualization:  10 lowest-ranked countries in terms of number of GA and FA quality articles as a proportion of all articles.  I'm getting 39 countries with zero GA/FA quality articles.  How would you suggest ranking these 39 countries?  By total number of articles?  In other words choose the 10 countries which have the highest total number of articles.

j-mo [3:55 PM]  
I would make them all 'tied' for last place.

[3:55]  
ordering among them doesn't matter, if they all have the same value

