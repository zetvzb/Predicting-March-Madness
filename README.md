# Predicting-March-Madness QAD Random Forrest with advanced statistics. 
Prediction Model for March Madness 2019

  
## 2019 March Madness Prediction Model
*Step 1:  Data Load* 
Pre-Processing Detailed Datasets from Kaggle Competition as Sponsored by Google
*Step 2: Setup Libraries*
Required R Packages: 
* library(tidyverse)
* library(gridExtra)
* library(knitr)
* library(magrittr)
* library(XML)
* library(RCurl)
* library(dplyr)
* library(data.table)
* library(stringr)
* library(randomForest)
* library(tidyr)

*Step 3: Calculate Posessions Per game Statistics as the control*

*Step 4: Feature Engineering*
Calculate TEAM season TOTALS                                                                                                  
Methodology inspired from Max Phillips Kernel on Kaggle                                                                       
Transforms Individual Game data for each Team to Season Totals. Creates a Tidy Dataset                                        
                                                                                                                                
First I will define a function that will take the detailed results data and reshape it so that it results in a dataframe where each observation is a team for that season and their totals statistics for that season. It will also calculate the statistics allowed for the season. This function only requires pass regular season stats and references a Teams Dataset.  

*Step 5: Create a dataframe of season averages for each team --------------------------------------------------#
#Now Create dataset that does the same process as above, but as team game averages instead of totals.                            #
# Next I will define a function that takes in the totals dataframe from the above function and calculate a season averages dataset.
# this function also only requires one parameter to be passed to it, the totals dataframe.      


#------------------------------------------------- Advanced Stats ---------------------------------------------------------------#
#In this section, I will analyse the impact of advanced stats on a teams performance.                                            #
#The first subsection will deal with per-game advanced stats, while the second will                                              # 
#look at season-aggregated advanced stats.                                                                                       #
                                                                                                                                 #
#As a lot of you are probably aware, since the popularisation of sabermetrics and integration of                                 #
#advanced analytics into other sports, there are better ways of measuring a team's expected success.                             #
#These per game advanced analytics are displayed below. These metrics all show a considerable difference                         #  
#when comparing wins and losses in regular season play between 2003 and 2018.                                                    #
                                                                                                                                 #    
#The calculations of the displayed advanced stats are as follows:                                                                #
#Possessions = 0.96 x (FGA + Turnovers + (0.475 x FTA) - Offensive Rebounds                                                      #
#Offensive Rating = 100 x (Score / Possessions)                                                                                  #
#Defensive Rating =  100 x (Opponent's Score / Possessions)                                                                      #
#Strength of Schedule = 100 x (Offensive Rating - Defensive Rating)                                                              #  
#Performance Impact Estimator = Score + FGM + FTM - FGA - FTA + Defensive Rebounds + (0.5 * Offensive Rebounds) + Assists +      #
#Steals + (0.5 * Blocks) - PF - Turnovers                                                                                        #  
#Team Impact Estimator = PIE / (PIE + Opponent's PIE)                                                                            #
#Assist ratio  = 100 * Assists / (FGA + (0.475 * FTA) + Asistst + Turnovers))                                                    #
#Turnover ratio = 100 * Turnovers / (FGA + (0.475 * FTA) + Assists + Turnovers)                                                  #
#True Shooting% = 100 * Team Points / (2 * (FGA + (0.475 * FTA)))                                                                #
#Effective FG% = (FGM + 0.5 * Threes Made) / FGA                                                                                 #  
#Free Throw rate = FTA / FGA                                                                                                     #  
#Offensive Rebound = Offensive Rebounds / (Offensive Rebounds + Opponent's Defensive Rebounds)                                   #   
#Defensive Rebound = Defensive Rebounds / (Defensive Rebounds + Opponent's Offensive Rebounds)                                   #
#Total Rebound = (Defensive Rebounds + Offensive Rebounds) / (Defensive Rebounds + Offensive Rebounds +                          #
#Opponent's Defensive Rebounds + Opponent's Offensive Rebounds)  



#--------------------------------------------------------- Massey Ordinals Rankings -----------------------------------------------------------#
#Using Massey Ordinals Data to use Rankings as a feature in the model.                                                                         #
#Specifically chose Ken Pomeroy and Jeff Sagarin Rankings as they are the most famous.                                                         #
#Select the last rankings of each season for each team. Do not load entire Massey Ordinals dataset, it is a billion records.                   #
                                                                                                                                               #
## Rankings and winning percentages?                                                                                                           #
#As can be seen, the better Pomeroy ranked team won on average 71.9% of the time in tourney games during 2003-2018.                            #
#The 2008 season saw the highest percentage of better ranked teams winning at 81% of games,                                                    #
#while 2014 was the worst seasons for better ranked teams, with them winning only 65% of the time.                                             #
                                                                                                                                               #
#Sagarin rankings were fairly similar, with an average performance of 71.6%, just below Pomeroy's rankings.  




#----------------------------------------------------------- Feature Selection -------------------------------------------------------------------#
#First Merge the Seasonal Stat Averages by Team with the Advanced Stats by Team                                                                   #
#Second Create a Field called "SeasID" that is a combination of Season and TeamID. This is a unique identifier for each team by season            #
#Third Define the Test set as Season, Team 1, Team 2, and Outcome (1=Win, 0 = Loss). Outcome is if Team 1 beat Team 2.                            #
#Munge Team Seeds to Give Seeds by Season by Team                                                                                                 #
#Then Joing Regular Season Stats with Team Seeds and All Aggregated Stats Data                                                                    #
#Clean up Rows with Missing Data, Remove them                                                                                                     #
#Clean up dataset Feature Names with Convention "Team x_name_of_Stat"    


#--------------------------------------------------------------- Train Model -----------------------------------------------------------------#


#----------------------------------------------------------------- Test Set -------------------------------------------------------------------#


#---------------------------------------------------------------Predict------------------------------------------------------------------------#
