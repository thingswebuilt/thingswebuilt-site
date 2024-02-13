---
title: "Zombie Points"
date: 2023-12-04T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Maths
---

# Unraveling the Zombie Apocalypse: A Mathematical Approach to Pi Wars Strategy
In the world of Pi Wars, the Zombie Apocalypse challenge stands out not only for its thematic allure but also for the strategic depth it offers to participants. Recently, an intriguing aspect of this challenge caught our attention—the scoring system. Through a detailed mathematical analysis, we've uncovered insights that could significantly influence strategy, particularly concerning the distribution of targets across the "Pi Wars Tower."

## Initial Observations:
The original scoring system offered points based on target location within the compound, with an escalating reward for targets positioned on higher floors. Additionally, a substantial bonus and points for autonomous operation seemed to skew potential scores towards unprecedented heights. Our curiosity piqued, we delved into the numbers to decipher the implications.

### Original Scoring Scheme for Autonomous Robots
* 40 points will be awarded for each target in the “car park”.
* 70 points will be awarded for each ground floor target.
* 90 points will be awarded for each middle floor target.
* 120 points will be award for each top floor target.  
An additional 140 points will be awarded if all 5 shots hit their target, regardless of which floor the target is on.  
An additional 200 points will be awarded to robots that run completely autonomously with their own firing mechanism (i.e. not using the supplied balls).  

## Mathematical Analysis:
Using the scoring data, we calculated the maximum achievable scores under different scenarios. Our initial findings suggested that with five targets on the top floor per round, a team could amass up to 2420 points—a figure vastly exceeding the typical range for other challenges. This discrepancy led to a reconsideration of target distribution and the bonus points' application. We reasoned that for the total points to be comparable with other challenges, there could only be two targets in the whole building, which seemed unlikely to be how the challenge was intended to be run. 

## Revised Scoring and New Calculations:
Following a dialogue with the organizers, the scoring system was updated, leading to a more balanced distribution of points across different target locations. Our recalculations, adapted to the new structure, hinted at a strategic layout with fewer targets per floor than initially assumed, especially on the higher (and higher-scoring) levels.

## Formulaic Breakdown:
To illustrate, let's consider the formula for calculating the maximum potential score with the updated points system:

### Scoring Scheme for Autonomous Robots
* 30 points will be awarded for each target in the “car park”.
* 40 points will be awarded for each ground floor target.
* 60 points will be awarded for each middle floor target.
* 90 points will be award for each top floor target.  
An additional 140 points will be awarded if all 5 shots hit their target, regardless of which floor the target is on. This can apply a maximum of 3 times.  
An additional 200 points will be awarded to robots that run completely autonomously with their own firing mechanism (i.e. not using the supplied balls).  

### Score Calculation
$$ Top\ Floor\ Points\ per\ round\ (TopFloorPts) = Top\ Floor\ Targets * Points\ per\ Top\ Floor\ Target $$
$$ Middle\ Floor\ Points\ per\ round (MiddleFloorPts) = Middle\ Floor\ Targets * Points\ per\ Middle\ Floor\ Target $$
$$ Ground\ Floor\ Points\ per\ round (GroundFloorPts) = Ground\ Floor\ Targets * Points\ per\ Ground\ Floor\ Target $$
$$ Compound\ Points\ per\ round (CompoundPts) = Compound\ Targets * Points\ per\ Compound\ Target\ $$

$$ Max Score = Rounds * (TopFloorPts + MiddleFloorPts + GroundFloorPts + CompoundPts + Round Bonus) + Autonomous Bonus $$

Applying the new points values and hypothesizing about the distribution of targets, we arrive at two probable scenarios for target placement:

Two Targets on Each Floor:

$$ 3 * (2 * 90 + 2 * 60 + 1 * 40 + 140) + 200 = 1640 points $$
One Target on the Top Floor and Two on Others:

$$ 3 * (1 * 90 + 2 * 60 + 2 * 40 + 140) + 200 = 1490 points $$
These calculations suggest a strategic emphasis on targeting multiple floors to maximize scores, aligning closely with the competitive spirit of Pi Wars.

## Strategic Insights:
The power of mathematics has enabled us to deduce likely scenarios for the Zombie Apocalypse challenge, emphasizing the importance of precision and adaptability in strategy. It appears aiming for targets across multiple floors, rather than focusing on quantity alone, will be key to scoring highly in this challenge.

## Conclusion:
This analysis not only showcases the intricate balance of the Zombie Apocalypse scoring system but also highlights the strategic depth embedded within Pi Wars challenges. By embracing a mathematical approach, teams can uncover insights that may not be immediately apparent, guiding their preparations and tactics for the competition.

As we continue to prepare for Pi Wars, let this be a reminder of the value of critical thinking and strategic analysis in robotics competitions and beyond. The adventure of discovery lies not just in the physical engineering of our robots but also in the cerebral challenges we navigate along the way.

!["An image that visually represents a strategic analysis of a robotic competition. The scene includes a detailed illustration of a robot aiming at targets located on different floors of a multi-story building, embodying the concept of precision and strategy. The building, stylized as 'Pi Wars Tower', has windows through which zombies (targets) can be seen. The robot is equipped with a firing mechanism, and mathematical formulas float above, symbolizing the analytical approach to maximizing scores. This imagery should convey the fusion of robotics, strategy, and mathematics in the context of a competition."](PiWarsTowers.jpg "An image that visually represents a strategic analysis of a robotic competition. The scene includes a detailed illustration of a robot aiming at targets located on different floors of a multi-story building, embodying the concept of precision and strategy. The building, stylized as 'Pi Wars Tower', has windows through which zombies (targets) can be seen. The robot is equipped with a firing mechanism, and mathematical formulas float above, symbolizing the analytical approach to maximizing scores. This imagery should convey the fusion of robotics, strategy, and mathematics in the context of a competition.")
