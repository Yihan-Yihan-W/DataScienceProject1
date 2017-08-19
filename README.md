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
      Which month publish most games? 
      Most popular year? month? day? genre? by platform/genre/series games?
      Most popular platform and genres?  what are percentage?
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
