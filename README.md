# DataScienceProject1 Porposal
SpringBoard Data science project on analysis of 20 years of game history


1. Problems: Review the 20 year history of games.
   What is the relationship between review score and other factors. 
   How to achieve higher score and avoid low scores   

2. Who is your client and why do they care about this problem? 
   In other words, what will your client DO or DECIDE based on your analysis that they wouldn’t have otherwise?

   My cliend would be game developer/publisher. 
   Based on my analysis, they might decide 
      A. Should they continue with same series game? Time gap to publish a new game? Which platform?
      B. If there is a need to develope new game, what is the best combination of genres & platforms? 
          - based on score (assume higher score indicate higher demand)
          - based on which genre/platform has least games available (to satisfy players with different tasts)
      C. How to avoid extremely bad games

3. What data are you going to use for this? How will you acquire this data?
   data set https://www.kaggle.com/egrinstein/20-years-of-games
   crawled from http://www.ign.com/reviews/games

4. In brief, outline your approach to solving this problem (knowing that this might change later).

   A. History & Trends: 
      Most popular year? month? day? genre? by platform/genre/series games?
      Most popular platform and genres? what are percentage?
      Platforms corresponding to computer, console, portable, mobile, arcade. How these changes over years?
      games corresponding to company: sony nintendo microsoft sega snk bandai 
      Most common words in title?

   B. How score of game related to other factors:
      Same game on different platform has the same score? If not, which platform tend to have lower score?
      How score/score phase related to different platforms, genres, and release year/ month/ day? 
      The ranking of avg. score for each combination of genre & platform.
      Are series of games have higher scores? which platform/genre particularly. 
      Avg. year for release of next game in same series. Is score increasing? Any relationship with gap years? 

   C. Analysis on successful games/bad games: 
      The characteristics of game which has score = 10? game which has score < 5?
      What is the characteristic for games which has score <= 8.5 but a yes for editor's choice? 
   
5. What are your deliverables? Typically, this would include code, along with a paper and/or a slide deck.  

# Data Wrangling Steps
   1) check if there is any missing value --> no missing value
      check outlier--> year 1970, stay in the dataset   
   2) Adding "company" column by mapping platform to company which released it
      adding "type" column by categorize the platforms by types like console, phone, PC, Portable 
      adding "date" column by combine year, month, day usinng pd.to_datetime()
   3) Join the game data with another dataset which describe when the platform is released
   4) plot the distribution of scores, outlier on the left side, not normally distributed, scores skewed to the left
      summarize the data, range of the score from [0.5,10],
      so the outliers on the left is not because of nobody reviews the game, outliers are also important in the dataset.
   
# Story Telling

Having made these plots, what are some insights you get from them? Do you see any correlations? Is there a hypothesis you would like to investigate further? What other questions do they lead you to ask?

By now you’ve asked a bunch of questions, and found some neat insights. Is there an interesting narrative, a way of presenting the insights using text and plots from the above, that tells a compelling story? As you work out this story, what are some other trends/relationships you think will make it more complete?

Note including: 
The questions you asked
The trends you investigated
The resulting visualizations and conclusions.

      Part 1: Explore number of releases

      Question1: Most popular year, month, day to release a game
      
Dates that release most amounts of games:
          Year 2008 : 1915 games
          Month 11 : 2657 games
          Day 14 : 693 games
          Date 1999-07-06 : 73 games
          The most popular month-day pair is 2008-11: 256 games 
          The combination of most popular year, month and day is 2008-11-14,
          when 28 games are relased, ranked number 6 popular date of all game history.
Trend:
From bar plot of number of y = releases v.s. x = release_year/release_month/release_day
The first small peak is reach by year 2000 (4th top releases). With a slightly drop from 2000 to 2001, number of releases each year continued increasing till 2009. 2008, 2009 and 2007 are top 3 years that released most video games, indicating that game video industry is at its peak during these years. 

From Heatmap, x = release_year, y = release_month, number on each small cube is number of releases
From kdeplot, the density is more clear: 
Year 2000-2010, September-November has relatively more releases than other times.
Year 2007-2008, October-Novermber are peak times for game releases

Number of releases continued decreasing after 2009. Within each quarter, the last month of each quarter (month 3,6,9) has most games released except for 4th quarter. The 4th quarter anomly might due to holidays and vacation in December. 

It's worth noticing that November, October and December, March and December are top 5 months for releasing games. The 4th quarter has 0.347489932885906% of total releases. However, the total releases on each day of the month is similar. 

      Question 2: Popular releases by type, company, genre
Number of games releases by platform, genre, type ,and company (Top 3)
By grouping data by different columns and count the size, calculate the relative proprotion
Platform: 19.09% of games released on PC, 9.05% on PlayStation2, 8.75% on Xbox 360 
Genre: 20.38% of games are action games, 10.287% sports, 8.644% shooter  
Type: 52.4% of games released on a console,computer 18.6% and portables 18.4%
Company: others 29.18%, Sony 27.16%, Nintendo 21.86%

      Question 3: Pattern of games releases counts each genre by year
By visulizing releases counts for each year on different genres through heatmap, we can see that:
Year 2007, 2008 and 2009 has most releases for Action games. 
Year 2008 is also the year of Adventure games, shooters game.   
Year 2002 and Year 2008 tied, ranked number one on sports game genre.  

      Part 2: Explore relationship of review scores of games with other factors
      
      Question 1: The distribution and some statistics of the review scores? Is is normally distributed?
There are 18625 games reviewed, with mean score of 6.950459 , max score 10 and min score 0.5. There is no missing value for score columns. The distribution of review scores of games is skewed to left, with outliers on left side. IQR of review score is [6,8.2]

      Question 2: Are review socres distribution same for all the platform type? Which has highest/lowest scores?
By plotting the violin plot on calculated average score by different types of platform:
Mobile games has highest average score (7.306)
Arcade games has lowest average score(6.069)
Portable games and acade games has stable scores (no outlier on both side)
Mobile and other games tend to have both perfect reviews and worst reviews.
Consle games and computer games tend to have worst reviews.

      Question 3: Are review socres distribution same for all the platform type? Which has highest/lowest scores?
By caluclate the mean score for different company and plot the violin plot of Review scores v.s. Platform Company:
Games on Apple devices have the highest average review scores (7.322)
However, Games for Apple devices tends to both get highest scores and lowest socres.
Games on Nintendo have lowest average review socres (6.446611) 
Games for Bandi devices very have stable performances (about [6,8])
For all companiess, it seems that games are more likely to get below average scores.

      Question 4: Any trends between review score by genre?
Bar plot, swormplot, and voilin plot:
Top 3 review scores genres: 1) Compilation, complition 2) Hardware 3) PUzzle, RPG 
                   Worst 3: 1) Hunting, Action 2) Sports, Fighting 3) Ducation, Trivia

The games with very high or very low average scores only has a few games released in its genre. 
The violin plots of review score corresponding to popular genres (most games released) show that review scores 
are roughly normally distributed with slight tail to the left (0). From the plot, sports and racing games has largest range of scores and more outliers on both sides.
The standard deviation of review scores for Racing, Sports and Shooter games are larger than other genre's, indicating there performances are more volitile.

      Question 5:  Trend of Average Review score by Year and Genre?
line plot & Heatmap
The average review socres continues to increase with first drop in 2000, follow by a small drop by 2002.
The score continues to increase to 2005, and then keep decreasesing till 2008. From 2008, the score keep increasing. The lowest average scores occures in 2008.

The heatmap also indicate that the average score for many genres in 2008 is lower than others.
For Fight and action genre games, 2013 is the worst year. 

      Part 3: Worst games & Perfect Games characters:
THE WORST Games:
32.86% of games for Nintendo falls in the range of a bad game(lower 25%)
38.461% of games for Arcade is bad game
33.4% of the games released in 2008 are bad games. 
The Perfect Games:
Total of 55 perfect games (review score = 10)
Top platform: 18% of perfect games is designed for Game Boy Color
Top genre: 30.9% of perfect games has genre Action, Adventure is perfect.
Top year: Year 1999 release 20% of perfect games

# Inferential Statistics
Are there variables that are particularly significant in terms of explaining the answer to your project question? 
Are there strong correlations between pairs of independent variables, or between an independent and a dependent variable? 

      Question1: More releases = more bad games? What is the relationship between number of releases and avg. review score for each year?

Null hypthosis: the slope between number of games released each year and average score for that year is zero. 
By use scipy.stats, the leaset square regression indicate there is a negatvie relationship between two variables, however, with p-value = .19>.05, accept the null hypothesis that slope is 0. There statistical evidence that more games relaased results a poor average score.

      Qustion2: Is it better that a game released for different platforms?
By group the dataset by title and count number of platforms for each title. Calculate the average score corresponding to number of platforms. 

Null hpythosis: no relationship between average score and number of platforms a game released on (slope = 0). 
P-value =.0103, so reject the null hypothesis and conclude there is a positive relationship between two variables. Least square linear regression slope = .087, indicate a positive relationship between two variables. The more platforms released on, the higher average score.

      Question3: How score varies according to difference between game releases and platform releases?
Null hypothesis: no relationship between difference of game & console release days and score of games. 
Fitting least square linear regression to x= difference in release days and y = score, slope is negative with p-value<.01. So reject null hypothesis and conclude that there is significant relationship between two variables. The later game released after the platform is released, the lower the score.

The kdeplot shows the density of scores and difference in releases dates. Most of games are released after 500-1000 days after a particular platform is released and has a score around 8. Plotting year difference between game and platform release dates, we can see that no clear trends. However, average score decreases after 7 years of platforms released and increase at year 10,but continue decrease as years passed by.
The bar chart shows that portable game has score less than console games before year 6. At year 6 and 7, the portable games outperform console games.

      Question4: Is games in series has better performances than non-series games?
Test the null hypothesis that two group has same mean by independent t test, p-value<.001, reject the null hypothesis and conclude there is significant difference between two groups. Game series has higher score than non-series group.Series games has average score (mean = 7.15) higher than non-series games(mean = 6.48) 

Except for arcade games, series games for different types platforms has higher score than non-series games.
