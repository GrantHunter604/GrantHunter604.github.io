# College Football Adjusted Ratings
College Football Adjusted Ratings is an attempt at creating a ranking system similar to KenPom's college basketball adjusted ratings, but for football. 
The ratings produced by our model displays how many points better or worse a team is compared to a perfectly average team for that season. So for example, if 
a team were to have an adjusted efficiency margin (AdjEM) of 35.12, that means that if this hypothetical team were to play a perfectly average team 
(with an AdjEM of 0.00) this team is expected to win by 35.12 points on a neutral field. 

The ratings produced by this system are adjusted for opponents and are
predictive. We are attempting to predict how well a team would fare against a perfectly average team. We are not attempting to rank teams based off of resume, 
the eye test, or any other metric. Due to the nature of college football, there are not enough datapoints to build our model off of early in the season. Our model
will not produce "accurate" ratings until there are enough games to build our model off of, which tends to be around week 6.

Website: https://collegefootballadjustedratings.github.io/

## Methodology
The methodology behind the rating system is simple. We take the results of all games played between FBS teams and attempt to produce a system of linear 
equations that most accurately predicts all final scores of the games played (most accurately according to least squares regression). We predict the final 
score of a game using the formulas:

*homeTeamScore = homeTeamOffense + awayTeamDefense + averageFbsPointsScored + 0.5 * homeFieldAdvantage* <br/>
*awayTeamScore = awayTeamOffense + homeTeamDefense + averageFbsPointsScored - 0.5 * homeFieldAdvantage*

## Example
Using the 2013 Michigan @ Michigan State game as an example, the average FBS points scored in a game in 2013 was 28.42 and home field advantage was 3.10. Michigan 
had an adjusted offensive rating of 6.95 for the year and a defensive rating of -1.61. Michigan State in 2013 had an adjusted offensive rating of 0.58 and defensive 
rating of -16.11. Plugging the numbers into the formulas, we would have Michigan State beating Michigan by a score of 29 - 18:

*michiganStateScore = 0.58 + -1.61 + 28.42 + 0.5 * 3.10* <br/>
*michiganScore = 6.95 + -16.11 + 28.42 - 0.5 * 3.10*
