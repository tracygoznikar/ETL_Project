!(https://github.com/tracygoznikar/ETL_Project/blob/main/Images/download.jfif)
# ETL Technical Report
## Purpose
<blockquote>The purpose of this project is to introduce students to extracting, transforming, and loading data into a database for retrieval. The requirements of this ETL Project included the following:
<br>
<ul>
    <li> Project must use 2 or more sources of data. Recommended sites are: <a href="https://data.world/">Data World</a> or <a href="https://www.kaggle.com/">Kaggle</a> (APIs can be used as well)</li><br>
    <li> A technical report must be submitted which details sources of data, type of files, type of database, and expected output</li>
</ul>
</blockquote>

## Extracting Data Sources
<blockquote>The first data source we used was from Kaggle. We used the <a href="https://www.kaggle.com/mylesoneill/world-university-rankings">World University Rankings</a> dataset. Its comprised of three separate ranking sources that attempt to rank institutions of higher education from best to worst. One list is from the Tiimes Higher Education World University Ranking, the other from Academic Ranking of World Universities (aka Shanghai Ranking), and the third is from the Center for World University Rankings. The second data source comprises <a href="https://www.kaggle.com/jessemostipak/college-tuition-diversity-and-pay?select=tuition_cost.csv">tuition</a> costs. All files are in comma-separated format.
<br>
<br>
These 3 rankings use different criteria to rank universities. Therefore, there are not many columns of data that are the same but it will be interesting to see where a university ranks on one list compared to another. The tuition cost file provides more detail about the institutions such as whether or not they're 2 or 4 year, public, private or for-profit, and includes the state the school is located in which isn't available in the ranking files.
<br>
<br>
We used Pandas within a Jupyter Notebook to handle all phases of ETL.
</blockquote>

## Transformation
<blockquote>The only column of data present in all files is the name of the university. This is not ideal to have a name field as the primary key. We decided to only focus on schools in the U.S. Also, the files cover different ranking years. Years 2012-2015 are the only years present in all 3 ranking files. Additionally, the tuition cost file only covers the 2018-19 academic year. With that we filtered 2 of the ranking files on the year field and country field. The Shanghai Ranking file didn't include a country column but we also found a crosswalk file which simply listed university names and country. We were able to merge these two lists and then filter(.loc) only U.S. schools to create a final dataframe for the Shanghai ranking.
<br>
<br>
Additionally, there were no duplicates in any of the files as each school was listed only once. Also, we didn't feel the need to remove any columns as the point of selecting the datasets was to see the different criteria used by the different rankings. At the point of analysis the decision can be made to remove any extraneous columns.
</blockquote>

## Loading
<blockquote>We loaded all data into a sql database using pgAdmin. We have a total of 4 tables, 1 for each of the different rankings, and a table for the tuition costs. The user has the option to join data using the school name or simply to view data one ranking at a time.</blockquote>

## Challenges

<blockquote>As mentioned previously, it wasn't an ideal situation to have a name column as the primary key. Therefore, when joining the Shanghai ranking with the crosswalk file, we encountered non-matching school names, when indeed the school was the same. An example of this is one list would list University of California-Berkeley and the other would list University of California, Berkeley. We encountered several inconsistencies such as this. We asked the TA how we should handle these type of discrepancies, with respect to the time restraint on the project and our novice experience. The TA mentioned some solutions but none were easy fixes and we were finally advised to ignore the non-matching records.</blockquote>

## Next Steps
<blockquote>It would be interesting to see how certain schools rank on the different lists. Analyzing whether or not a prominent school is higher on one list and why they might be lower on another since these rankings source from different countries. We'd also want to determine if a higher ranking correlates to higher tuition. Since we have the data, determining if 2-year schools are ranked lower than 4-year or not and do the same with school type: public, private, non-profit, or for-profit.</blockquote>


