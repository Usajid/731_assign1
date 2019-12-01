# EECS 731 Jimmy Wrangler, Data Explorer (Assignment # 01)


### Quick Note:
If you are interested in only looking at notebook, please access the notebook in **/notebooks/data_explorer.ipynb**.

/notebooks: Contains the notebook of this assignment.

/data: Contains the data csv files (movies.csv, ratings.csv, links.csv, tags.csv)

Also, some content of this assignment and my assignment # 03 (Weekend Movie Trip) notebook will be similar, as I have used the same datasets for both assignments.

### Objective:

Traveling the world on a mission to discover new data

1. Set up a data science project structure in a new git repository in your GitHub account

2. Install Jupyter notebook prerequisites (Anaconda, Python, etc.)

3. Select an industry

4. Select two to three public data sets from that industry

5. Load the data sets into panda data frames following the 10 minutes to pandas guide

6. Formulate one or two ideas on how the data sets could be combined to establish
additional value using exploratory data analysis

7. Transform the data sets into a single data set while following data preparation processes
to clean and transform features (use pandas documentation for help)

8. Document your process and results

9. Commit your notebook, source code, visualizations and other supporting files to the git
repository in GitHub

### Datasets:

For this assignment, I took three datasets from the MovieLens Website (https://grouplens.org/datasets/movielens/), namely **Movies, Ratings, and Tags datasets**. First, we do exploratory analysis on each dataset separately, followed by cleaning and merging (those datasets into one) process (Data csv files are in /data/ directory of this repository).

### Process:

<ul>
<li>First I loaded and inspected the three data csv files (movies.csv, ratings.csv, links.csv, tags.csv), so I can explore and combine MOVIES, RATINGS, and TAGS information from them to prepare for the similar movies clustering process. (Please see the /notebooks/movieTrip.ipynb for more details)</li>
<li>Then, we merge the information from these data frames into a new data frame that contains MOVIES, THEIR RATINGS AND TAGS VECTORS.</li>
<li>Next, we apply K-Means Clsutering Algorithm on this new Data frame to get 100 clusters, each containing similar movies with similar tags and ratings.</li>
<li>Next, we analyze the qualitative performane of clustered similar movies groups.</li>
 </ul>

*The process and results are detailed as follows, as well as in /notebooks/movieTrip.ipynb notebook.*

### Discussion and Results:
Since we have three different csv files for three different things, i.e. MOVIES, RATINGS, TAGS. So, first we inspected how we can extract and merge the information for the similar movies clustering process.

Then, we **MERGED** the required columns from these dataframes and also **dropped NA** valued rows. Finally, the merged dataframe to be used for clustering process was obtained (PLease see /notebooks/movieTrip.ipynb for more details). First five rows of merged dataframe are as follows:


![](figs/fig1u.png)

![](figs/fig2u.png)

![](figs/fig3u.png)

![](figs/fig4u.png)

![](figs/fig5u.png)

![](figs/fig6u.png)

movieId | title |	userId |	rating	| tag

187595 |	Solo: A Star Wars Story (2018) |	62.0 |	4.0 |	starwars

193565 |	Gintama: The Movie (2010) |	184.0 |	3.5 |	anime

193565 |	Gintama: The Movie (2010)	184.0 |	3.5 |	comedy

193565 |	Gintama: The Movie (2010)	184.0 |	3.5 |	gintama

193565 |	Gintama: The Movie (2010) |	184.0|	3.5 |	remaster



This final dataframe also has some interesting insights, as follows:

**Unique Users :  54**

**Unique Movies :  1464**

**Unique Tags :  1424**

**Based on the above final table, I have also given the clustering process in this assignment notebook, which is not required by the given assignment,thus, optional part that can be skipped/ignored.**

# Conclusion

This was the basic data science assignment, but, I believe this was the **most important data science asignment**. Because data cleaning/ feature engineering process is vital before doing any data modeling stuff. As there is a famous term in data science and machine/deep learning community for importance of data pre-processing, i.e. GIGO (Garbage In, Garbage Out). So, in my opinion, this assingment was very important and useful for me to understand the baseics of data pre-processing. So, first we loaded three separate datasets, followed by merging them into a single table based on some common features/fields. Along the way, we also did cleaning/feature engineering on these tables e.g. Dropping NaN values.
