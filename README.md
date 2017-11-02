# Investigating Bias in Wikipedia Article Counts by Country

This project was performed for **Assignment 2: Bias in Data** in my Human-Centered Data Science course (DATA 512, University of Washington, Autumn 2017). The assignment description can be found here (as of November 2017): https://wiki.communitydata.cc/HCDS_(Fall_2017)/Assignments#A2:_Bias_in_data

## Overview

For this assignment I investigate bias in English Wikipedia politician coverage by country. I look at two different metrics regarding the proportion of articles about politicians by country:

* **Total Coverage:** proportion of articles compared to the country's population
* **High-Quality Coverage:** proportion of high-quality articles compared to the total number of articles for the country

I report on the extremes of both of these metrics (i.e. countries with the highest and lowest proportions of each metric) and provide a short reflection on this activity below. The full analysis and results can be found in the Jupyter Notebook in the main folder of this repository (i.e. [hcds-a2-bias.ipynb](hcds-a2-bias.ipynb)).

### Results: Total Coverage

**Ten Highest-Ranked Countries**

|Country  						| Population 	| Articles 	| Articles Per 100 People 	|
|-------------------------------|---------------|-----------|---------------------------|
|Nauru							|10860			|53			|0.488029					|
|Tuvalu							|11800			|55			|0.466102					|
|San Marino						|33000			|82			|0.248485					|
|Monaco							|38088			|40			|0.105020					|
|Liechtenstein					|37570			|29			|0.077189					|
|Marshall Islands				|55000			|37			|0.067273					|
|Iceland						|330828			|206		|0.062268					|
|Tonga							|103300			|63			|0.060987					|
|Andorra						|78000			|34			|0.043590					|
|Federated States of Micronesia	|103000			|38			|0.036893					|

**Ten Lowest-Ranked Countries** (ascending order)

|Country  				| Population 	| Articles 	| Articles Per 100 People 	|
|-----------------------|---------------|-----------|---------------------------|
|India					|1314097616		|990		|0.000075					|
|China					|1371920000		|1138		|0.000083					|
|Indonesia				|255741973		|215		|0.000084					|
|Uzbekistan				|31290791		|29			|0.000093					|
|Ethiopia				|98148000		|105		|0.000107					|
|Korea, North			|24983000		|39			|0.000156					|
|Zambia					|15473900		|26			|0.000168					|
|Thailand				|65121250		|112		|0.000172					|
|Congo, Dem. Rep. of	|73340200		|142		|0.000194					|
|Bangladesh				|160411000		|324		|0.000202					|


### Results: High-Quality Coverage

**Ten Highest-Ranked Countries**

|Country  					| Articles 	| HQ Articles 	| High-Quality Proportion (%) 	|
|---------------------------|-----------|---------------|-------------------------------|
|Korea, North				|39			|9				|23.076923						|
|Romania					|348		|45				|12.931034						|
|Saudi Arabia				|119		|15				|12.605042						|
|Central African Republic	|68			|8				|11.764706						|
|Qatar						|51			|5				|9.803922						|
|Guinea-Bissau				|21			|2				|9.523810						|
|Vietnam					|191		|18				|9.424084						|
|Bhutan						|33			|3				|9.090909						|
|Ireland					|381		|31				|8.136483						|
|United States				|1098		|86				|7.832423						|

**Ten Lowest-Ranked Countries**

There are 39 countries with zero high-quality articles:  
Andorra, Antigua and Barbuda, Bahamas, Bahrain, Barbados, Belgium, Belize, Burundi, Cape Verde, Comoros, Djibouti, Dominica, Eritrea, Federated States of Micronesia, French Guiana, Guadeloupe, Guyana, Kazakhstan, Kiribati, Lesotho, Liechtenstein, Macedonia, Marshall Islands, Monaco, Mozambique, Nauru, Nepal, San Marino, Sao Tome and Principe, Seychelles, Solomon Islands, Suriname, Swaziland, Switzerland, Tajikistan, Tonga, Tunisia, Turkmenistan, and Zambia


### Reflection

TODO: Write a few paragraphs, either in the README or in the notebook, reflecting on what you have learned, what you found, what (if anything) surprised you about your findings, and/or what theories you have about why any biases might exist (if you find they exist). You can also include any questions this assignment raised for you about bias, Wikipedia, or machine learning.

## Data Sources and Licensing

Data for this project was obtained from three different sources, as described below. License information for each source is also described below.

### Population data

Population data for 210 countries was made available by the Population Reference Bureau (PRB). The specific dataset used in this analysis represents world populations by country as of Mid-2015. It is sourced from the *2015 World Population Data Sheet*, which is described in detail here:  
http://www.prb.org/Publications/Datasheets/2015/2015-world-population-data-sheet.aspx

The actual data used in this analysis can be found here:  
http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14  (see Excel icon at top right)

The raw data includes six columns:

* **Location**
* Location Type
* TimeFrame
* Data Type
* **Data**
* Footnotes

For this analysis I only use data from the columns bolded above (i.e. `Location` and `Data`).

The population data is copyrighted by PRB and therefore is not included within this repository. See the [Reproducibility](#reproducibility) section below for specifics on how to retrieve this data if you wish to duplicate or expand upon this analysis.

### Page Data

The wikipedia politician article dataset can be found on Figshare at the following link:  
https://figshare.com/articles/Untitled_Item/5513449

The link above includes the following documentation about the data:

> This project contains data on most English-language Wikipedia articles within the category "Category:Politicians by nationality" and subcategories, along with the code used to generate that data. Both are released under the CC-BY-SA 4.0 license.
> 
> Data
The data was extracted via the Wikimedia API using the associated code. It is formatted as a CSV and saved as page_data.csv in the "data" directory. Columns are:
> 
> 1. "country", containing the sanitised country name, extracted from the category name;
> 2. "page", containing the unsanitised page title.
> 3. "last_edit", containing the edit ID of the last edit to the page.
> 
> Country codes are inconsistent. Where possible, they have been modified to match the country names found in http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14 - but the PRB dataset contains nations not found in Wikipedia, and vice versa.
> 
> The actual recursion only went 2 levels deep into the category tree: someone listed as an Antiguan politician, say, is included - someone exclusively listed as an Antiguan politician who was assassinated is not.

When retrieved from the site above, the download consists of a zip file with the raw data and the code that was used to create it. I have saved the raw data alone (i.e. excluding the source code) to this GitHub repository, under `data/raw`.

As mentioned in the documentation above, the data is released under the CC-BY-SA 4.0 license. 


### Page Ratings (Wikipedia ORES)

Page ratings are retrieved using the Wikimedia ORES RestAPI.

General information about the ORES system can be found here:  
https://www.mediawiki.org/wiki/ORES  
and here:  
https://ores.wikimedia.org

Documentation for the ORES API can be found here:  
https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context

The ORES API takes a handful of arguments, including project, model, and a string of revision IDs, separated by '|'. The model returns a JSON file with a rating and other information for each revision ID. The rating options, from best to worst, consist of the following:

* **FA:** Featured article
* **GA:** Good article
* **B:** B-class article
* **C:** C-class article
* **Start:** Start-class article
* **Stub:** Stub-class article

For our second metric, we consider articles to be "high-quality" if they are rated as either "FA" or "GA".

The ORES API does not explicitly list a license for use. The project is hosted by the Wikimedia Foundation, so we assume it falls under the same general license as Wikimedia content:

Attribution-ShareAlike 3.0 Unported (CC BY-SA 3.0)  
https://creativecommons.org/licenses/by-sa/3.0/

## Output Data

The cleaned data table can be found in `population_and_article_quality_data.csv` ([link](data/population_and_article_quality_data.csv)). It consists of country populations and article ratings by country monthly. The schema is as follows:

| Column        		| Value 					| Type		|
|-----------------------|---------------------------|-----------|
| **country**			| country name 				| string 	|
| **population**		| country population		| integer	|
| **article_name**		| article name 				| string	|
| **revision_id**		| article revision ID 		| integer	|
| **article_quality**	| article quality			| string	|

Data notes:

* ORES returned invalid results for a handful of articles. These articles were included in the total article counts, but were excluded from the high-quality article count since the missing articles could not be ranked.
* 23 countries from the Population data did not have any articles with a corresponding country name. These countries were removed from the analysis per the assignment instructions.

## Directory Structure

```
data-512-a2/
    |- data/
        |- raw/
            |- page_data.csv 				 // page data
        |- population_and_article_quality_data.csv   	 // combined data table for analysis
    |- hcds-a2-bias.ipynb 				 // source code (Jupyter Notebook) 
    |- LICENSE 						 // standard MIT License
    |- README.md
 ```

## Reproducibility

This work is intended to be fully reproducible. This means that any user should be able to run my code and produce the exact same result as presented here.

To test this out, simply `git clone` this repository, and open and run `hcds-a2-bias.ipynb`. The results should be exactly reproduced.

However, note that exact reproducibility will be limited by two factors:

* PRB population data is copyrighted and therefore is not included within this repository. Thus, users that wish to reproduce this analysis must download the population data from PRB on their own. It is possible this dataset may have changed between the time of my analysis and your own.
* The ORES API returns results based on the present state of each given article. Thus, any changes to articles since my implementation may result in changes to the final results.

To mitigate the potential differences, I have included my `merged_df` dataframe in `population_and_article_quality_data.csv`. The analysis can be picked up from the point where this file is read/written, and all downstream analysis should match my own exactly.

Do note if you plan to attempt the analysis from this "checkpoint", you may need to run the first line of code in the notebook to import relevant modules.

## License

This work is released under MIT License, per the Data Sources and Licensing](#data_sources_and_licensing) section above.

Feel free to contact me (Rex Thompson) at rext@uw.edu if you have any questions about this analysis.