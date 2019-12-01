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


Before the actual clustering algorithm start, one last pre-processing and mandatory thing I did was to produce the tags vectors as strings/categorical values are unacceptable in such scenarios. We used *TfidfVectorizer* feature of *scikit-learn library* for that. To group similar movies and recommend movies to the users, I am using **RATINGS** and **TAGS** features that are really helpful for such recommendation system. Once we get the clusters/groups, then we can recommend similar movies using those clusters. So, the **k-means algorithm** is being used for clustering simiar movies together. The input to the alogrithm would be the movies tags vectors and ratings. Consequently, the k-means algorithm clustered the similar movies together. In the end, we get **100 groups of similar movies** after the clustering process. 

First and last few clusters have been shown as follows:


**CLUSTER | MOVIES IN THE CLUSTER**

0	Little Princess, A (1995), Song of the Little ...

1	Dolores Claiborne (1995), Stand by Me (1986), ...

2	American President, The (1995), Nixon (1995), ...

3	To Die For (1995), Up Close and Personal (1996...

4	Persuasion (1995), Crumb (1994), Eat Drink Man...

5	Sixth Sense, The (1999)

6	Lion King, The (1994), Aladdin (1992), Snow Wh...

7	Batman Forever (1995), Batman (1989), Batman R...

8	Thin Blue Line, The (1988), L.A. Confidential ...

9	Moonrise Kingdom (2012), History of Future Fol...

10	Twelve Monkeys (a.k.a. 12 Monkeys) (1995), Sta...

11	Dangerous Minds (1995), Dead Poets Society (19...

12	Anne Frank Remembered (1995), Schindler's List...

13	Platoon (1986), Apocalypse Now (1979), Full Me...

14	Don Juan DeMarco (1995), What's Eating Gilbert...

15	Welcome to the Dollhouse (1995), Rebel Without...

.

.

.

89	Beautiful Mind, A (2001), Proof (2005)

90	Quiz Show (1994), Truman Show, The (1998)

91	Ran (1985), Seven Samurai (Shichinin no samura...

92	Rudy (1993), Waterboy, The (1998), Necessary R...

93	How to Make an American Quilt (1995), Four Wed...

94	Harry Potter and the Sorcerer's Stone (a.k.a. ...

95	Last Temptation of Christ, The (1988), Prince ...

96	Kingsman: The Secret Service (2015), The Man f...

97	Great Santini, The (1979), Matchstick Men (200...

98	Seven (a.k.a. Se7en) (1995), Game, The (1997),...

99	Father of the Bride Part II (1995), Angie (199...


If we analyze top keywords being used in each of the first 10 clusters, then results are as follows:

**Top terms/words per cluster:**

**Cluster :  1**
 
 india
 
 girlpower
 
 cinematography
 
 england
 
 surreal

**Cluster :  2**
 
 stephenking
 
 prom
 
 highschool
 
 firefly
 
 fathersonrelationship

**Cluster :  3**
 
 politics
 
 president
 
 africa
 
 business
 
 fbi

**Cluster :  4**
 
 journalism
 
 zooeydeschanel
 
 fbi
 
 fantasyworld
 
 farfetched

**Cluster :  5**
 
 innetflixqueue
 
 televangelist
 
 courtroomdrama
 
 janeausten
 
 biopic

**Cluster :  6**
 
 ghosts
 
 iseedeadpeople
 
 brucewillis
 
 stylized
 
 imdbtop250

**Cluster :  7**
 
 disney
 
 nanny
 
 kingarthur
 
 fish
 
 heartwarming

**Cluster :  8**
 
 superhero
 
 amyadams
 
 marvel
 
 hughjackman
 
 comicbook

**Cluster :  9**
 
 police
 
 drugs
 
 murder
 
 innetflixqueue
 
 action


**Cluster :  10**

quirky

zooeydeschanel

family

fantasyworld

farfetched

As you can see above, the keywords in each cluster show that the clustering process is doing a pretty reasonable job. Now, if we look into one of the clusters for seeing the (similar) movies in that group, we get the following result:

*Lion King, The (1994), Aladdin (1992), Snow White and the Seven Dwarfs (1937), Beauty and the Beast (1991), Pinocchio (1940), Aristocats, The (1970), Cinderella (1950), Sword in the Stone, The (1963), Mary Poppins (1964), Dumbo (1941), Pete's Dragon (1977), Alice in Wonderland (1951), Fox and the Hound, The (1981), Fantasia (1940), Honey, I Shrunk the Kids (1989), Jungle Book, The (1967), Lady and the Tramp (1955), 101 Dalmatians (One Hundred and One Dalmatians) (1961), Finding Nemo (2003)* 


As shown above, thus, user interested in one of those movies, can be **RECOMMENDED** other movies similar to that movie in this particular cluster or group, which is the core idea behind designing such clustering based recommendation systems.


# Conclusion

This was the basic data science assignment, but, I believe this was the **most important data science asignment**. Because data cleaning/ feature engineering process is vital before doing any data modeling stuff. As there is a famous term in data science and machine/deep learning community for importance of data pre-processing, i.e. GIGO (Garbage In, Garbage Out). So, in my opinion, this assingment was very important and useful for me to understand the baseics of data pre-processing. So, first we loaded three separate datasets, followed by merging them into a single table based on some common features/fields. Along the way, we also did cleaning/feature engineering on these tables e.g. Dropping NaN values.
