# DOTA2Analysis
An analysis of different factors that affect the meta in DOTA 2 updates and patches

Dota 2 is a popular multiplayer online game developed by Valve that pits two teams of five players each.  Each player picks one character, or hero, (two players can’t play the same character, regardless of team) from a pool of 110+ characters with the goal of destroying the opposing team’s base.

This analysis is to be able to identify and analyze the changing game metas and be able to provide a framework to inform designers on what subsequent updates need to focus on.

One of the things that influence game updates the most, in a MOBA such as DOTA 2 is…
**Game META**

## What is a META?
The metagame (also called the meta) is the current trend that is often considered to be the optimal way to play the game by the community. 
This always changes over time, and is driven by community opinion, professional players, and balance patches.

## What are some of the important QUESTIONS for a designer when it comes to the game meta?
* How often do we need to help shift the meta?
* Is the game getting stale for our player base?
* Can we think of introducing a new element in the game that will have effects in the meta?
* A new hero, perhaps?
* Can we modify the existing elements of the core game mechanics (excluding those concerning monetization) that will cause a shift in the meta?
* Is the current and most popularly chased meta something desirable from a game functionality perspective?

## How can we CLASSIFY each major game update?
* Map changes
* Item additions or changes
* Hero Rebalances
* New Hero addition
* Game mechanics changes
* Rubber banding / anti rubber banding
* Counter balances to major patches (Minor updates usually)
* Bug Fixes (Minor updates usually)

## So, what VARIABLES can encapsulate the response of the designer’s questions?

* Game characteristics
  * Rubber banding (rate of matches with comebacks)
  * Increase in hero synergies, win rates, etc.
  * Increase in item usage
  * Increase or Decrease of heroes played in Captain’s mode*
  * Increase or Decrease of heroes (not available in Captain’s mode) being played in other modes*
  
* Player engagement
 * Number of concurrent players
 * Rate of playing matches
 * Number of online vs # of offline matches
 
* Update characteristics
 * Gap between the last update
 * Previous Patch type

* Bug reports
 * NLP Search machine on Reddit maybe?*

## Let’s take a look at the individual variables!

### What DATA are we using?
* Source of data – Kaggle dataset on Dota 2 matches (https://www.kaggle.com/devinanzelmo/dota-2-matches) provided by opendota.com, a stat tracking website for Dota 2 players.
* I used mainly players.csv, match.csv, and hero_names.csv, which total to 89 attributes.  To get the data into a useful form for this project, I had to stitch together several of the provided spreadsheets and clean up values.  I was able to toss out 35 games that were missing data and 7,745 games that involved players leaving the game.  A player leaving significantly alters the course of the game and it wouldn’t be proper to include those in this analysis.  This leaves 42,220 games that include information about 211,100 hero picks and win rates.

### The HERO Equation
The sheer number of heroes in the game, combined with how unique each one is, makes for there to be synergies and combinations that are more successful than others. This causes it is extremely difficult for even professional players to navigate the hero picking process leading to a victory. 

From Figure 2., we can see that there is a significant difference in picks across the cast of heroes. The general tendency for people would think that successful heroes are picked more often. It’s easy to jump to the conclusion that Windranger and Shadow Fiend must have very high win rates and that Chen and Elder Titan have very low win rates. This would be a hasty and erroneous conclusion. In Figure 3, we add a secondary axis to show each hero’s win rate, a dotted red line to show the 50% mark, and lower the alpha of the bars to make the points easier to see.

> __*Figure 2: Frequency of Hero Picks*__
![Frequency of Hero Picks](https://github.com/ajaypt92/DOTA2Analysis/blob/master/Visualizations/Fig2.png)

> __*Figure 3: Frequency of Hero Picks*__
![Frequency of Hero Picks](https://github.com/ajaypt92/DOTA2Analysis/blob/master/Visualizations/Fig3.png)

Figure 3 makes it much easier to see how assumptions about the relationship between pick rate and win rate aren’t straight forward.  In the top 12 most picked heroes, there is an even 6-6 split between being in the top or bottom half of win rate.  On the other hand, for 12 least picked heroes, 8 have win rates less than 50%. Later on we’ll see that this isn’t even a great measure of hero performance.  Dota 2 is first and foremost a team game.  An individual hero’s performance isn’t a good measure because we need to see and understand how heroes interact with each other. If you’re starting a pickup game of basketball and have a whole bunch of people to pick from, you don’t want to pick 5 people that primarily want to play point. You need to form a balanced team of people that play well together and compliment each other. The same concept is true for Dota 2.

> __*Figure 4: Occurance of Hero Pairings Compared to Median*__
![Occurance of Hero Pairings Compared to Median](https://github.com/ajaypt92/DOTA2Analysis/blob/master/Visualizations/Fig4.png)

To try to uncover hero synergies and hero utility, or how well a hero plays with others, I generated all unique permutations of 2 hero pairs for each team and made a set of visualizations that pair the heroes together.  For example, a 3 person team of ABC would lead to the following permutations: AB, AC, BC.  Why focus on hero pairs?  Team based games are generally the most fun when you play with friends.  The goal with looking at hero pairs is to establish a form for a player to determine how to pick a hero that is likely to be successful with a friend who has picked a hero.  Figure 4 aims to really bring out common pairings by comparing them against the median pick rate (for reference, the median pick rate for hero pairs was 78).  Note: The empty spaces are hero id’s that were not used at the time of the data collection.  For example, Earthshaker and Shadowfiend are paired together roughly 20 times more than the median pick rate.  The color scale lets us see streaks of common pick rates.  If you look at Windranger’s X and Y axes, you’ll see that they’re significantly lighter than the other squares.  This is a reflection of just how much higher her pick rate is compared to other heroes.  If we use the same graph type and chart win rates rather than pick rates, then we can see how successful hero pairs are together.

> __*Figure 5: Win Rate of Hero Pairs*__
![Win Rate of Hero Pairs](https://github.com/ajaypt92/DOTA2Analysis/blob/master/Visualizations/Fig5.png)

Here, in Figure 5, we chart the win rate of hero pairs.  Successful pairs are more yellow and unsuccessful pairs are more blue.  You’ll see some black speckles around (ex. Jakiro & Oracle, Omniknight & Elder Titan, Chen & Sandking | Warlock | Enigma).  These are all heroes that were played together a single time in the data set.  At the time this data was collected, there were 110 playable heroes.  This means that there are 5,995 unique 2-pair combinations of those heroes (the formula for unique 2-pair permutations is n(n-1)/2). It’s pretty notable that some of these combinations weren’t picked at all, when you consider that a single game will have 20 unique hero pairs. Similar to the black spots, the bright yellow spots are of particular interest.  If you remember from earlier, Chen had a very low overall pick rate and his axes for the pick per median are practically dark, but here he has 5 bright yellow spots to indicate a fantastic win rate.  This is because I didn’t discriminate these tables by numbers of picks.  This leads Chen has a 100% win rate with Outworld Devourer, Enchantress, Oracle, Elder Titan, and Techies although all of these pairing combined only amount to 16 co-occurrences.

Another way to visualize hero pairs is by chord diagram.  Figure 6 is an unlabeled chord diagram showing every hero pair from the data set.  Now, this particular diagram isn’t useful due to the sheer number of hero pairs available, but if we start setting rules for it, patterns will start to emerge.

> __*Figure 6: A chord diagram of all Hero pairs*__
![A chord diagram of all Hero pairs](https://github.com/ajaypt92/DOTA2Analysis/blob/master/Visualizations/Fig6.png)
