---
title: "Get to the Point"
date: 2021-07-17
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
---

<!--more-->

I've always found Piwars points allocation confusing. Every year I've been surprised by how many points my team has got in the competition, despite our best efforts to needlessly try to work it out before the closing ceremony. I think the confusion stems from the apparently simple "formula" points system referred to in the rules (where faster finishes get more points, like in F1). That's simple, right? But if there's only ~5 challenges, and first place gets 50 points, how do some team's scores total more than 6000?!

So this year I decided to really study the rules and understand where the points come from, where we scored well and where we could do better.
Here's what I found out:

This year there were 7 "challenges" where points could be scored: Feed the Fish, Tidy Up the Toys, Up the Garden Path, DIY Obstacle Course, Blogging, Artistic and Technical Merit. Artistic and Technical Merit were in some ways combined in the way the points were allocated and what needed to be submitted for them, but they were judged and ranked seperately, so I'll consider them seperate "challenges".
For some challenges the formula scoring system applies, where you get additional points depending on your ranking in the challenge:
>1st: 150  
>2nd: 120  
>3rd: 95  
>4th: 70  
>5th: 55  
>6th: 45  
>7th: 35  
>8th: 30  
>9th: 25  
>10th: 15  
>11th: 10  
>12th: 5

Let's next pull out the key lines from the rules for each challenge and see what it means for the available points:
#### Feed the Fish
> There are 3 rounds and 5 shots in each round, giving a maximum of 15 shot deliveries.  
> The points per each correct delivery of shot are as follows (and remember, you cannot mix these methods):  
>- Autonomous, shot into the top box – 80 points.  
>- Remote control, shot into the top box – 50 points.  
>- Autonomous, rolled into the bottom box – 50 points.  
>- Remote control, rolled into the bottom box – 30 points.
>
> Rankings, which will be according to the Formula Scoring System, will be awarded according to the number of points scored on the food targeting challenge, split into the four different method/control method combinations.  
> In the event of a tie-break, the robot who manages to complete their 3 x 5 shots in the shorter time will rank higher. In the event of a time-and-points tie-break, the tie will be settled by artistic merit points (see below).  
> Up to 150 Artistic Merit points will be given for the decoration of your Fish Bowl.

So to get maximum points for completing the challenge, you need to attempt it autonomously, into the top box, and get all the shots on target, for 15x80 = 1200points. If you get the most shots on target (or tie on number but get the fastest time), from the formula scoring page that's another 150points. Getting maximum points for your art nets you another 150points, for a total of 1500points being up for grabs for Feed the Fish. Interestingly, only 150 (10%) of those points are for being fastest. Achieving the maximum shots in the time allowed was more likely to score big points than being fast. 

#### Tidy Up the Toys
> For each block successfully placed into the target box, the following points will be awarded:  
>- Remote control, side-by-side – 100 points.  
>- Remote control, stacked – 200 points.  
>- Autonomous, side-by-side – 150 points.  
>- Autonomous, stacked – 300 points.
>
> If all blocks are placed into the correct sequence (as specified above), the following points will be awarded:  
>- Remote control, side-by-side – 100 points.  
>- Remote control, stacked – 350 points.  
>- Autonomous, side-by-side – 250 points.  
>- Autonomous, stacked – 450 points.
>
>Robots will be grouped together according to the four options above and then ranked according to the duration of their recorded run. Points will be awarded to the top ranked robots in each group according to the Formula Scoring System.


So again, the method to get maximum points is attempting it autonomously, where you get 3 x 300 + 450 = 1350 if the blocks are successfully stacked. Finishing fastest gets you another 150points, for a total of 1500 points again. As with Feed the Fish, being fast is only 10% of the points

#### Up the Garden Path
The scoring for this challenge gets more complicated, as there are plenty of permutations possible. The rules say:
> For each of the six elements (marked in red in the above plan) passed by the entire chassis, you will be awarded points, dependent on the method chosen:  
>- Completely remote control – 45 points.  
>- Dead reckoning – 55 points.  
>- Line following using line following sensors – 80 points.  
>- Navigation using a camera – 150 points.  
>- Audio commands only – 150 points.
>
>Additional points for navigating the entire course, depending on the method chosen are as follows:  
>- Completely remote control – 50 points.  
>- Dead reckoning – 75 points.  
>- Line following using line following sensors – 100 points.  
>- Navigation using a camera – 200 points.  
>- Audio commands only – 450 points.
>
> If you use audio commands together with either the Line following method or Camera method, you will gain an additional 250 points. You must use at least three audio commands to score these points.

So audio only navigation or camera plus audio can both potentially score the same, and successfuly completing the entire course nets you:  6 * 150 + 200 + 250  = 1350. And again, there's 150 extra points for doing that fastest, for a maximum score of 1500. 

#### DIY Obstacle Course
This is judged in different categories:
>- How imaginitive your obstacle course is – out of 100 points.  
>- The complexity of your obstacle course – out of 200 points.  
>- The amount of humour on display – out of 300 points.  
>- The agility of your robot – out of 200 points.  
>- For remote control robots – the skill of the driver – out of 200 points.  
>- For autonomous robots – the accuracy and maneuverability of the robot – out of 300 points.  
>
> Fully autonomous robots will be awarded a bonus of 400 points.  
> For remote-controlled robots, if audio commands are used as well, a bonus of 150 points will be awarded.

Again, a fully autonomous entry could score 100 + 200 + 300 + 200 + 300 + 400 = 1500 points, same as the other challenges.

#### Blogging
>Points will be awarded by an expert judge out of a maximum of 30. Only one team can be awarded the maximum points but below the maximum, some teams may receive the same points as another. Scores will be multiplied to give a maximum acquired total of 1500 points.

The guidance suggests the criteria used is "the information", "the look", "the feel" and "the ongoing story", but nothing more about how the points are assigned. 


#### Technical and Artistic Merit
The maximum scores available for the Technical Merit and Artistic Merit challenges are 750 points each, giving a total of 1500 


so, in summary:
| Challenge | Ranking points | Bonus points | Assessed points | Total Points |
|:--|:---:|:--:|:---:|:---:|
| Feed the Fish | 150 | 1200 | 150 |1500|
| Tidy Up the Toys | 150 | 1350 | 0 |1500|
| Up the Garden Path | 150 | 1350 | 0 |1500|
| DIY Obstacle Course | 0 | 400 | 1100 |1500|
| Blogging | 0 | 0 | 1500 |1500|
| Artistic | 0 | 0 | 750 |750|
| Technical Merit |  0 | 0 | 750 |750|

For a total of 9000points.
It's clear from this analysis that outright speed is worth very little points (5%), provided the robot is fast enough and reliable enough to complete the challenges within the time limit. The majority of the points this year were "bonus points" for completing the challenge in a prescribed way, with the next biggest chunk coming from the assessed categories of blogging, artistic and technical merit. Looking back at previous years, the points structure has been reasonably consistently weighted like this, with only minor tweaks in recent years.

By analysing how the top three advanced teams did this year, we can see where our performance is most lacking. We know how the different teams attempted each challenge, so the bonus points can be worked out. We also know the ranking positions, so those points can be assigned. For the entirely assessed chalelgnes, we only know the ranking order, so we'll have to make up some scores that are consistent with the positions and give the correct overall score. here

| |	||**Tauradigm** (3rd)|		||	|**Chameleon** (2nd)|		||	|**Pidrogen** (1st)|  |		
|:--|:-:|:---:|:--:|:---:|:---:|:-:|:---:|:--:|:-:|:---:|:---:|:---:|
|Challenge	 ||	Ranking points | Bonus points |	Assessed points	 || Ranking points	 |	Bonus points	 |	Assessed points	 ||	Ranking points |Bonus points | Assessed points |
|Feed the fish || 95 | 650 | 100 || 150 | 1200 | 100 || 120 | 1120 | 100|
|Tidy the toys || 150 | 1350  | || 120 | 1350  | ||	70 |	1350	 | |
|Up the garden path || 120 | 1350  || | 150 | 1350 ||  | 95 | 1350| | 	
|Obstacle course ||  |  | 700 | ||  |  1000 || |  | 	950|
|Blogging ||  |  | 587.5 |  ||  | 170|| |  | 667|
|Artistic ||  |  | 230  |  || | 515  ||  | | 300|
|Technical ||  |  | 750  ||  | | 515  ||  | | 600|
|Subtotals|| 365 | 3350 | 2367.5 || 420 | 3900 | 2300|| 285 | 3820 | 2617|	
|% of max possible|| 81% | 86% | 51% || 93% | 100% | 49%|| 63% | 98% | 56% |	
|**Total**	 || | 	**6082.5** | ||	 | **6620** |  || |  **6722** | | 	

Compared to first and second, we scored about average on the ranking points. As expected, its not making much of a difference. We gave up quite a few bonus points by not doing Feed the Fish autonomously, that lost us ~500points. Despite that, this is the category where the bulk of our (and the other team's) points came from. A slow but accurate autonomous Feed the Fish run that got all the balls in the bowl would have just nudged us into 2nd place. In the assessed challenges, we again scored fairly average compared to the other competitors, but it's clear we're all giving up about half the available points. A good score rather than our poor-to-average score in the obstacle course, blogging or artistic challenges could have been enough to move us up to first place. So plenty of areas and scope for improvement!

We're going to be doing the same analysis for the Disaster Zone challenges, assuming the points allocation remains much the same for 2022 as it was intended to be for 2020.