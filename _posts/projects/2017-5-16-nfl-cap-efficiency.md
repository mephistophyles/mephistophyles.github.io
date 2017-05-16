---
layout: post
title: Each NFL team's cap spending efficiency based on position ranking
blog_group: project
---

## Introduction

The goal of this project was to understand how well each team's allocated resources are being spent. Each NFL team has a fixed cap number to spend on the salaries of their players. While in reality the exact cap rules are a bit more complicted (with yearly roll-over, cuts, dead money etc) for the purposes of this analysis we assume that each team has the same yearly budget to spend. In the 2016 season this was $155.27 million, for the 2017 season this has been raised to $167 million.  

## Evaluations

For this initial assessment, the analysis will be broken down into 2 tiers. First each team's offensive and defensive performance will be compared to their relative cap spending in those areas. Second, we will break this down further, taking rankings for quarterback, running backs, wide receivers and offensive lines for the offense, and similarly evaluating the secondaries and the defensive fronts relative to their cap costs. For the position evaluation we will compare the top 5 of each group, showing methodology and sources to allow any interested party to recreate the analysis and perform it on an overlooked team or in another season.

#### Overall Cap Breakdown

In this graph, we can see the overall breakdown for each team's cap spending between offense and defense. The graph is group by division and conference. Of interest is noting that the Cowboys spent $24.7 on Tony Romo at quarterback, but their starter throughout the season, Dak Prescott, only counted for $635848 against the team's cap. This is obviously an extreme anomaly, but paying two quarterbacks a large percentage of the salary cap is not uncommon, highlighting the position's importance.

|![breakdown of cap spending by offense and defense per team]({{site.url}}/images/nfl/offense_defense_breakdown2016.png)|
|---|
|The spending breakdown by team for offense and defense, grouped by division|

Similarly, a cursory overview of each team's spending by position could be instructive.

|![breakdown of cap spending by offensive and defensive position group per team]({{site.url}}/images/nfl/cap_breakdown2016.png)|
|---|
|The spending breakdown by team for offensive and defensive position groups, grouped by division|

We see here a wide variance in each team's cap allocation by position. 

### Offense
The offense as a whole is hard to give a definitive measure to. In this evaluation we will look at yards gained and points scored during the regular season as a measure of offensive ability. We will then compare each offense's performance when scaled by their relative investment in the offense compared to the mean, giving us two rankings. Using the means from the season, we can see that the average team scored 364.4 points over 16 games (for a tidy 22.775 points per game on average), we can also see that the mean yardage was 5606 (for a respectable 350 yards of offense a game).

The following graph shows us how each team has performed offensively in the 2016 season.

|![ratios of yardage and points gained on offense]({{site.url}}/images/nfl/offensive_performance_ratio2016.png)|
|---|
|The ratios of yardage and points gained on offense compared to the league average|

This does show that the two metrics we chose for offensive efficiency do not necessarily go hand in hand. In fact, it can be an indication of a team's inability to convert in the red zone or a measure of a team's true offensive drive efficiency when these two metrics diverge greatly. However, when normalized with what each team spends on offense we see a different trend.

|![ratios of yardage and points gained on offense normalized for cap expenditure]({{site.url}}/images/nfl/offensive_efficiency2016.png)|
|---|
|The ratios of yardage and points gained on offense normalized to offensive cap spending|

We can now see that in terms of point-scoring the Saints are by far the most potent offense. Followed by the Falcons, Seahawks, Bills and Broncos. When looking at yardage the Saint still lead the pack, however the Browns are the second best in that category, surprising considering their 1-15 final record. 

#### Quarterbacks

#### Wide Receivers

#### Running Backs
 
#### Offensive Lines


### Defense
Similar to the offensive statistics, we will use yards and points as the metric, however in this case we will look at the point and yards gained *against* the teams, so lower is better. In order for this to scale properly, we will divide the mean by the team's points and yardage (so a different ratio, where higher is better). So we can again see the correlation with cap expenditure.

|![ratios of yardage and points given up on defense]({{site.url}}/images/nfl/defensive_performance_ratio2016.png)|
|---|
|The ratios of league average to team yardage and points given up on defense|

This indicates the Patriots were by far the best scoring defense. This goes very well with their "bend but don't break" philosophy on defense. 

Now looking at the defensive expenditures per team's performance

|![ratios of yardage and points given up on defense normalized for cap expenditure]({{site.url}}/images/nfl/defensive_efficiency2016.png)|
|---|
|The ratios of yardage and points given up on defense normalized to defensive cap spending|

Again the Patriots seem to rule the roost. With the Lions, Redskins and Panthers showing good performance to compensation figures on both metrics. 

#### Secondaries

#### Defensive Fronts

## Evaluation of Results

All data was pulled from [Overthecap](http://www.overthecap.com), so the validity of these results start and finish with the veracity of this site's reporting. The overall cap numbers were cross-checked with the [Spotrac website](http://www.spotrac.com/nfl/cap/2016/) to ensure nothing too gross was happening. Any addition that doesn't make sense in terms of adding up position groups vs total can probably be attributed to the cost of special teamers. 

Due to the way promising and high-performing rookies are relatively under-paid compared to veterans, they can have a disproportionate impact on a team's ranking. However, since each team has the ability to draft rookies and develop them, as well as the certainty of 'proven' veterans vs the risk of 'unproven' rookies counter balances this disproportionate impact.

Teams are also in various stages of the rebuilding/reloading/contending cycle, which also impacts their cap space and positional rankings. Prime examples of rebuilding are the Browns and 49ers, who after years of poor performance are clearing their rosters of costly veterans and stocking up young (and cheap) players, in the hope that they can develop these players and acquire the spots that are missing in free agency. Similarly looking at the contenders in the last Super Bowl on these rankings show it to be a matchup of not just the highest scoring offense vs the lowest scoring defense, but also two of the teams who effectively manage their cap resources.

However, it is also interesting to see that efficient use of cap space does not always translate to on-field success. Two cases to look at here are the Saints and the Redskins. The Saints were in the bottom of giving up points, despite being fourth in yard efficiency per cap room. Indicating that if you put very little cap resources into a defense, you will give up a lot of points. The Redskins also scored high on the defensive efficacy per cap resource, despite just below average in absolute defensive statistics. On offense both teams performed at the top in terms of yardage and above average in points, but when looking at their financial efficacy, they are mirror images, with the Saints being above all others by a clear margin, but the Redskins solidly in the bottom half.

Another interesting tidbit is how very average the Titans are, hovering around unity in all categories. Where the Packers, Dolphins and Buccaneers are below average defenses and seem to be overpaying for them.

## Future Work

Besides the 'obvious' ability to extend the figures and data into the past to see trends of teams, of particular interest in evaluating the teams' GMs would be the talent identification, acquisition and retention figures. Tracking a GM's draft history and free agent signings would enable the exposition of how often they 'hit' on draft picks as well as signing undrafted free agents and veterans in free agency. Similarly the efficacy of the coaching staff in developing players could be tracked through the amount of players still in the league by the time their initial contracts are up. There is a simbiosis/mutual responsibility here between coaching and GM. Similarly a team's injury history could also be looked at, seeing above average numbers of injuries to players year after year could indicate a problem with the training staff or the way they practice. 