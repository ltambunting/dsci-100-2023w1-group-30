# dsci-100-project_proposal
Template project repository for DSCI-100


"Player Stats for Top 500 Players" on the Ultimate Tennis Statistics (UTS) website provides comprehensive statistical information about 
the top 500 professional tennis players in the world. These player statistics offer valuable insights into the performance, strengths, 
and weaknesses of these athletes. 
Problem: 1. What is the relationship between the age of tennis athletes an their best rankings? 
         2. Which country/athlete contains the best rank. 
         3. What is the relationship between the use of backhand and the best rank?
         4. Are the left-handed athletes get relatively higher average best ranks, or do the right-handed athletes?
         5. (1)If we are provided with a new observation which includes the country of the athlete, what best-rank is most possibly be achieved by him/her?
            (2)If we are provided with a new observation which includes the backhand of the athlete, what best-rank is most possibly be achieved by him/her?
            (3)If we are provided with a new observation which includes the play-hand of the athlete, what best-rank is most possibly be achieved by him/her?
            (4)If we are provided with a new observation which includes the age of the athlete, what best-rank is most possibly be achieved by him/her?
            (5)If we are provided with a new observation which includes the country,backhand, play-hand, and age of the athlete, what best-rank is most possibly be achieved by him/her?
            Are the results for each question different? Which one is more precise?
Data set: Our data set has 501 rows and 6 columns which are chosen from the original 38 columns. The 6 columns are Age, 
Country, Plays, Name, BestRank, and Backhand, respectively. All of them will be used to complete the further classification and 
prediction problems.

Preliminary exploratory data analysis:
From the url: https://drive.google.com/uc?export=download&id=1_MECmUXZuuILYeEOfonSGqodW6qVdhsSLinks which is an external site, we downloaded the
data as a ".csv" form data and imported it into the data folder in our jupyter notebook. To read the data, function read_csv("data/player_stats.csv")
has been used, then it turns out to be tibble with 501 rows and 38 columns. To tidy up the data as well as choose the variables we'd like to utilize,
we use the code such as: 
player_data <- read_csv("data/player_stats.csv")|>
                select(Age,Country,Plays,Name,BestRank,Backhand)|>
                mutate(BestRank = gsub("\\([^\\)]+\\)", "", BestRank))|>
                mutate(Age = gsub("\\([^\\)]+\\)", "", Age))|>
                mutate(Age=as.numeric(Age))|>
                mutate(BestRank=as.numeric(BestRank))


Methods:
Create 4 different graphs which are:
1. point graph with x_variable=age, and y_variable=BestRank 
2. point graph with x_variable=country, and y_variable=BestRank
3. point graph with x_variable=plays, and y_variable=BestRank
4. point graph with x_variable=backhand, and y_variable=BestRank
Then, for each provide it with a new observation,
for example:
1. age = 18
2. country= Brazil
3. plays= Left-handed
4. Backhand= Two-handed
Finally, create 4 classifiers and do the prediction(by k-neighbors).
After that, create a new classifier using country,backhand, play-hand, and age as predictors to predict the best_rank of a new observation.
In this process, we will also let R to help us to find the best value of k and fold the data to improve the accuracy of our prediction.
In the end, we will use the plots 1-4 to identify which three variables have a stronger influence on the result of best rank, then create a dot graph using those three variables, and use it to predict a new observation's possible best rank.

Expected outcomes and significance:
From the preliminary data, we expect to find an inverse relationship between age and BestRank; more popular tennis-playing countries (eg. USA, Spain, etc.) might have more players with top rankings; the use of backhand and best rank might not correlate as they might depend on the comfort of the player.
