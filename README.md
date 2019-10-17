# A2: Bias in Data
## Goal
This project is the second assignment of the DATA 512 Human_centred Data Science course. This assignment aims to study bias in data by looking at Wikipedia articles of politicians from different countries. The goal is to gain a better understanding of biases in data and its consequences. The analysis calculates the following metrics for each country from Wikipedia articles of their political figures:

- Proportion of number of Wikipedia articles about their political figures to the population.

- Percentage of number of high-quality Wikipedia articles about political figures for each country. This is measured using Wikipedia's machine learning service ORES API.

- A ranking of geographic regions by articles-per-person and proportion of high quality articles.

The analysis consists of calculating the proportion (as a percentage) of articles-per-population and high-quality articles for each country AND for each geographic region. By "high quality" articles, in this case we mean the number of articles about politicians in a given country that ORES predicted would be in either the "FA" (featured article) or "GA" (good article) classes.

## Data Sources

1. Politicans by Country
This dataset contains the country, revision ID and names of each politician wikipedia article. This dataset was downloaded into csv file page_data.csv. Source: https://figshare.com/articles/Untitled_Item/5513449

2. Country Population Data
The dataset contains the country name and population of that country. It was downloaded into csv file WPDS_2018_data.csv. Source: https://www.prb.org/international/indicator/population/table/

3. The ORES API was used to obtain the article quality feature. Source: https://github.com/wikimedia/ores
An article may be predicted to have one of the following quality levels:
FA - Featured article
GA - Good article
B - B-class article
C - C-class article
Start - Start-class article
Stub - Stub-class article
We define "high-quality" as an article predicted to be either FA or GA.

4. Code blocks and conceptualization of this repository has been inspired by the assignment: https://wiki.communitydata.science/Human_Centered_Data_Science_(Fall_2019)/Assignments#Scheduled_assignments

## Libraries and APIs

This analysis was done using Python 3.6 running in a Jupyter Notebook. Python packages used were pandas, matplotlib.pyplot and ores. You can pip install ores in your local notebook environment (https://github.com/wikimedia/ores)

Object Revision Evaluation Service (ORES) was used to obtain the article quality feature. The documentation for using this API can be found here: https://github.com/wikimedia/ores.

The API call function in the iPython notebook used a code block from: https://wiki.communitydata.science/Human_Centered_Data_Science_(Fall_2019)/Assignments#A2

## Output

The final format of the file "Final_combined_data.csv" is given below:

| country       | GA_FA          | revision_id  | article_quality | page| Population mid-2018 (millions) | frequency	| articles-per-population-percentage	| high-quality-percentage

where
country: the country we are talking about
GA_FA: Total number of good and featured articles for that country
revision_id: for the article
article_quality: predicted article quality
page: politician's article name
Population mid-2018 (millions): of the country	
frequency: total number of articles for that country
articles-per-population-percentage: frequency by population percentage
high-quality-percentage: GA_FA by frequency percentage

PLEASE NOTE: This notebook does not consist of the regional analysis. That has been stored seperately in the tables given in the jupyter notebook

## Using the repository
1. Clone the repo.

2. Activate a Python 3 environment.

3. Run all cells in notebook from top to bottom.

## License
This assignment code is released under the MIT License.
The Wikipedia English language articles data source is released under the CC-BY-SA 4.0 license.

## Reflection

 1. Tulavu is ranked to be the country with the highest number of articles per population, however, when we compare its population with other countries in the game, it is a significantly low. We can see that New Zealand which has higher number of articles but has a massive population. A possible argument here is that we do not know how penetrative these numbers are. What if a number of areas were left out of the population counting? Will that not introduce a bias in data? We also do not know whether the people who do not have access to internet have been covered in this data. Data collection is a something that needs to be probed into
 
 2. This dataset only accounts for English articles. Countries such as India and China where we have multiple regional languages, and high population numbers will not be fully accounted. Using this data (to train a model, perform a hypothesis-driven research, or make business decisions) might not lead to good results in these regions, however for country like the United States where English is the first language, it might be lead to relevant results.
 
3. Countries with smaller populations to have higher percentage of articles when compared to its population. This is because every country, regardless of the population size, has 1 head of state or government, and similar number of cabinet members, etc. In fact, the first table (showing top 10 highest-ranked countries in terms of number of politician articles as a proportion of country population) contains only countries that have population smaller than 1 million, with 7 out of 10 having population of 100,000 or less.

4. North Korea is an interesting observation. It has the highest quality of articles but is in the 10 lowest-ranked countries in terms of number of politician articles as a proportion of country population which includes the most populous countries, such as India, China, and Indonesia. One theory is that because North Korea is a secretive dictatorship with little known info about its politicians and because sites like Wikipedia are censored, there's few articles about its politicians. 

5. Most of the countries in the third table had multiple numbers of high quality articles, while most of the countries in the fourth table had just one high quality article. It seems that population size did not play a role in determining countries in either tables.
