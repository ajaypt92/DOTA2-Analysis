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

From Figure 2., we can see that there is a significant difference in picks across the cast of heroes.  The general tendency for people would think that successful heroes are picked more often.  It’s easy to jump to the conclusion that Windranger and Shadow Fiend must have very high win rates and that Chen and Elder Titan have very low win rates. This would be a hasty and erroneous conclusion.  In Figure 3, we add a secondary axis to show each hero’s win rate, a dotted red line to show the 50% mark, and lower the alpha of the bars to make the points easier to see.

*Figure 2*
![Frequency of Hero Picks](https://github.com/ajaypt92/DOTA2Analysis/blob/master/Visualizations/Fig2.png)

