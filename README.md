# DirectStrikeGoldMineProject
An overview of goldmine timings

For Context of the game
https://directstrike.org/guide/overview

This project seeks to counter the meta narrative that players should stay on one gold mine throughtout most of the game, going only to 2 goldmines at 10 minutes, and 3 gold mines at the very late stages of the game (20 mins+).

# Overview
The main file Direct Strike Project.ipynb consists of a real time gold simulation of the game. It simulates the base gold income (100g/20secs), with the ability to build mines(by typing 'mine') at the user's request. It follows the goldmine linear cost and cooldown (90 seconds) from the base game. After a 35 minute timer goes off or whenever the user types 'quit' the simulation stops. Total gold accumulation for every second in the game, as well as a mine counter are saved to the gold_progress.csv. New runs will be appended to gold_progress.csv.
NOTE: to save the results the user must type 'quit'.

Direct Strike Project.ipynb contains 5 scripts. In the first script mine creation is purely user controlled.
Script 2 automatically adds a mine at the beginning of the game (as most players do).
Script 3 follows Script 2, but also auto builds a 2nd mine at 3 mins.
Script 4 autobuilds a third mine at 5 mins.
Script 5 autobuilds a fourth mine at 7.5 mins.

GMS according to guide.ipynb instead uses the logic provided by the official direct strike guide. It autobuilds a mine at the beginning of the game, a 2nd mine at 8-12 mins (averaged to 10 mins), and a third mine at the 20 min mark, never building a 4th mine.

After reviewing gold advantages in Gold Visualization and Analysis.ipynb I found that the 4 gold mine approach broke even and gained a gold advantadge after 13.3min with the 1 mine approach, after 15.24mins with the 2 mine approach, and after 17.3 mins with the 3 gold mine approach.

![newplot](https://github.com/user-attachments/assets/053da364-b5e7-4624-a6b3-c40560cbb705)




# Comparisons to the DS guide
Comparing these home cooked mine timings to the guide script provides an even more stark difference. 

The 2 mine approach is only behind in gold to the guide from minute 3 to minute 10. It maintains a static 205g lead from the 10 minutes to 20 minutes, with the lead jumping up to 450g once the guide creates it 3rd mine at 20 minutes. After the guide creates its 3rd goldmine, it will only break even at the 34.3 minute mark.

![newplot(2)](https://github.com/user-attachments/assets/02d8b0f3-7642-4c20-bda0-e042b3468abb)


The 3 mine approach compared to the guide is only behind in gold up to the 10 min mark. After the guide creates its 10 minute 2nd mine, the 3mine script immediately gains a 105g lead which increases up to 400g at 20mins. Finally the gold increases to 650, and remains static at 20 minutes, after the guide creates its 3rd mine. In other words the 3 mine approach will always be at a 650 gold lead after 20 minutes, without taking into account mid bonuses.

![newplot(3)](https://github.com/user-attachments/assets/403be302-2207-49bb-90d4-88c1ef2f40ab)


The 4 mine approach remains behind in gold to the guide until minute 12, its lowest gold difference being -540gold at the 7:30 minute mark. At the 20 minute mark however (just before the guide builds its third mine), the 4 mine approach has amassed a 480 gold lead, sharply increasing to 730g when the guide builds its 3rd gold mine. This lead increaes linearly for the rest of the game, reaching upwards of 1000g at 30 minute games. 

![newplot(4)](https://github.com/user-attachments/assets/8421690f-583f-482b-ac2e-8bfba791a4a5)

# Approximation of the middle bonus

To simulate the middle control gold income I created new versions of each program which add a handicap variable to the gold multiplier. The guide version gained a .4 gold/sec increase to its gold income during the periods at which it had a gold advantadge. This is to simulate the guide controlling the middle 80% of the time at those periods. A respective .1 gold/sec advantadge was granted to its competitors to account for middle control rest 20% of the time.

At the break even points the handicap value was equalized to .25gold/sec to each side. 

# New Comparisons after the addition of middle bonus gold
 2 Mine Approach: With the introduction of the middle bonus gold 2 mines quickly become non viable, as the early loss in total gold (-240 at 3 minutes) does not provide a flat gold advantadge as it did before (50 - 25 g advantadge from 10 to 20 minutes). However when the guide builds its 3rd mine at the 20 minute point the gold advantadge quickly shoots up to 275g, while slowly dissipating and finally going negative at the 29 minute mark. This means you are at a 2 footman disadvantadge during the early game, equalizing later, and being at most a destroyer worth of gold at the 20 minute mark, whilke lead slowly decreases over time. The early investment never seems to pay off.

![newplot(5)](https://github.com/user-attachments/assets/eb23a08c-b777-43ef-b38f-475f9de2948d)

3 Mine Approach: My Favorite approach so far. While you reach a negative gold difference at the 5 minute mark of 460g (4 footmen), this difference only disappears over time, becoming even at 12:51 seconds. At the 20 minute mark you go from a 213g advantadge to a static advantadge of 464g for the rest of the game, as the guide creates its 3rd mine. In other words at 20 mins you will always be on average a mountain giant+footman ahead of your opponent.

![newplot(6)](https://github.com/user-attachments/assets/640c074e-c621-4a68-9b02-15b7843a6bd3)


4 Mine Approach: The most controversial approach. At the cost of being 660g behind at the 7:30 minute mark and finally breaking even 15:15 minutes, you will have 4 gold mines. At 20 minutes however your lead will increase from 283g to 535g once the guide builds its 3rd gold mine, while only expanding and reaching gold leads of 1000g+ at the 35 minute mark.

![newplot(7)](https://github.com/user-attachments/assets/bb3cc64d-6476-4192-a998-2eb7f133f298)

# Results and other data

After downloading Direct Strike game length data through the W3Champions website api we find that these stats:

🎮 GM_DS Game Duration Stats:

• Average: 1643.24 seconds (27.39 minutes)

• Median: 1560 seconds (26.00 minutes)

• Mode: 1350 seconds (22.50 minutes)

📊 GM_DS Game Duration Percentiles:

• 5th percentile: 1050 seconds (17.50 minutes)

• 10th percentile: 1140 seconds (19.00 minutes)

• 25th percentile: 1320 seconds (22.00 minutes)

• 50th percentile: 1560 seconds (26.00 minutes)

• 75th percentile: 1890 seconds (31.50 minutes)

• 90th percentile: 2280 seconds (38.00 minutes)

• 95th percentile: 2520 seconds (42.00 minutes)

![newplot(8)](https://github.com/user-attachments/assets/0e69f8e3-2b33-4dea-8bec-34755815de0f)

(You can also see this graph in https://w3champions.com/OverallStatistics/)

With less that 5% of games ending before 17 and a half minutes it seems a no brainer to invest early into 3 and even 4 gold mines, as the latest at which you will be even in gold witll be 13 and 16 minutes respectively. While in the median game lngth of 26 minutes you will be ahead by 460 gold and 715 gold respectively. With the 715g value only increasing as the game goes on.

# IN CONCLUSION: BUILD YOUR MINES EARLY. IN 95% OF CASES YOU WILL NOT LOSE BEFORE 18 MINUTES.
In most cases you can manage to build your 2nd mine at the 3 to 3:30 minute mark, and your third at the 5:30 minute mark. With your 4th mine at the 7:30 minute mark

# Limitations of the Simulations

Since the middle bonus gold is so chaotic, it's almost impossible to quantify. The game state depends on more than simple gold advantadges, and unit counters may be more important than just gold. The early gold advantadge the guide received (middle income 80% of the time) may be greater, or smaller. I picked 80% as an arbitrary number. If you wish to run your own tests with different handicaps you can download the scripts and edit them yourself.

I do not know how to quantify the 150g bonus from tower destruction. Adding that bonus creates another step of complexity that will only obfuscate the results of the simulation. If you have a good idea on how to implement it however, please reach out.

This assumes that both players are of equal skill.

THe simulation does not take into account tech or hero timings. You can get away with creating a hero before the 3 minute 2nd mine 90% of the times from anecdotal experience. 

FInally, if this statrategy becomes popular the average game length will surely go down if the opposite team scouts you and takes advantadge of your timings. As the game stands (5/16/25) less than 5% of games end before 17:30 mnutes. This could increase as this strategy gains popularity. 

Be sure to communicate your plans to your team.

















