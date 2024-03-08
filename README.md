# PROJECT DATA ENGINEERING

## REPORT

### Preliminary
**Domain:** NBA  
**Questions:** Who actually deserved the MVP this season.  
**How good is he compared to previous MVPs?**

#### Obtain:
**BasketballReference**  
**statspergame**  
**statsadvanced**  
**teamstats**  
**allmvps**

#### Scrub:
Get datasets from csv  
drop all mvps from the past that have no blocks nor steals

We started our project by thinking about a topic that we liked. One of our first ideas was the NBA. Since it’s filled with statistics and we believed it’d be easy to find useful datasets online. 
After a look at kaggle, we didn’t find any useful NBA datasets. So after some more research, we came across basketball-reference.com, a website where there was plenty of data and statistics about NBA, so we got down to work. 
We decided that we wanted to prove if the MVP award given this year had been fairly awarded. It has been really controversial this year since Joel Embiid, center for the Philadelphia 76ers, was awarded with it. Nikola Jokić, center for the Denver Nuggets, was the heavy favourite to win the award throughout the year, and others argue the Greek Giannis Antetokounmpo deserved to be granted the prize.
The first steps were to upload the data to our python notebook. We tried to use the same methodology as the one that we have learned from this subject. Using pandas, importing csv files… 
The files were obtained from the website we previously mentioned, since it gave us the option of copying the data in a csv format. More precisely, we downloaded the 4 datasets: a table of the primary stats of every player that has played in the NBA this season, the same table but this time with exclusively advanced stats, all the teams' statistics, and also a table we found with statistics from all the previous MVPs in the history of the organisation. 
Before uploading the file, we checked we had all the information we needed within those csv files, and we removed/changed things that could cause problems.
Once all the data was successfully uploaded, we had to do a very important step, filtering. At the beginning, we had more than 500 players, so we decided that we wanted to narrow down our choice to only 25 candidates for the MVP. So our first filter was by eliminating the players that had played a few games. An NBA season is 82 games long. The MVP must be: someone who has played a considerable amount of games (if you have been injured for over half of the season, you shouldn't be considered the MVP of the season). Another condition that has to be met is that the player must be a starter, or has to have played a substantial amount of minutes. This step is very significant because, a player who have played, for example, only 5 minutes in the season, and had scored 6 points, would have very good stats, but these stats wouldn’t be representative. 
To do the next filter, we'll focus on the most important stat in basketball, points. We used the file allNBAmvps.csv, which contains the stats of all MVPs that the NBA has ever had. We found out how many points are the least you can score in order to win MVP. Not only that, but took that number as a minimum (and that's being generous, since the pace of the game is much quicker now and more points are scored in every game).
Our last filtering needed to be a little more sophisticated. That is the way we used PER, which stands for Player Efficiency Rating. The Player Efficiency Rating (PER) is a per-minute rating developed by ESPN.com columnist John Hollinger. In John's words, “The PER sums up all a player's positive accomplishments, subtracts the negative accomplishments, and returns a per-minute rating of a player's performance.” So after filtering all the players, we only kept the top 25 players in this statistic (that also passed the last filters). So we had our 25 main candidates for the MVP. 
There's always been a lot of controversy regarding this trophy, and that is, apart from other reasons, because the NBA has never given a precise definition of what it stands for. We know the meaning is Most Valuable Player, however, the voters throughout the history have voted following one of these 4 definitions:
1.	**The best player:** lots of people vote who they believe is the best player in the organization, however, this would mean Michael Jordan should have like 10 MVPs.
2.	**The most outstanding player:** some MVP have been awarded to players who've achieved incredible statistical feats never seen before. Like Russell Westbrook's triple double season.
3.	**Best player on best team:** other people just vote the greatest players of the better performing teams.
4.	**Most valuable to his team:** which reward great players surrounded by bad teammates. We'll try to come up with a formula that takes into account all 4.
So to try to be as objective as possible, we came up with a formula for every definition, so we could see, for every definition, who should have won the MVP.
Since for the formulas we used another dataset, we again faced the problem that there were players with very few minutes played (2 minutes), but they had the best stats. So we again filtered the players who had played at least 100 minutes. That would enable us to compare and visualize not only our top 25 candidates but also the whole league.
After doing the corresponding computations and applying the formulas, we finally got the results. For three of the four definitions, Nikola Jokić won the MVP: 
The MVP according to the first definition (best player): Nikola Jokić
The MVP according to the second definition (most outstanding): Nikola Jokić
The MVP according to the third definition (best player in best team): Giannis Antetokounmpo
The MVP according to the fourth definition (most valuable to his team): Nikola Jokić


Then, we wanted to visualize the data of the top 25 candidates, and we came up with a 4d plot where each dimension referred to a definition of the MVP. In the plot, the most up and right the player is, the better he deserved the MVP, and we can see Nikola Jokić on the top of there. 

We know that a 4D plot may be a little confusing to understand, so we reduced the dimensionality, so it is more readable. The further to the right and to the top, the more likely he should be to winning the MVP (being to the right is more important than being to the top).
For a further approach to the results, we computed the total MVP points taking into account the 4 definitions, and guess what, once again Nikola Jokic took the lead with Embiid and Giannis trailing just behind. Which makes sense if we compare it to the previous 2D plot since they were clearly the ones more to the right top corner. 



As we were supposed to use everything we did in class, we also created a histogram and a scatter plot for better visualization and comparing things more easily. Which served as proved that the top 25 candidates we picked were also the best performing players in the league.

Of course, this approximation isn't 100% accurate and we might be overlooking some things. One thing that we cannot get in numbers is the leadership of a player, and limiting defence to stats like steals or blocks doesn't paint the whole picture. However, the results we obtained make a lot of sense and are really close to the opinions of professional critics, which is an indicator of a great job.
Also, by looking at the final results, we see that really giving the award to Embiid isn't a crazy thing to do. It's true that his game might depend too much on free throws, and he has another superstar calibre player on his team, like it's also true that stats really make Jokić look like a better defender than he actually is.
Another thing we see when we look at the data frame of the whole league (without including players who barely played), are some names who didn't make it into the top 25 for several reasons. These could be injuries like Zion Williamson, or not scoring enough, like Robert Williams. This is an indicator of how well they played even though they realistically didn't have a chance to be the MVPs.
Comparing to previous MVPs
Now we wanted to compare the real MVP, Joel Embiid, and our MVP, Nikola Jokić, with the past MVP’s. So we took a data set where there is information of all the MVP’s in the history of the NBA. 
Firstly, we had to add Nikola Jokić since he is not in the list. Also, we removed all the MVPs previous to the 1973-74 season, since there weren’t enough statistics for us to accurately use them in any comparison.
So once again, we applied our 4 formulas (this time fairly modified since we don’t have enough stats available now) to every MVP in history to compare them. Note that we avoided our 3rd formula for the 3rd definition because in the dataset of all MVPs there is no information about the matches won. We thought of using imputation or some other technique learned in class, but it doesn’t make sense since we have 0 information. 
We plotted the data once again (3d) and we applied 2 clusters, which would more or less divide the MVPs into the players that definitely deserved the award and the ones that perhaps shouldn’t have won it.


Afterwards, we obtained the total MVP points and plotted them in a scatter plot as well. Surprisingly, this Nikola Jokić season is the third best of all time MVPs, nevertheless he hasn’t even been awarded this year as MVP. This comes to show that the game is more than statistics and numbers, however, if the award was solely dependent on numbers, we could say that it wasn’t well deserved.
