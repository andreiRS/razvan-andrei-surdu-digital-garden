---
{"dg-publish":true,"permalink":"/30-interests/analytics/the-rule-of-five-in-statistics/"}
---

[[30 interests/Analytics/Analytics\|Analytics]]

# The Rule of Five
When needing to approximate the median of a certain population, it **requires only 5 random samples** to identify with **93.75% confidence** that the value is between the smallest and the largest of those samples.

**The Explanation**
The chance to random pick a value that is above the median is 50%, same as flipping a coin. The chance of hitting heads five times in the row is 1/32 or 3.125%. The chance of not to get all heads or tails is 100 - 2 x 3.125 = 93.75

**Varied Amounts** 
How about if we vary the amount of samples?

![](https://i.imgur.com/kGy14DL.png)

```ad-note
title: The Math Behind
collapse: false


// 2 samples
1 - 1/4 * 2 = 0,5 

// 3 samples
1 - 1/8 * 2 = 0,75

// 4 samples
1 - 1/16 * 2 = 0,875

// 5 samples
1 - 1/32 * 2 = 0,938

// 6 samples
1 - 1/64 x 2 = 0,969

// 7 samples
1 - 1/128 x 2 = 0,984
```

It seems that we are getting diminishing returns after the 5 samples.
## Examples

What are scenarios that this tool proved to be valuable?

TBD

---
- Source: [[30 interests/Analytics/L. How to Measure Anything\|L. How to Measure Anything]]
- Tags: #statistics #estimations #tools