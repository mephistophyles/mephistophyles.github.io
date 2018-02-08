---
layout: post
title: Risky Business
blog_group: blog
--

Growing up, Risk was the go-to game in our family to play on cold winter days. We had the house rule that the attacker had to roll first, and the defending player could then choose how many dice he wanted to roll. Normally, the two roll at the same time. We also had the house rule that a defender could roll with up to three dice, just like the attacker.

Curiosity propelled me to investigate how much of an advantage this gave the defender. So I built a Monte Carlo simulation, with corresponding web app [here](https://cryptic-peak-47052.herokuapp.com/), to investigate the outcome of various army situations (assuming the attacker doesn't elect to abort sometime before he reaches 1 army).

The essence of the situation boils down to random dice being rolled, the highest rolls are compared between players and the rest discarded. If the defender rolls higher or equal to the attacking player, the defender wins and the attacker loses an army. Likewise if the attacker's die is higher than the defender, the defender loses an army. Attacker can roll up to three dice and has to have at least 2 armies in a territory to be allowed to attack (if you're successful, you need 1 army to remain and 1 army to take over the new territory).

### Simulation

So our Monte Carlo situation basically is a comparison of dice rolls. We know each number has a probability of 1/6 of being the result of a roll. So a simply 1 vs 1 roll would lead to (1+2+3+4+5+6)/(6^2) probability of the defender winning; 21 out of ever 36 rolls. This makes intuitive sense, since the defender wins any draws they have a slight advantage. Running our simulation 10000 times leads to 5860 losses for the attacker. Since 21/36 is approximately 5833/10000, our simulation seems to be in the right neighborhood.

We can extend this reasoning and calculate the odds of wins and losses for every possibly circumstance. But what I find more interesting is possible outcomes. Frequently in the game, you won't attack just once, but will like to chain together successful assaults to amass larger territories. So knowing not just how likely you are to win this attack, but how many armies you will have left once you do win, is very important.

### The 3 Crucial Defenders

[!Result distributions of 10 armies attacking 3 defenders 10000 times]({{site.url}}/images/risk/10vs3sim10k.png)

Above is an image resulting from 9 armies attacking (ie the territory has 10) 3 defenders 10000 times. The simulation was run several times and the pattern remains; most likely outcome would be to lose all your attacking armies and the second most likely outcome is to not lose any!

The key to understanding this lays in the critical number of defenders. The initial advantage of winning tied matchups is lost as soon as one army is lost. As soon as the defender is reduced to rolling two dice and the attacker can still roll 3, the defender's advantage is gone and is quickly overwhelmed. 

Looking at the situation where an attacker has 3 dice and the defender only has 2 (and borrowing the math from [here](https://web.stanford.edu/~guertin/risk.notes.html)) we can see the defender loses 2 armies approximately 37% of the time (2890/7776) and loses 1 army over 33% of the time (2611/7776). Meaning the attacker comes out ahead 70% of the time, assuming they don't mind losing a few armies to get to that point. 

This rule of thumb to remember (3 defenders is beatable, because 2 is VERY beatable) seems to hold true, because when we simulate the same situation with 4 defenders instead of 3, the success chances looks very different.

[!Result distributions of 10 armies attacking 4 defenders 10000 times]({{site.url}}/images/risk/10vs4sim10k.png)

Now it shows that the odds of success have decreased dramatically, especially those of winning without incurring a loss.

### Scaling 

What is interesting to note is that the distribution of results doesn't change a ton once the attacker has more armies. Below is the outcome of running the simulation with 100 attacking armies vs 90 defenders. 

[!Result distributions of 100 armies attacking 90 defenders 10000 times]({{site.url}}/images/risk/100vs90sim10k.png)

And below is the same 100 armies attacking 30 defenders. 

[!Result distributions of 100 armies attacking 30 defenders 10000 times]({{site.url}}/images/risk/100vs30sim10k.png)

Clearly a win is a win. Once you have a superior number of armies, then it doesn't matter a great deal whether your opponent has 30% or 90% of your force, victory seems almost assured.

### House Rules

The defensive strategy was boiled down to the following rule:

 * If the attacker doesn't roll anything higher than a 3, roll the max amount of allowed dice
 * If the attacker doesn't roll anything less than a 4, roll the min amount of allowed dice.
 * Else, split the difference, roll 2 if possible, otherwise just the 1.

I expect the conservatie strategy as such to result in a more favorable result for the defense. Yet nothing could be further from the truth:

[!Result distributions of 100 armies attacking 30 defenders 10000 times with house rules]({{site.url}}/images/risk/100vs30sim10khouse.png)

[!Result distributions of 100 armies attacking 90 defenders 10000 times with house rules]({{site.url}}/images/risk/100vs90sim10khouse.png)

The above graphs show the results of 100 armies attacking 30 and 90 defenders respectively. They are nearly identical to the above results (only a mild shift of the peak to the left). So our house strategy is indeed better, but minimally.

### Explaining Results

The reason the house rules here are only marginally better than both players throwing their max allowed dice is not because of poor human intuition, but rather poorly translating this intuition into hard rules. 

Naturally in a situation where the attacker rolls a 6-1-1, the defender would be best suited to rolling 3 dice as well, but in the above scenario they only roll 2. Similar attempts at creating more complex rules to handle the different scenarios have proven unable to change the initial results by much more than a minimal degree.
