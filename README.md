# Investigating Bias in Wikipedia Article Counts by Country

This project was performed for **Assignment 2: Bias in Data** in my Human-Centered Data Science course (DATA 512, University of Washington, Autumn 2017). The assignment description can be found here (as of November 2017): https://wiki.communitydata.cc/HCDS_(Fall_2017)/Assignments#A2:_Bias_in_data

For this assignment I investigate bias in English Wikipedia political article coverage by country. I look at two different metrics regarding the coverage of political figures by country:

* **Total Coverage:** proportion of articles about political figures compared to the country's population
* **High-Quality Coverage:** proportion of high-quality articles compared to the total number of articles for the country

## Data Source



## Output Data

The cleaned data table can be found in `en-wikipedia_traffic_200801-201709.csv` ([link](data/en-wikipedia_traffic_200801-201709.csv)). It consists of monthly visit counts grouped by API call (i.e. Pagecount, Pageview) and source (i.e. all, desktop, mobile). The schema is as follows:

| Column        				| Value 		|
|-------------------------------|---------------|
| **year** 						| year (YYYY)	|
| **month**						| month (MM)	|
| **pagecount_all_views**		| num_views 	|
| **pagecount_desktop_views**	| num_views		|
| **pagecount_mobile_views**	| num_views 	|
| **pageview_all_views**		| num_views 	|
| **pageview_desktop_views**	| num_views 	|
| **pageview_mobile_views**		| num_views		|

Data notes:

* Two rev_id's returned invalid results in ORES....list them here and mention how they were handled.

## Reproducibility

As previously mentioned, a major goal of this work is to make it fully reproducible. This means that any user should be able to run my code and produce the exact same result as presented here.

To test this out, simply `git clone` this repository, and open and run `hcds-a1-data-curation.ipynb`. The results should be exactly reproduced.

However, note that the code is configured to refer to local data files if they exist. This was done for two reasons:

* to create checkpoints (with reproducibility in mind)
* to prevent redundant API calls

To truly duplicate this analysis from scratch, delete all the data in `/data` and `/data/raw`, and then run the notebook. The data will be re-retrieved from Wikimedia, and new .csv files will be written. The final visualization is always regenerated regardless of whether new or existing source data is used.

If differences are found in results between code run with a clean slate vs. otherwise, they should be able to be traced to differences in the source data itself, or in modules upon which the code was written. Hopefully the "data checkpoints" will help with troubleshooting if this is ever found to be the case.

## License

Documentation on both Wikimedia REST API endpoints endpoints can be found here:
https://wikimedia.org/api/rest_v1/. For the endpoints used in this project, the content is available under the [CC0 1.0 license](https://creativecommons.org/publicdomain/zero/1.0/).

**IMPORTANT:** If you plan to modify the code to call to different API endpoints, note that these may fall under different licensing (e.g. CC-BY-SA 3.0 and GFDL licenses). Please be sure to refer to the endpoint documentation above for terms and conditions before using any API endpints other than the two use in this original project.

Please also refer to the Wikimedia Foundation Terms of Use prior to use:
https://wikimediafoundation.org/wiki/Terms_of_Use/en


## Writeup

You are also expected to write a short reflection on the project, that describes how this assignment helps you understand the causes and consequences of bias on Wikipedia.

Might put it here. Might put it in a different file. Save this for the end.

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

