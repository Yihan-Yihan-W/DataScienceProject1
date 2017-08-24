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
