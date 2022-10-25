---
{"dg-publish":true,"permalink":"/30-interests/analytics/probability-fundamentals-briliant-course/probability-fundamentals-briliant-course/"}
---

[[60 tools/Brilliant|Brilliant]] | [[30 interests/Analytics/Analytics|Analytics]] 

![](https://i.imgur.com/ayQcEWp.png)

## Introduction
- [[30 interests/Analytics/Probability Fundamentals - Briliant Course/Estimating Probabilities|Estimating Probabilities]]
- [[30 interests/Analytics/Probability Fundamentals - Briliant Course/Counting Cases|Counting Cases]]
- [[30 interests/Analytics/Probability Fundamentals - Briliant Course/Common Paradoxes|Common Paradoxes]]
- [[30 interests/Analytics/Probability Fundamentals - Briliant Course/Intro to Simulation|Intro to Simulation]]
## Principles of Probability
- Using Outcomes
- Outcome Distibution
- Complements
- [[30 interests/Analytics/Probability Fundamentals - Briliant Course/Probability as Counting|Probability as Counting]]
- The Rule of Sum
	- P(A or B) = P(A) + P(B) - P(A AND B)
- The Product Rule
	- P(A and B) = P(A) * P(B)
	- For any group of unrelated events, the probability they happen together is the product of their probabilities.
	- If the chance of some scenario happening in *p*, then the probability it happens *n* times independently is $p^n$
		- Example if you toss a coin, the probability to guess the winning side on the first time  is 1/2; two times on the row is 1/4; three times 1/8; 4 times 1/16
- Applying Probability Rules
	- If the events have certain dependency and can't happen in the same time, you sum the probabilities 
		- e.g., flight to be canceled and to be overbooked; these two events are distinct, you can't have a flight that is canceled and overbooked
	- If the events are independent and  can happen in the same time, you multiply the probabilities
		- e.g., one flight can be delayed by wind, second flight can be delayed by traffic; any of these events are independent, so the chance to arrive in time by taking both flights, you need to use the product rule

## Events
-   **Independent events**: The occurrence of one event does not affect the probability of the other event. For example, when flipping a coin, getting “heads” does not change the likelihood of getting “heads” on the next coin flip.
-   **Dependent events**: The occurrence of one event does affect the probability of the other event. For example, if you draw a King from a deck of cards and do not replace it, it causes the probability of drawing another King to decrease.
